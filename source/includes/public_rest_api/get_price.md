
## Get Price

`GET /price`

Returns the current price of the specified market.

> Sample Request

```json
{
  "exchange": "BINANCE",
  "baseAsset": {
      "type": "SPOT",
      "asset": "BTC"
  }, 
  "quoteAsset": "USDT",
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[Exchange](#exchange)|True|Exchange to fetch data from|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|

> Sample Response

```json
27879.5
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|Float (f64)|True|Price of the asset in units of quote asset|