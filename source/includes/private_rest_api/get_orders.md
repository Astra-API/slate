## Get Orders

`GET /orders`

Fetches the user's open orders for the specified market.

<aside class="notice">
Coming soon!
</aside>

<!-- > Sample Request

```json
{
	"exchange": "BINANCE",
	"baseAsset": {
      "type": "SPOT",
      "asset": "BTC"
  },
	"quoteAsset": "USDT"
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
[
  {
    "id": "123456789",
    "baseAsset": {
      "type": "SPOT",
      "asset": "BTC"
    }, 
    "quoteAsset": "USD",
    "price": 20000.00,
    "quantity": 1.2,
    "side": "buy"
  },
  {
    "id": "2345678910",
    "baseAsset": {
      "type": "SPOT",
      "asset": "ETH"
    }, 
    "quoteAsset": "USD",
    "price": 1200.00,
    "quantity": 2.4,
    "side": "sell"
  }
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Order]](#order)|True|List of open orders| -->
