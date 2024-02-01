
## Get Best Bid/Offer

`GET /bbo`

Returns the current BBO of the specified market on the specified exchange.

> Sample Request

```json
{
  "exchange": "OKX",
  "baseAsset": {
      "type": "SPOT",
      "asset": "SOL"
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

> Successful Sample Response

```json
{
  "bid": {
    "price": 20.19,
    "quantity": 1.5,
  },
  "ask": {
    "price": 20.15,
    "quantity": 1.5,
  }
}
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|bid|[Bid](#bid)|True|Current best bid of the market|
|ask|[Ask](#ask)|True|Current best ask of the market|

