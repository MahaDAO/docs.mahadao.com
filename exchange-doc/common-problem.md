# Common Problem

### What is the maximum difference between the timestamp parameter of the request interface and the arrival time of the server? <a href="#what-is-the-maximum-difference-between-the-timestamp-parameter-of-the-request-interface-and-the-arri" id="what-is-the-maximum-difference-between-the-timestamp-parameter-of-the-request-interface-and-the-arri"></a>

When the server receives the request, it will judge the timestamp in the request. If it is sent before 5000 milliseconds, the request will be considered invalid. This time window value can be customized by sending the optional parameter recvWindow.

### The request header "X-CH-TS" cannot be empty. How to solve it? <a href="#the-request-header-x-ch-ts-cannot-be-empty-how-to-solve-it" id="the-request-header-x-ch-ts-cannot-be-empty-how-to-solve-it"></a>

First, it is recommended that the user print out the X-CH-TS, and check whether the X-CH-TS is empty when there is an exception, and it is recommended that the user code is optimized, and judge whether the X-CH-TS is empty before each request.

### Why does authentication always return invalid signatures? <a href="#why-does-authentication-always-return-invalid-signatures" id="why-does-authentication-always-return-invalid-signatures"></a>

You can print out the request header information and the string before signature, with the following points:：

* Compare your request header with the following request header example one by one

```
Example request header:​Content-Type: application/json​X-CH-APIKEY: 44c541a1-****-****-****-10fe390df2​X-CH-SIGN: ssseLeefrffraoEQ3yI9qEtI1CZ82ikZ4xSG5Kj8gnl3uw=​X-CH-TS: 1574327555669
```

* Is the API-key configured correctly in the program
* Whether the string before signing conforms to the standard format, the order of all elements must be consistent. You can copy the following example to compare with your string before signing:

```
GET Example： 1588591856950GET/sapi/v1/account​POST Example：1588591856950POST/sapi/v1/order/test{"symbol":"BTCUSDT","price":"9300","volume":"1","side":"BUY","type":"LIMIT"}
```

### The calling interface prompts ILLEGAL\_CONTENT\_TYPE (-1017). What is the reason? <a href="#the-calling-interface-prompts-illegal_content_type-1017-what-is-the-reason" id="the-calling-interface-prompts-illegal_content_type-1017-what-is-the-reason"></a>

We recommend attaching Content-Type to all request headers and setting it to application/json

### Is there a limit to the frequency of API calls per second? <a href="#is-there-a-limit-to-the-frequency-of-api-calls-per-second" id="is-there-a-limit-to-the-frequency-of-api-calls-per-second"></a>

There are restrictions. For details, see the access frequency restrictions for each interface in the document.

### What is the limit on API access frequency**？** <a href="#what-is-the-limit-on-api-access-frequency" id="what-is-the-limit-on-api-access-frequency"></a>

Personal data is restricted according to API-key, and public data is restricted according to ip. It should be noted that if the user requests public data and passes in valid personal information, it is restricted according to API-key.

### What is the cause of HTTP status code 429? <a href="#what-is-the-cause-of-http-status-code-429" id="what-is-the-cause-of-http-status-code-429"></a>

The request interface exceeds the access frequency limit. It is recommended to reduce the access frequency.

### Will the IP be blocked if the API call interface reports that the access frequency is exceeded? How long is it sealed? <a href="#will-the-ip-be-blocked-if-the-api-call-interface-reports-that-the-access-frequency-is-exceeded-how-l" id="will-the-ip-be-blocked-if-the-api-call-interface-reports-that-the-access-frequency-is-exceeded-how-l"></a>

Normally not, just reduce the frequency of access.

### Why is WebSocker disconnected?? <a href="#why-is-websocker-disconnected" id="why-is-websocker-disconnected"></a>

* Without adding a heartbeat, the WebSocket connection requires the client to return to pong to ensure the stability of the connection.
* The pong message sent by the client is caused by network reasons, but the server does not receive it, or other network reasons may also cause automatic disconnection.
* It is recommended that users have a good WebSocket disconnect and reconnect mechanism to ensure that the program can automatically reconnect when the heartbeat (ping/pong) connection is accidentally disconnected.

### The user request interface reports an error Time Out? <a href="#the-user-request-interface-reports-an-error-time-out" id="the-user-request-interface-reports-an-error-time-out"></a>

The network cannot connect to the server. It is recommended that you check whether the network is smooth.

### How to get all the currency pairs on the platform? <a href="#how-to-get-all-the-currency-pairs-on-the-platform" id="how-to-get-all-the-currency-pairs-on-the-platform"></a>

Coin's /sapi/v1/symbols interface can be obtained

### Is there a limit on the number of batch orders/cancellations?? <a href="#is-there-a-limit-on-the-number-of-batch-orders-cancellations" id="is-there-a-limit-on-the-number-of-batch-orders-cancellations"></a>

Yes, the batch interface will limit 10 orders

### What is newClientOrderId and what does it do? <a href="#what-is-newclientorderid-and-what-does-it-do" id="what-is-newclientorderid-and-what-does-it-do"></a>

* newClientOrderId is your customized order number, which can be used to identify your order. After the order is placed, you can make newClientOrderId call the "Order Information" interface to view the order status;
* The user needs to ensure that this ID is not repeated, and we will not prompt for re-relocation. If there is a repetition, you can only cancel or query the latest piece of data when canceling and querying the order

### How to get the latest transaction price? <a href="#how-to-get-the-latest-transaction-price" id="how-to-get-the-latest-transaction-price"></a>

You can get ticker information, last is the latest transaction price

### Will there be a negative growth in the 24-hour trading volume in the ticker interface? <a href="#will-there-be-a-negative-growth-in-the-24-hour-trading-volume-in-the-ticker-interface" id="will-there-be-a-negative-growth-in-the-24-hour-trading-volume-in-the-ticker-interface"></a>

Will do. Because the 24-hour trading volume is a 24-hour rolling data (the size of the translation window is 24 hours), it may happen that the accumulated trading volume and accumulated trading volume in the next window are smaller than the previous window.
