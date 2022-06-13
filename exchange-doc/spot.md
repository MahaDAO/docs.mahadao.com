# Spot

## Public

### Security: None

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures.

<details>

<summary>Test Connectivity </summary>

This endpoint checks connectivity to the host

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/TestConnectivity.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/TestConnectivity.java)

#### Parameters

#### Responses

* 200                                                           Connection Normal&#x20;

```
{}
```

</details>

<details>

<summary>Check Server Time</summary>

This endpoint checks connectivity to the server and retrieves server timestamp

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/CheckServerTime.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/CheckServerTime.java)

#### Parameters

#### Responses

* 200                                                         Successfully retrieved server time &#x20;

```
{
    "timezone": "GMT+08:00",
    "serverTime": 1595563624731
}
```

</details>

<details>

<summary>Pairs List</summary>

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/PairsList.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/PairsList.java)

#### Parameters

#### Responses

* 200                                                       Successfully retrieved pairs list

```
{
    "symbols": [
        {
            "quantityPrecision": 3,
            "symbol": "sccadai",
            "pricePrecision": 6,
            "baseAsset": "SCCA",
            "quoteAsset": "DAI"
        },
        {
            "quantityPrecision": 8,
            "symbol": "btcusdt",
            "pricePrecision": 2,
            "baseAsset": "BTC",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 3,
            "symbol": "bchusdt",
            "pricePrecision": 2,
            "baseAsset": "BCH",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 2,
            "symbol": "etcusdt",
            "pricePrecision": 2,
            "baseAsset": "ETC",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 2,
            "symbol": "ltcbtc",
            "pricePrecision": 6,
            "baseAsset": "LTC",
            "quoteAsset": "BTC"
        }
    ]
}
```



</details>

| Name              | Type    | Example   | Description                     |
| ----------------- | ------- | --------- | ------------------------------- |
| symbol            | string  | `BTCUSDT` | Name of the symbol              |
| baseAsset         | string  | `BTC`     | Underlying asset for the symbol |
| quoteAsset        | string  | `USDT`    | Quote asset for the symbol      |
| pricePrecision    | integer | `2`       | Precision of the price          |
| quantityPrecision | integer | `6`       | Precision of the quantity       |

## Market

### Security Type: [None](broken-reference)

**Market** section can be accessed freely without requiring any API-key or signatures.

<details>

<summary>Depth</summary>

#### market depth data

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Depth.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Depth.java)

#### Parameters

#### Query

limit                             integer                                                   Default 100; Max 100&#x20;

symbol                        string                                                     Symbol Name E.g. BTCUSDT

#### Responses

* 200                              Successfully retrieved market depth data&#x20;

</details>

| Name  | Type  | Example         | Description                                                     |
| ----- | ----- | --------------- | --------------------------------------------------------------- |
| time  |  long | `1595563624731` | Current timestamp (ms)                                          |
| birds | list  | ;               | List of all bids, best bids first. See below for entry details. |
| asks  | list  | ;               | List of all asks, best asks first. See below for entry details. |

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

| Name | Type  | Example | Description                                       |
| ---- | ----- | ------- | ------------------------------------------------- |
| ' '  | float | `131.1` | price level                                       |
| ' '  | float | `2.3`   | The total quantity of orders for this price level |

<details>

<summary>24 hours ticker</summary>

24 hour price change statistics.

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Ticker.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/Ticker.java)

#### Parameters

#### Query

symbol                             string                                      Symbol Name. E.g. `BTCUSDT`

#### Responses

* 200                              Successfully retrieved market ticker data&#x20;

```
{
    "high": "9279.0301",
    "vol": "1302",
    "last": "9200",
    "low": "9279.0301",
    "rose": "0",
    "time": 1595563624731
}
```

</details>



| Name | Type  | Example         | Description  |
| ---- | ----- | --------------- | ------------ |
| time | long  | `1595563624731` | Open Time    |
| high | float | `9900`          | High Price   |
| low  | float | `8800.34`       | Low price    |
| last | float | `8900`          | Last price   |
| vol  | float | `4999`          | Trade Volume |

<details>

<summary>Recent Traders List</summary>

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/RecentTradesList.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/RecentTradesList.java)

#### Parameters

#### Query

symbol                             string                                      Symbol Name. E.g. `BTCUSDT`

Limit                                 string                                      Default 100;MAX 1000

#### Responses

* 200 &#x20;

```
[
  {
    "price": "3.00000100",
    "qty": "11.00000000",
    "time": 1499865549590,
    "side": "BUY"
  },...
]
```

