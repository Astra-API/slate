## MarketMetadata

> Sample Data

```json
{
    "symbol": "BINANCE-PERP-BTC-USD-COINM",
    "assetType": "PERP",
    "baseAsset": "BTC",
    "quoteAsset": "USD",
    "marginAsset": "BTC"
},
```

Metadata associated with a particular market.

<aside class="notice">
Note: Currently, the only metadata we return is <i>baseAsset</i>, <i>quoteAsset</i>, and <i>marginAsset</i>, along with the market symbol and asset type. These assets are returned in a format that is normalized across exchanges (see <a href="#abstracttoken">AbstractToken</a> in our schema for more info)

We will gradually be adding much more normalized metadata to this response, including margin requirements, lot size, expiry, strike price, and more.
</aside>

|Name|Type|Required|Description|
|---|---|---|---|---|
|symbol|[Market](#market)|True|The market symbol, formatted as mentioned [above](#market), which uniquely identifies the market|
|assetType|[AssetType](#assettype)|True|The type of asset this market is for|
|baseAsset|[AbstractToken](#abstracttoken)|True|For derivatives, this is the underlying asset of the instrument being bought and sold. For spot markets, this is itself the instrument being bought and sold|
|quoteAsset|[AbstractToken](#abstracttoken)|True|Prices for this market are expressed in units of quoteAsset|
|marginAsset|[AbstractToken](#abstracttoken)|False|The asset which is used as collateral for this market. Only exists for markets that allow margin trading|