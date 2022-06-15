# Contract

## Public

### Security: [None](broken-reference)

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures.

<details>

<summary>Test connectivity</summary>

This endpoint checks connectivity to the host.&#x20;

### Parameters

#### Responses

* 200&#x20;

```
{}
```

</details>

<details>

<summary>Check server time</summary>

### Parameters

#### Responses

* 200

```
{
    "serverTime":1607702400000,
    "timezone":Chinese standard time
}
```

</details>

### Response:

| Name       | Type   | Example             | Description      |
| ---------- | ------ | ------------------- | ---------------- |
| serverTime | long   | 1607702400000       | server timestamp |
| timezone   | string | China standard time | server time zone |

<details>

<summary>Contract List</summary>

### Parameters

#### Responses

* 200

```
[
    {
        "symbol": "H-HT-USDT",
        "pricePrecision": 8,
        "side": 1,
        "maxMarketVolume": 100000,
        "multiplier": 6,
        "minOrderVolume": 1,
        "maxMarketMoney": 10000000,
        "type": "H",
        "maxLimitVolume": 1000000,
        "maxValidOrder": 20,
        "multiplierCoin": "HT",
        "minOrderMoney": 0.001,
        "maxLimitMoney": 1000000,
        "status": 1
    }
]
```



</details>



| Name            | Type   | Example      | Description                                                                       |
| --------------- | ------ | ------------ | --------------------------------------------------------------------------------- |
| symbol          | string | `E-BTC-USDT` | Contract name                                                                     |
| status          | number | 1            | status（0：cannot trade，1：can trade                                                 |
| type            | string | `S`          | contract type, E: perpetual contract, S: test contract, others are mixed contract |
| side            | number | `1`          | Contract direction(backwards：0，1：forward)                                         |
| multiplier      | number | 0.5          | Contract face value                                                               |
| multiplierCoin  | string | BTC          | Contract face value unit                                                          |
| pricePrecision  | number | `4`          | Precision of the price                                                            |
| minOrderVolume  | number | 10           | Minimum order volume                                                              |
| minOrderMoney   | number | 10           | Minimum order value                                                               |
| maxMarketVolume | number | 10000        | Market price order maximum volume                                                 |
| maxMarketMoney  | number | 10000        | Market price order maximum value                                                  |
| maxLimitVolume  | number | 10000        | Limit price order maximum volume                                                  |
| maxValidOrder   | number | 10000        | Maximum valid order quantity                                                      |

## Market <a href="#hang-qing-xiang-guan" id="hang-qing-xiang-guan"></a>

### Security: [None](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-none-1" id="an-quan-lei-xing-none-1"></a>

Market section can be accessed freely without requiring any API-key or signatures.

<details>

<summary>Depth </summary>

**Market depth data**&#x20;

### Parameters

#### Query&#x20;

limit                           integer                            Default 100, Max 100

&#x20;Contract name        string                              Contract Name E.g. E-BTC-USDT

#### Response

* 200                                                             Successfully retrieve market depth data

```
{
  "bids": [
    [
      "3.90000000",   // price
      "431.00000000"  // quantity
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // price
      "12.00000000"  // quantity
    ],
    [
      "5.10000000",
      "28.00000000"
    ]
  ]
}
```

</details>

| Name  | Type  | Example         | Description              |
| ----- | ----- | --------------- | ------------------------ |
| time  |  long | `1595563624731` | Current timestamp (ms)   |
| birds | list  | look below      | Order book purchase info |
| asks  | list  | look below      | Order book selling info  |

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

| Name | Type  | Example | Description                                       |
| ---- | ----- | ------- | ------------------------------------------------- |
| ' '  | float | `131.1` | price level                                       |
| ' '  | float | `2.3`   | The total quantity of orders for this price level |

<details>

<summary>24 hours ticker</summary>

24 hour price change statistics

### Parameters

**Query**

symbol                 string                              Symbol Name. E.g. BTCUSDT

#### Responses

* &#x20;200                                                       Successfully obtain ticker info

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

### Response

| Name | Type   | Example         | Description     |
| ---- | ------ | --------------- | --------------- |
| time | long   | `1595563624731` | Open Time       |
| high | float  | `9900`          | High Price      |
| low  | float  | `8800.34`       | Low price       |
| last | float  | `8900`          | Last price      |
| vol  | float  | `4999`          | Trade Volume    |
| rose | string | +0.5            | Price variation |

