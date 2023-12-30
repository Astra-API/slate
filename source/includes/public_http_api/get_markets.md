
## Get Markets

`GET /markets`

Returns all markets listed by the specified exchange.

> Sample Request

```json
{
    "exchange": "BINANCE"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[Exchange](#exchange)|True|Exchange to fetch data from|

> Successful Sample Response

```json
[
    {
        "baseAsset": {
            "type": "SPOT",
            "asset": "ETH"
        },
        "quoteAsset": "BTC"
    },
    {
        "baseAsset": {
            "type": "SPOT",
            "asset": "LTC"
        },
        "quoteAsset": "BTC"
    },
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Market](#market)]|True|List of all supported asset pairs|
