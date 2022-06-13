# Errors

Errors consist of two parts: an error code and a message. Codes are universal, but messages can vary. Here is the error JSON payload:

```
{
  "code":-1121,
  "msg":"Invalid symbol."
}
```



## 10xx - General Server or Network issues

### -1000 UNKNOWN

* An unknown error occured while processing the request.

### -1001 DISCONNECTED

* Internal error; unable to process your request. Please try again.

### -1002 UNAUTHORIZED

* You are not authorized to execute this request. Request need API Key included in . We suggest that API Key be included in any request.

### -1003 TOO\_MANY\_REQUESTS

* Requests exceed the limit too frequently.

### -1004 NO\_THIS\_COMPANY

* You are not authorized to execute this request. User not exit Company

### -1006 UNEXPECTED\_RESP

* An unexpected response was received from the message bus. Execution status unknown. OPEN API server find some exception in execute request .Please report to Customer service.

### -1007 TIMEOUT

* Timeout waiting for response from backend server. Send status unknown; execution status unknown.

### -1014 UNKNOWN\_ORDER\_COMPOSITION

* Unsupported order combination.

### -1015 TOO\_MANY\_ORDERS

* Too many new orders.

### -1016 SERVICE\_SHUTTING\_DOWN

* This service is no longer available.

### -1017 ILLEGAL\_CONTENT\_TYPE

* We recommend attaching Content-Type to all request headers and setting it to application/json

### -1020 UNSUPPORTED\_OPERATION

* This operation is not supported.

### -1021 INVALID\_TIMESTAMP

* Timestamp for this request is outside of the recvWindow.
* Timestamp for this request was 1000ms ahead of the server's time.
* Please check the difference between your local time and server time .

### -1022 INVALID\_SIGNATURE

* Signature for this request is not valid.

### -1023 UNTIMESTAMP

* You are not authorized to execute this request, we recommend that you add X-CH-TS to all request headers

### -1024 UNSIGNATURE

* You are not authorized to execute this request, we recommend that you add X-CH-SIGN to the request header

## 11xx - Request issues

### -1100 ILLEGAL\_CHARS

* Illegal characters found in a parameter.

### -1101 TOO\_MANY\_PARAMETERS

* Too many parameters sent for this endpoint.

### -1102 MANDATORY\_PARAM\_EMPTY\_OR\_MALFORMED

* A mandatory parameter was not sent, was empty/null, or malformed.
* Mandatory parameter '%s' was not sent, was empty/null, or malformed. &#x20;
* Param '%s' or '%s' must be sent, but both were empty/null!

### -1103 UNKNOWN\_PARAM

* An unknown parameter was sent.
* each request requires at least one parameter. {Timestamp}.

### -1104 UNREAD\_PARAMETERS

* Not all sent parameters were read.
* Not all sent parameters were read; read '%s' parameter(s) but was sent '%s'.

### -1105 PARAM\_EMPTY

* A parameter was empty.
* Parameter '%s' was empty.

### -1106 PARAM\_NOT\_REQUIRED

* A parameter was sent when not required.
* Parameter '%s' sent when not required.

### -1111 BAD\_PRECISION

* Precision is over the maximum defined for this asset.

### -1112 NO\_DEPTH

* No orders on book for symbol.

### -1116 INVALID\_ORDER\_TYPE

* Invalid orderType.
* In the current version , ORDER\_TYPE values is LIMIT or MARKET.

### -1117 INVALID\_SIDE

* Invalid side.
* ORDER\_SIDE values is BUY or SELL

### -1118 EMPTY\_NEW\_CL\_ORD\_ID

* New client order ID was empty.

### -1121 BAD\_SYMBOL

* Invalid symbol.

### -1136 ORDER\_VOLUME\_TOO\_SMALL

* Order volume lower than the minimum.

### -1138 ORDER\_PRICE\_WAVE\_EXCEED

* Order price exceeds permissible range.

### -1139 ORDER\_NOT\_SUPPORT\_MARKET

* This trading pair does not support market trading

### -1145 ORDER\_NOT\_SUPPORT\_CANCELLATION

* This order type does not support cancellation

### -2013 NO\_SUCH\_ORDER

* Order does not exist.

### -2015 REJECTED\_CH\_KEY

* Invalid API-key, IP, or permissions for action.

### -2016 EXCHANGE\_LOCK

* Transaction is frozen

### -2017 BALANCE\_NOT\_ENOUGH

* Insufficient balance