<details>

<summary>Get index/marked price</summary>

### Parameters

#### Query&#x20;

limit                           integer                            Default 100, Max 100

&#x20;Contract name        string                              Contract Name E.g. E-BTC-USDT

#### Responses

* 200&#x20;

```
{
    "markPrice": 581.5,
    "indexPrice": 646.3933333333333,
    "lastFundingRate": 0.001,
    "contractName": "E-ETH-USDT",
    "time": 1608273554063
}
```

</details>

| Name              | Type   | Example      | Description       |
| ----------------- | ------ | ------------ | ----------------- |
| `indexPrice`      | float  | 0.055        | Index price       |
| `markPrice`       | float  | 0.0578       | Marked price      |
| `contractName`    | string | `E-BTC-USDT` | Contract name     |
| `lastFundingRate` | float  | `0.123`      | Current fund rate |

<details>

<summary>Kline/Charts data</summary>

**Parameters**

**Query**

Contract Name            string                      Contract Name. E.g. BTCUSDT

Limit                             Integer                    Default 100; Max 1000

interval                         string                      K-line interval, identifies the sent value as:\
&#x20;                                                                    `1min`,`5min`,`15min`,`30min`,`1h`, `1day,`\
&#x20;                                                                    `1week`,`1month`

#### Responses

* 200&#x20;

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

### Response:

| Name    | Type  | Example         | Description  |
| ------- | ----- | --------------- | ------------ |
| `IDX`   | long  | `1538728740000` | Start time   |
| `open`  | float | `36.00000`      | Open price   |
| `close` | float | `33.00000`      | close price  |
| `high`  | float | `36.00000`      | MAX price    |
| `low`   | float | `30.00000`      | MIN price    |
| `vol`   | float | `2456.111`      | Trade volume |

## Trading <a href="#jiao-yi-xiang-guan" id="jiao-yi-xiang-guan"></a>

### Security: [TRADE](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-trade" id="an-quan-lei-xing-trade"></a>

&#x20;All interfaces under the transaction require [signature and API-key verification​.](https://exdocs.gitbook.io/v/v/english/general-info#signed-trade-yu-userdata-endpoint-security)

<details>

<summary>Order creation</summary>

Creation of single new orders

### **Parameters**&#x20;

**Header**

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### Body

volume                   number            Order quantity

price                       number            Order price

contractName       string               Contract name E.g. `E-BTC-USDT`

type                        string               Order type, `LIMIT/MARKET`

side                        string               trade direction, `BUY/SELL`

open                       string               Open balancing direction, `OPEN/CLOSE`

positionType          number           Hold-up position, 1 Full position 2 restrictive position

clientOrderId          string              Client order identity, a string with length less than 32 bit ``&#x20;

timeInForce             string              `IOC, FOK, POST_ONLYBody`

#### Responses

* 200&#x20;

```
{
    "orderId": 256609229205684228
}
```

</details>

| Name    | Type   | Example            | Description |
| ------- | ------ | ------------------ | ----------- |
| orderId | string | 256609229205684228 | Order ID    |

<details>

<summary>Condition order creation</summary>

### **Parameters**&#x20;

****

**Header**

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### Body

volume                  number           Order quantity

price                      number          Order price

contractName       string              Contract name E.g. `E-BTC-USDT`

type                       string              Order type, `LIMIT/MARKET`

side                       string               trade direction, `BUY/SELL`

open                      string               Open balancing direction, `OPEN/CLOSE`

positionType         number            Hold-up position, 1 Full position 2 restrictive position

triggerPrice           string               trigger price

triggerType            string              trigger type `3UP/4DOWN`

#### Responses

* 200                                           OK

```
{
     "orderId": 256609229205684228
}
```

</details>

<details>

<summary>Cancel order</summary>



</details>

<details>

<summary>Order details</summary>



</details>

<details>

<summary>Open order</summary>



</details>

<details>

<summary>Order history</summary>



</details>

<details>

<summary>Profit history</summary>



</details>

<details>

<summary>Order record</summary>



</details>

## Account <a href="#zhang-hu" id="zhang-hu"></a>

### Security: [USER\_DATA](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-userdata" id="an-quan-lei-xing-userdata"></a>

All interfaces under the account require [signature and API-key verification​.](https://exdocs.gitbook.io/v/v/english/general-info#signed-trade-yu-userdata-endpoint-security)

<details>

<summary>Account info</summary>



</details>

