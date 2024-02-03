
## Get Orderbook

> Sample Request

```bash
GET /orderbook?market=BINANCE-SPOT-ETH-USDT
```

> Sample Response

```json
{
  "bids": [
    {
      "price": 1798.00,
      "quantity": 1.5,
    },
    {
      "price": 1797.01,
      "quantity": 5.0,
    }
  ],
  "asks": [
    {
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

`GET /orderbook`

Returns a snapshot of the current L2 orderbook for the specified market. Bids are sorted in descending order of price, and asks are sorted in ascending order. The quantity at each price level corresponds to the aggregate of all open orders at that price.

### Request

| Parameter | Type               | Required | Description                                   |
|-----------|--------------------|----------|-----------------------------------------------|
| market    | [Market](#market)  | True     | Market to fetch data for                      |

### Response

| Name | Type               | Required | Description                                   |
|------|--------------------|----------|-----------------------------------------------|
| bids | Array<[Bid](#bid)> | True     | List of aggregated buy orders  |
| asks | Array<[Ask](#ask)> | True     | List of aggregated sell orders |