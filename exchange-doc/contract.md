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

#### Response:

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

### **Parameters**&#x20;

**Header**

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### Body

orderId                   string               Order ID

contractName       string               Contract name E.g. `E-BTC-USDT`

#### Responses

* 200

```
{
    "orderId": 256609229205684228
}
```

</details>

<details>

<summary>Order details</summary>

### Parameters

#### Body

contractName       string   &#x20;

#### Responses

* 200

```
[
    {
       "side": "BUY",
       "executedQty": 0,
       "orderId": 259396989397942275,
       "price": 10000.0000000000000000,
       "origQty": 1.0000000000000000,
       "avgPrice": 0E-8,
       "transactTime": "1607702400000",
       "action": "OPEN",
       "contractName": "E-BTC-USDT",
       "type": "LIMIT",
       "status": "INIT"
    }
]


```

</details>

#### Response:

| Name           | Type   | Example              | Description                                                                                                                                                                           |
| -------------- | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| orderId        | long   | `150695552109032492` | Order ID                                                                                                                                                                              |
| `contractName` | string | E-BTC-USDT           | Contract name                                                                                                                                                                         |
| `price`        | float  | 10.5                 | Order price                                                                                                                                                                           |
| `origQty`      | float  | 10.5                 | Order quantity                                                                                                                                                                        |
| `executedQty`  | float  | 20                   | Order quantity                                                                                                                                                                        |
| `avgPrice`     | float  | 10.5                 | Average transaction price                                                                                                                                                             |
| `symbol`       | string | BHTUSDT              | Coin pair name                                                                                                                                                                        |
| `status`       | string | `NEW`                | Order status. Possible values are：`NEW`(new order，not filled)、`PARTIALLY_FILLED`（partially filled）、`FILLED`（fully filled）、`CANCELLED`（already cancelled）and`REJECTED`（order rejected） |
| `side`         | string | `NEW`                | Order direction. Possible values can only be：BUY（buy long）and SELL（sell short）                                                                                                        |
| `action`       | string | `OPEN`               | `OPEN/CLOSE`                                                                                                                                                                          |
| `transactTime` | long   | 1607702400000        | Order creation time                                                                                                                                                                   |

<details>

<summary>Open order</summary>

**Speed limit rules:**\
**Obtain open contract, the user's current order**

### **Parameters**

**Query**&#x20;

contractName                string           Contract name `E-BTC-USDT`&#x20;

**Header**

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### Responses:

* 200&#x20;

```
[
    {
       "side": "BUY",
       "executedQty": 0,
       "orderId": 259396989397942275,
       "price": 10000.0000000000000000,
       "origQty": 1.0000000000000000,
       "avgPrice": 0E-8,
       "transactTime": "1607702400000",
       "action": "OPEN",
       "contractName": "E-BTC-USDT",
       "type": "LIMIT",
       "status": "INIT"
    }
]

```

</details>

#### Response:

| Name           | Type   | Example              | Description                                                                                                                                                                           |
| -------------- | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| orderId        | long   | `150695552109032492` | Order ID                                                                                                                                                                              |
| `contractName` | string | E-BTC-USDT           | Contract name                                                                                                                                                                         |
| `price`        | float  | 10.5                 | Order price                                                                                                                                                                           |
| `origQty`      | float  | 10.5                 | Order quantity                                                                                                                                                                        |
| `executedQty`  | float  | 20                   | Order quantity                                                                                                                                                                        |
| `avgPrice`     | float  | 10.5                 | Average transaction price                                                                                                                                                             |
| `symbol`       | string | BHTUSDT              | Coin pair name                                                                                                                                                                        |
| `status`       | string | `NEW`                | Order status. Possible values are：`NEW`(new order，not filled)、`PARTIALLY_FILLED`（partially filled）、`FILLED`（fully filled）、`CANCELLED`（already cancelled）and`REJECTED`（order rejected） |
| `side`         | string | `NEW`                | Order direction. Possible values can only be：BUY（buy long）and SELL（sell short）                                                                                                        |
| `action`       | string | `OPEN`               | `OPEN/CLOSE`                                                                                                                                                                          |
| `transactTime` | long   | 1607702400000        | Order creation time                                                                                                                                                                   |

<details>

<summary>Order history</summary>

### **Parameters**

**Header:**

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### **Body**

**Query**&#x20;

contractName                string           Contract name `E-BTC-USDT`&#x20;

limit                                 string           Lines per page, default 100, max 1000

fromID                             long             Start retrieving from this Id

#### Responses:

* 200                    **OK**

```
[
    {
        "side":"BUY",
        "clientId":"0",
        "ctimeMs":1632903411000,
        "positionType":2,
        "orderId":777293886968070157,
        "avgPrice":41000,
        "openOrClose":"OPEN",
        "leverageLevel":26,
        "type":4,
        "closeTakerFeeRate":0.00065,
        "volume":2,
        "openMakerFeeRate":0.00025,
        "dealVolume":1,
        "price":41000,
        "closeMakerFeeRate":0.00025,
        "contractId":1,
        "ctime":"2021-09-29T16:16:51",
        "contractName":"E-BTC-USDT",
        "openTakerFeeRate":0.00065,
        "dealMoney":4.1,
        "status":4
    }
]
```

