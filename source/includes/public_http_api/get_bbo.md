
## Get Best Bid/Offer

`GET /bbo`

Returns the current BBO of the specified market on the specified exchange.

> Sample Request

```json
{
  "exchange": "BINANCE",
  "baseAsset": "BTC",
  "quoteAsset": "USDT",
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[[Exchange](#exchange)]|True|Exchange to fetch data from|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|

> Successful Sample Response

```json
{
  "bid": {
    "price": 27879.5,
    "quantity": 1.5,
  },
  "ask": {
    "price": 27879.5,
    "quantity": 1.5,
  }
}
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|bid|[Bid](#bid)|True|Current best bid of the market|
|ask|[Ask](#ask)|True|Current best ask of the market|