</details>

| Name    | Type   | Example       | Description            |
| ------- | ------ | ------------- | ---------------------- |
| `price` | float  | `0.055`       | The price of the trade |
| `time`  | long   | 1537797044116 | Current timestamp (ms) |
| `qty`   | float  | `5`           | The quantity traded    |
| `side`  | string | `BUY/SELL`    | Taker side             |

<details>

<summary>Kline/Candlestick data</summary>

sdk:[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/KlineCandlestickData.java](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/KlineCandlestickData.java)

### Parameters

#### Query

symbol-string- String-Symbol Name  E.g. `BTCUSDT`

Interval-string-Interval of the Kline. Possible values include: `1min`,`5min`,`15min`,`30min`,`60min`,`1day`,`1week`,`1month`

limit-integer-Default 100;MAX 300

#### Responses

* 200

```
[
    {
        "high": "6228.77",
        "vol": "111",
        "low": "6228.77",
        "idx": 1594640340,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "222",
        "low": "6228.77",
        "idx": 1587632160,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "333",
        "low": "6228.77",
        "idx": 1587632100,
        "close": "6228.77",
        "open": "6228.77"
    }
]
```





</details>

### Responses



| Name    | Type  | Example         | Description  |
| ------- | ----- | --------------- | ------------ |
| `IDX`   | long  | `1538728740000` | Open time    |
| `open`  | float | `36.00000`      | Open price   |
| `close` | float | `33.00000`      | close price  |
| `high`  | float | `36.00000`      | high price   |
| `low`   | float | `30.00000`      | low price    |
| `vol`   | float | `2456.111`      | volume       |

## Trade

### Security Type: [TRADE](broken-reference)

Endpoints under **Trade** require an [API-key and a signature.](broken-reference)

<details>

<summary>New Order</summary>

**Rate Limit: 100times/2s**

**sdk:**[**https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/NewOrder.java**](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/NewOrder.java)

### **Parameters**&#x20;

**Header**

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### **Body**

symbol   ****          ``       string                  Symbol Name. E.g. `BTCUSDT`

volume                   number              Order vol. For MARKET BUY orders, vol=amount.

side                        string                 Side of the order,`BUY/SELL`

type                       string                  Type of the order, `LIMIT/MARKET`

price                      number              Order price, REQUIRED for LIMIT orders

newClientOrderId string                 Unique order ID generated by users to mark their orders

recvWindow         integer                Time window

#### Responses

* 200                                   Successfully post new order

```
{
    'symbol': 'LXTUSDT', 
    'orderId': '150695552109032492', 
    'clientOrderId': '157371322565051',
    'transactTime': '1573713225668', 
    'price': '0.005452', 
    'origQty': '110', 
    'executedQty': '0', 
    'status': 'NEW',
    'type': 'LIMIT', 
    'side': 'SELL'
}
```



</details>

| Name            | Type    | Example              | Description                                                                                                     |
| --------------- | ------- | -------------------- | --------------------------------------------------------------------------------------------------------------- |
| `orderId`       | long    | `150695552109032492` | ID of the order                                                                                                 |
| `clientOrderId` | string  | `213443`             | A unique ID of the order.                                                                                       |
| `symbol`        | string  | `BTCUSDT`            | Symbol Name                                                                                                     |
| `transactTime`  | integer | 1273774892913        | Time the order is placed                                                                                        |
| `price`         | float   | `4765.29`            | Price of the order                                                                                              |
| `origQty`       | float   | `1.01`               | Quantity ordered                                                                                                |
| `executedQty`   | float   | `1.01`               | Quantity of orders that has been executed                                                                       |
| `type`          | string  | LIMIT                | <p><br>Order type <code>LIMIT,MARKET</code></p>                                                                 |
| `side`          | string  | `BUY`                | <p><br>Order side：<code>BUY, SELL</code></p>                                                                    |
| `status`        | string  | NEW                  | The state of the order.Possible values include `NEW`, `PARTIALLY_FILLED`, `FILLED`, `CANCELED`, and `REJECTED`. |

<details>

<summary>Test New Order</summary>

Test new order creation and signature/recvWindow length. Creates and validates a new order but does not send the order into the matching engine.

sdk：[https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/TestNewOrder.java\
](https://github.com/exchange2021/openapidemo/blob/master/src/main/java/com/spot/TestNewOrder.java)

### Parameters

#### Header

X-CH-SIGN                          string                 Sign&#x20;

X-CH-APIKEY                      string                 Your API-key&#x20;

X-CH-TS                              integer                timestamp

#### Body



</details>