</details>

<details>

<summary>Profit history</summary>

### Parameters

#### Header&#x20;

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### Body

contractName                string           Contract name `E-BTC-USDT`&#x20;

limit                                 string           Lines per page, default 100, max 1000

fromID                             long             Start retrieving from this Id

#### Responses:

* 200                        OK

```
[
    {
        "side":"SELL",
        "positionType":2,
        "tradeFee":-5.23575,
        "realizedAmount":0,
        "leverageLevel":26,
        "openPrice":44500,
        "settleProfit":0,
        "mtime":1632882739000,
        "shareAmount":0,
        "openEndPrice":44500,
        "closeProfit":-45,
        "volume":900,
        "contractId":1,
        "historyRealizedAmount":-50.23575,
        "ctime":1632882691000,
        "id":8764,
        "capitalFee":0
    }
]
```

</details>

<details>

<summary>Order record</summary>

**Speed limit rules: 20 times/ 2s**

**Parameters**

#### **Query**&#x20;

contractName                string           Contract name `E-BTC-USDT`&#x20;

limit                                 string           Lines per page, default 100, max 1000

fromID                             long             Start retrieving from this Id

#### Header&#x20;

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

**Responses**

* 200&#x20;

```
[
  {
    "symbol": "ETHBTC",
    "id": 100211,
    "bidId": 150695552109032492,
    "askId": 150695552109032493,
    "price": "4.00000100",
    "qty": "12.00000000",
    "time": 1499865549590,
    "isBuyer": true,
    "isMaker": false,
    "fee":"0.001"
  },...
]
```

</details>



| Name         | Type    | Example            | Description                                         |
| ------------ | ------- | ------------------ | --------------------------------------------------- |
| symbol       | string  | ETHBTC             | Coin name(trade pair)                               |
| tradeId      | number  | 28457              | Trade ID                                            |
| bidid        | long    | 150695552109032492 | Buyer order ID                                      |
| askid        | long    | 150695552109032493 | Seller order ID                                     |
| bidUserId    | integer | 10024              | Buyer user ID                                       |
| askUserId    | integer | 10025              | Seller user ID                                      |
| price        | float   | 4.01               | Filled price                                        |
| qty          | float   | 12                 | Trade quantity                                      |
| amount       | float   | 5.38               | Filled amount                                       |
| time         | number  | 1499865549590      | Trade time stamp                                    |
| fee          | number  | 0.001              | Trading fees                                        |
| side         | string  | buy                | Current order direction BUY purchase, SELL  selling |
| contractName | string  | E-BTC-USDT         | Contract name                                       |
| isMaker      | Boolean | true               | is it maker?                                        |
| isBuyer      | Boolean | true               | is it buyer?                                        |

## Account <a href="#zhang-hu" id="zhang-hu"></a>

### Security: [USER\_DATA](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-userdata" id="an-quan-lei-xing-userdata"></a>

