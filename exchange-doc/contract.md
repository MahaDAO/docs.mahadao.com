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

<details>

<summary>Contract List</summary>



</details>

## Market <a href="#hang-qing-xiang-guan" id="hang-qing-xiang-guan"></a>

### Security: [None](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-none-1" id="an-quan-lei-xing-none-1"></a>

Market section can be accessed freely without requiring any API-key or signatures.

<details>

<summary>Depth </summary>



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

