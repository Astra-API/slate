## Get Markets

> Sample Request

```bash
GET /markets?exchange=BINANCE
```

> Sample Response

```json
[
    {
        "symbol": "BINANCE-SPOT-ETH-USDT",
        "assetType": "SPOT",
        "baseAsset": "ETH",
        "quoteAsset": "USDT"
    },
    {
        "symbol": "BINANCE-PERP-BTC-USDT",
        "assetType": "PERP",
        "baseAsset": "BTC",
        "quoteAsset": "USDT",
        "marginAsset": "USDT"
    },
    {
        "symbol": "BINANCE-PERP-BTC-USD-COINM",
        "assetType": "PERP",
        "baseAsset": "BTC",
        "quoteAsset": "USD",
        "marginAsset": "BTC"
    },
    {
        "symbol": "BINANCE-FUT-BTC-USDT-210625",
        "baseAsset": "BTC",
        "quoteAsset": "USDT",
    }
]
```


`GET /markets`

Returns all markets on the specified exchange that are supported by Astra, along with their associated metadata.

You can see the list of asset types we currently support [here](#asset-type). We're working on expanding our coverage to all tradeable markets.

<aside class="notice">
Note: Currently, the only metadata we return is `baseAsset`, `quoteAsset`, and `marginAsset`, along with the market symbol and asset type. These assets are returned in a format that is normalized across exchanges (see [AbstractSpotAsset](#abstract-spot-asset) in our schema for more info)

We will gradually be adding much more normalized metadata to this response, including margin requirements, lot size, expiry, strike price, and more.
</aside>

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[Exchange](#exchange)|True|Exchange to fetch data from|

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|Array<[MarketMetadata](#marketmetadata)>|True|List of markets and their associated metadata|