All interfaces under the account require [signature and API-key verification​.](https://exdocs.gitbook.io/v/v/english/general-info#signed-trade-yu-userdata-endpoint-security)

<details>

<summary>Account info</summary>

### Parameters

#### Header

X-CH-SIGN                                  string                                                     Sign&#x20;

X-CH-APIKEY                              string                                                     Your API-key&#x20;

X-CH-TS                                      integer                                                   timestamp

#### Responses

* 200&#x20;

```
{
    "account": [
        {
            "marginCoin": "USDT",
            "accountNormal": 999.5606,
            "accountLock": 23799.5017,
            "partPositionNormal": 9110.7294,
            "totalPositionNormal": 0,
            "achievedAmount": 4156.5072,
            "unrealizedAmount": 650.6385,
            "totalMarginRate": 0,
            "totalEquity": 99964804.560,
            "partEquity": 13917.8753,
            "totalCost": 0,
            "sumMarginRate": 873.4608,
            "positionVos": [
                {
                    "contractId": 1,
                    "contractName": "E-BTC-USDT",
                    "contractSymbol": "BTC-USDT",
                    "positions": [
                        {
                            "id": 13603,
                            "uid": 10023,
                            "contractId": 1,
                            "positionType": 2,
                            "side": "BUY",
                            "volume": 69642.0,
                            "openPrice": 11840.2394,
                            "avgPrice": 11840.3095,
                            "closePrice": 12155.3005,
                            "leverageLevel": 24,
                            "holdAmount": 7014.2111,
                            "closeVolume": 40502.0,
                            "pendingCloseVolume": 0,
                            "realizedAmount": 8115.9125,
                            "historyRealizedAmount": 1865.3985,
                            "tradeFee": -432.0072,
                            "capitalFee": 2891.2281,
                            "closeProfit": 8117.6903,
                            "shareAmount": 0.1112,
                            "freezeLock": 0,
                            "status": 1,
                            "ctime": "2020-12-11T17:42:10",
                            "mtime": "2020-12-18T20:35:43",
                            "brokerId": 21,
                            "marginRate": 0.2097,
                            "reducePrice": 9740.8083,
                            "returnRate": 0.3086,
                            "unRealizedAmount": 2164.5289,
                            "openRealizedAmount": 2165.0173,
                            "positionBalance": 82458.2839,
                            "settleProfit": 0.4883,
                            "indexPrice": 12151.1175,
                            "keepRate": 0.005,
                            "maxFeeRate": 0.0025
                        }
                    ]
                }
            ]
        }
    ]
}
```

</details>

Response:&#x20;

| Name     | Type | Description        |
| -------- | ---- | ------------------ |
| account  | \[]  | Balance collection |

#### `account` field:



| Name                | Type   | Example | Description                        |
| ------------------- | ------ | ------- | ---------------------------------- |
| marginCoin          | string | USDT    | Margin coin                        |
| accountNormal       | float  | 10.05   | Balance account                    |
| accountLock         | float  | 10.07   | Margin frozen account              |
| partPositionNormal  | float  | 10.07   | Restricted position margin balance |
| totalPositionNormal | float  | 10.07   | Full position initial margin       |
| achievedAmount      | float  | 10.07   | Profit and losses occurred         |
| unrealizedAmount    | float  | 10.05   | Unfilled profit and losses         |
| totalMarginRate     | float  | 10.05   | Full position margin rate          |
| totalEquity         | float  | 10.07   | Full position equity               |
| partEquity          | float  | 10.07   | Restricted position equity         |
| totalCost           | float  | 10.07   | Full position costs                |
| sumMarginRate       | float  | 10.07   | All accounts margin rate           |
| positionVos         | \[]    |         | Position contract record           |

#### `positionVos` field:

| Name           | Type    | Example    | Description        |
| -------------- | ------- | ---------- | ------------------ |
| contractId     | integer | 2          | Contract ID        |
| contractName   | string  | E-BTC-USDT | Contract name      |
| contractSymbol | string  | BTC-USDT   | Contract coin pair |
| positions      | \[]     |            | Position Details   |

#### `positions` field:

| Name                  | Type    | Example | Description                                                               |
| --------------------- | ------- | ------- | ------------------------------------------------------------------------- |
| Id                    | Integer | 2       | Position ID                                                               |
| uid                   | Integer | 10023   | User ID                                                                   |
| positionType          | Integer | 1       | Hold position type(1 full，2 restrictive)                                  |
| side                  | string  | SELL    | Hold position direction SELL sell long, BUY buy short                     |
| volume                | float   | 1.05    | Hold quantity                                                             |
| openPrice             | float   | 1.05    | Open position price                                                       |
| avgPrice              | float   | 1.05    | Hold average price                                                        |
| closePrice            | float   | 1.05    | Balancing average price                                                   |
| leverageLevel         | float   | 1.05    | Leverage multiple                                                         |
| holdAmount            | float   | 1.05    | Hold position margin                                                      |
| closeVolume           | float   | 1.05    | Balanced quantity                                                         |
| PendingcloseVolume    | float   | 1.05    | The number of pending closing orders                                      |
| realizedAmount        | float   | 1.05    | Profit and losses occurred                                                |
| historyRealizedAmount | float   | 1.05    | Historic accumulated profit and losses                                    |
| tradeFee              | float   | 1.05    | Trading fees                                                              |
| capitalFee            | float   | 1.05    | Capital costs                                                             |
| closeProfit           | float   | 1.05    | Balancing profit and loss                                                 |
| shareAmount           | float   | 1.05    | Amount to share                                                           |
| freezeLock            | integer | 0       | Position freeze status: 0 normal, 1 liquidation freeze, 2 delivery freeze |
| status                | integer | 0       | Position effectiveness，0 ineffective 1 effective                          |
| ctime                 | time    |         | Creation time                                                             |
| mtime                 | time    |         | Update time                                                               |
| brokerID              | integer | 1023    | Client id                                                                 |
| lockTime              | time    |         | liquidation lock time                                                     |
| MarginRate            | float   | 1.05    | Margin rate                                                               |
| reducePrice           | float   | 1.05    | Price reduction                                                           |
| returnRate            | float   | 1.05    | Return rate (profit rate)                                                 |
| unRealizedAmount      | float   | 1.05    | Unfilled profit and losses                                                |
| openRealizedAmount    | float   | 1.05    | Open position unfilled profit and losses                                  |
| positionBalance       | float   | 1.05    | Position value                                                            |
| indexPrice            | float   | 1.05    | Newest marked price                                                       |
| keepRate              | float   | 1.05    | Scaled minimum kept margin rate                                           |
| maxFeeRate            | float   | 1.05    | Balancing maximum fees rate                                               |
