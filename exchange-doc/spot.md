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

