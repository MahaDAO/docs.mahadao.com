# Exchange doc

### BASIC INFORMATION

## API Basic Information <a href="#api-basic-information" id="api-basic-information"></a>

* baseurl `https://openapi.xxx.com`
* All endpoints return either a JSON object or array.
* Data is returned in **Reverse** order. newest first, oldest last.
* All time and timestamp related fields are in milliseconds.

## HTTP Error Codes <a href="#http-error-codes" id="http-error-codes"></a>

* HTTP `4XX` return codes are used for malformed requests; the issue is on the sender's side.
* HTTP `429` return code is used when breaking a request rate limit.
* HTTP `418` return code is used when an IP has been auto-banned for continuing to send requests after receiving `429` codes.
* HTTP `5XX` return codes are used for internal errors
* HTTP `504` return code is used when the API successfully sent the message but not get a response within the timeout period. It is important to **NOT** treat this as a failure operation; the execution status is **UNKNOWN** and could have been a success.
* All endpoints can possibly return an ERROR, the error payload is as follows:&#x20;

```
{
  "code": -1121,
  "msg": "Invalid symbol."
}
```



## General Information

* All requests are based on the Https protocol, and the `Content-Type` in the request header information needs to be uniformly set to:`'application/json'`
* For the interface of the `GET` method, the parameters must be sent in the `query string`
* The interface of the `POST` method, the parameters must be sent in the `request body`
* Parameters may be sent in any order.

## LIMITS

* There will be a limited frequency description below each interface.
* A 429 will be returned when either rate limit is violated.
* A 429 will be returned when either rate limit is violated.

## Endpoint Security Type

* Each endpoint has a security type that determines the how you will interact with it.
* API-keys are passed into the Rest API via the `X-CH-APIKEY` header.
* API-keys and secret-keys **are case sensitive**.

| Security Type | Description                                              |
| ------------- | -------------------------------------------------------- |
| NONE          | Endpoint can be accessed freely.                         |
| TRADE         | Endpoint requires sending a valid API-Key and signature. |
| USER\_DATA    | Endpoint requires sending a valid API-Key and signature. |
| USER\_STREAM  | Endpoint requires sending a valid API-Key.               |
| MARKET\_DATA  | Endpoint requires sending a valid API-Key.               |

## SIGNED (TRADE and USER\_DATA) endpoint security

* When calling the `TRADE` or `USER_DATA` interface, the signature parameter should be passed in the `X-CH-SIGN` field in the HTTP header.
* The signature uses the `HMAC SHA256` algorithm. The `API-Secret` corresponding to the API-KEY is used as the `HMAC SHA256` key.
* The request header of `X-CH-SIGN` is based on `timestamp` + `method` + `requestPath` + `body string`  (+ means string connection) as the operation object
* The value of `timestamp` is the same as the `X-CH-TS` request header, `method` is the request method, and the letters are all uppercase: `GET/POST`
* `requestPath` is the request interface path For example: `/sapi/v1/order`
* `body` is the string of the request body (post only)
* The signature is not case sensitive.

## Timing Security

* The signature interface needs to pass the timestamp in the `X-CH-TS` field in the HTTP header, and its value should be the unix timestamp of the request sending time e.g. `1528394129373`
* An additional parameter, `recvWindow`, may be sent to specify the number of milliseconds after `timestamp` the request is valid for. If `recvWindow` is not sent, **it defaults to 5000**.
* In addition, if the server calculates that the client's timestamp is more than one second ‘in the future’ of the server’s time, it will also reject the request.
* The logic is as follows:

```
if (timestamp < (serverTime + 1000) && (serverTime - timestamp) <= recvWindow) {
  // process request
} else {
  // reject request
}
```



**Serious trading is about timing.**  Networks can be unstable and unreliable, which can lead to requests taking varying amounts of time to reach the servers. With `recvWindow`, you can specify that the request must be processed within a certain number of milliseconds or be rejected by the server.&#x20;

**It recommended to use a small recvWindow of 5000 or less!**

## SIGNED Endpoint Examples for POST /sapi/v1/order

Here is a step-by-step example of how to send a vaild signed payload from the Linux command line using `echo`, `openssl`, and `curl`.

| Key       | Value                            |
| --------- | -------------------------------- |
| apiKey    | vmPUZE6mv9SD5V5e14y7Ju91duEh8A   |
| secretKey | 902ae3cb34ecee2779aa4d3e1d226686 |

| Parameter | value   |
| --------- | ------- |
| symbol    | BTCUSDT |
| side      | BUY     |
| type      | LIMIT   |
| volume    | 1       |
| price     | 9300    |

## Signature example

* **Body:**

```
{"symbol":"BTCUSDT","price":"9300","volume":"1","side":"BUY","type":"LIMIT"}
```

* **HMAC SHA256 Signature:**

```
[linux]$ echo -n "1588591856950POST/sapi/v1/order/test{\"symbol\":\"BTCUSDT\",\"price\":\"9300\",\"volume\":\"1\",\"side\":\"BUY\",\"type\":\"LIMIT\"}" | openssl dgst -sha256 -hmac "902ae3cb34ecee2779aa4d3e1d226686"
(stdin)= c50d0a74bb9427a9a03933d0eded03af9bf50115dc5b706882a4fcf07a26b761
```

* **Curl command:**&#x20;

```
  (HMAC SHA256)
  [linux]$ curl -H "X-CH-APIKEY: c3b165fd5218cdd2c2874c65da468b1e" -H "X-CH-SIGN: c50d0a74bb9427a9a03933d0eded03af9bf50115dc5b706882a4fcf07a26b761" -H "X-CH-TS: 1588591856950" -H "Content-Type:application/json" -X POST 'http://localhost:30000/sapi/v1/order/test' -d '{"symbol":"BTCUSDT","price":"9300","quantity":"1","side":"BUY","type":"LIMIT"}'
```
