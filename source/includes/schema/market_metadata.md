## MarketMetadata

> Sample Data

Metadata associated with a particular market.

This includes

|Name|Type|Required|Description|
|---|---|---|---|---|
|symbol|[Market](#market)|True|The market symbol, formatted as mentioned [above](#market), which uniquely identifies the market|
|assetType|[AssetType](#assettype)|True|The type of asset this market is for|
|baseAsset|[AbstractSpotAsset](#abstract-spot-asset)|True|For derivatives, this is the underlying asset of the instrument being bought and sold. For spot markets, this is itself the instrument being bought and sold|
|quoteAsset|[AbstractSpotAsset](#abstract-spot-asset)|True|Prices for this market are expressed in units of quoteAsset|
|marginAsset|[AbstractSpotAsset](#abstract-spot-asset)|True|The asset which is used as collateral for this market|