# Web Socket

### General

`Websocket` is a new HTML5 Protocol. It achieves full-duplex data transmission between the client and the server, allowing data to be transferred effectively in both directions. With just only one handshake, the connection between the client and the server is established. The server will then be able to push data to the client according to preset rules. Its advantages include:

* The `WebSocket` request header for data transmission between client and server is approximately 2 bytes only
* Either the client or server can initiate a data transmission
* As there is no need to create and delete TCP connection repeatedly, it saves resources for both bandwidth and server

**We strongly recommend developers to use WebSocket API to retrieve market data and order book depth.**

### Ws information

* url: [wss://wspool.hiotc.pro/kline-api/ws](wss://wspool.hiotc.pro/kline-api/ws)
* The returned data will be binary compressed except the heartbeat data (the user needs to decompress through Gzip algorithm)

### Command Format

| Event | Channel                       | Description                             |
| ----- | ----------------------------- | --------------------------------------- |
| sub   | `market_$symbol_depth_step0`  | `Subscribe depth`                       |
| unsub | `market_$symbol_depth_step0`  | `Unsubscribe depth`                     |
| sub   | `market_$symbol_trade_ticker` | `Subscribe to real-time trade`          |
| unsub | `market_$symbol_trade_ticker` | `Unsubscribe to real-time trade`        |
| sub   | `market_$symbol_ticker`       | `Subscribe to 24h market data`          |
| unsub | `market_$symbol_ticker`       | `Unsubscribe to 24h market data`        |
| sub   | `market_$symbol_kline_1min`   | `Subscribe to 1min k-line information`  |
| req   | `market_$symbol_kline_1min`   | `Request 1 month historical bar record` |



### Heartbeat

Every once in a while, the server will send a `PING` message. The client needs to reply to the `PONG` message, otherwise the server will close the connection.

* Ping

```
{
    "ping": 1535975085052
}
```

* Pong

```
{
    "pong": 1535975085052
}
```



### **Subscription Full Depth**

* Subscription message structure

```
{
    "event":"sub",
    "params":{
        "channel":"market_$symbol_depth_step0", // $symbol E.g. btcusdt
        "cb_id":"1" // Business ID is not required
    }
}
```

* Payload

```
{
    "channel":"market_btcusdt_depth_step0",
    "ts":1506584998239,
    "tick":{ //A maximum of 30 orders are returned
        "asks":[ //asks
            [10000.19,0.93],
            [10001.21,0.2],
            [10002.22,0.34]
        ],
        "buys":[ //buy
            [9999.53,0.93],
            [9998.2,0.2],
            [9997.19,0.21]
        ]
    }
}
```



### **Subscription Real Time Trade**

* Subscription message structure

```
{
    "event":"sub",
    "params":{
        "channel":"market_$symbol_trade_ticker", // $symbol E.g. btcusdt
        "cb_id":"1" // Business ID is not required
    }
}
```

* Payload

```
{
    "channel":"market_$symbol_trade_ticker",
    "ts":1506584998239,//request time
    "tick":{
        "data":[
            {
                "side":"buy",//buy,sell
                "price":32.233,
                "vol":232,
                "amount":323,
                "ds":'2017-09-10 23:12:21'
            }
        ]
    }
}
```



### **Subscription Kline Market**

* Subscription message structure

```
{
    "event":"sub",
    "params":{
        "channel":"market_$symbol_kline_[1min/5min/15min/30min/60min/1day/1week/1month]", // $symbol E.g. btcusdt 
        "cb_id":"1" // Business ID is not required
    }
}
```

* Payload

```
{
    "channel":"market_$symbol_kline_1min", //1min is for 1 minute
    "ts":1506584998239,//request time
    "tick":{
        "id":1506602880,//kline start time
        "vol":1212.12211,
        "open":2233.22,//open price
        "close":1221.11,//close price
        "high":22322.22,//high price
        "low":2321.22//low price
    }
}
```



### **Subscription** Market Tickers

* Subscription message structure

```
{
    "event":"sub",
    "params":{
        "channel":"market_$symbol_ticker", // $symbol E.g. btcusdt 
        "cb_id":"1" // Business ID is not required
    }
}
```

* Payload

```
{
    "channel":"market_$symbol_ticker",
    "ts":1506584998239,//request time
    "tick":{
        "amount":123.1221,
        "vol":1212.12211,
        "open":2233.22,//open price
        "close":1221.11,//close price
        "high":22322.22,//high price
        "low":2321.22,//low price
        "rose":-0.2922,//increase
    }
}
```



### Request Kline History Data

* Subscription message structure

```
{
    "event":"req",
    "params":{
        "channel":"market_$symbol_kline_[1min/5min/15min/30min/60min/1day/1week/1month]",
        "cb_id":"1",
        "endIdx":"1506602880", //Return pageSize data before endIdx Not required
        "pageSize":100 // Not required
    }
}
```

* Payload

```
{
    "event_rep":"rep","channel":"market_$symbol_kline_5min",
    "ts":1506584998239,//request time
    "data":[ //up to 300
        {
            "id":1506602880,//kline start time
            "amount":123.1221,
            "vol":1212.12211,
            "open":2233.22,//open price
            "close":1221.11,//close price
            "high":22322.22,//high price
            "low":2321.22//low price
        },
        {
            "id":1506602880,//kline start time
            "amount":123.1221,
            "vol":1212.12211,
            "open":2233.22,//open price
            "close":1221.11,//close price
            "high":22322.22,//high price
            "low":2321.22//low price
        }
    ]
}
```



### Request History Trade

* Subscription message structure

```
{
    "event":"req",
    "params":{
        "channel":"market_$symbol_trade_ticker", // $symbol E.g. btcusdt 
        "cb_id":"1" // Business ID is not required
    }
}
```

* Payload

```
{
    "event_rep":"rep","channel":"market_$symbol_trade_ticker",
    "ts":1506584998239,"status":"ok",
    "data":[
        {
            "side":"buy",//buy,sell
            "price":32.233,//trade price
            "vol":232,//trade vol
            "amount":323//trade amount
        },
        {
            "side":"buy",//buy,sell
            "price":32.233,//trade price
            "vol":232,//trade vol
            "amount":323//trade amount
        }
    ]
}
```

