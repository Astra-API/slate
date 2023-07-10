
## Get Orderbook

`GET /orderbook`

Returns a snapshot of the current L2 orderbook for the specified market. Bids are sorted in descending order, and asks are sorted in ascending order. Because it is an L2 snapshot, bids and asks are aggregated by price level.

> Sample Request

```json
{
	"exchange": "HUOBI",
	"baseAsset": {
      "type": "SPOT",
      "asset": "ETH"
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

> Successful Sample Response

```json
{
  "bids": [
    {                       //  Bid Data Type
      "price": 1798.00,
      "quantity": 1.5,
    },
    {
      "price": 1797.01,
      "quantity": 5.0,
    }
  ],
  "asks": [
    {                       //  Ask Data Type
      "price": 1798.00,
      "quantity": 1,
    },
    {
      "price": 1797.00,
      "quantity": 10.0,
    }
  ]
}

```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|bids|[[Bid](#bid)]|True|List of buy orders — Bid data type. See Schema.|
|asks|[[Ask](#ask)]|True|List of sell orders — Ask data type. See Schema.|