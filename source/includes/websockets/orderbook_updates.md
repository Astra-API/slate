## Orderbook Updates Channel

Subscribe to any exchanges orderbook updates. This makes use of the `Subscription` data type to record which type (ORDERBOOK) and the specific asset pair the developer is interested in.

> Sample Message

```json
{
"action": "SUBSCRIBE",
    "subscriptions": [
    {
      "exchange": "BINANCE",
      "market": {
        "baseAsset": "BTC",
        "quoteAsset": "USDT"
      },
      "dataType": "ORDERBOOK"
    },
  ]
}
```

> Sample Push Data

```json
{
  "bids": [
    {
      "side": "buy",
      "price": 27000.00
    },
    {
      "side": "buy",
      "price": 26000.00
    }
  ],
  "asks": [
    {
      "side": "sell",
      "price": 28000.00
    },
    {
      "side": "sell",
      "price": 29000.00
    }
  ],
}
```

### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|bids|[[Bids]](#bid)|True|List of updates to bids|
|asks|[[Asks]](#ask)|True|List of updates to asks|

<!-- ### OrderbookUpdate
|Parameter|Type|Required|Description|
|---|---|---|---|
|side|string|True|Side for the update|
|price|number|True|Price level for the update|
|quantity|number|True|New quantity for bid at this price level|
|sequenceNumber|number|True|Sequence number for update| -->