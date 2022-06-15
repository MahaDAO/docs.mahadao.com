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

Response:



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



<details>

<summary>24 hours ticker</summary>



</details>

<details>

<summary>Get index/marked price</summary>



</details>

<details>

<summary>Kline/Charts data</summary>



</details>

## Trading <a href="#jiao-yi-xiang-guan" id="jiao-yi-xiang-guan"></a>

### Security: [TRADE](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-trade" id="an-quan-lei-xing-trade"></a>

&#x20;All interfaces under the transaction require [signature and API-key verification​.](https://exdocs.gitbook.io/v/v/english/general-info#signed-trade-yu-userdata-endpoint-security)

<details>

<summary>Order creation</summary>



</details>

<details>

<summary>Condition order creation</summary>



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

