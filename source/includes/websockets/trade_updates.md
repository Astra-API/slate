## Trades Channel

Subscribe to any exchange's latest trade updates. There is one `Trade` update per message sent.

> Sample Message

```json
{
"action": "SUBSCRIBE",
  "subscriptions": [
    {
      "exchange": "COINBASE",
      "market": {
        "baseAsset": "BTC",
        "quoteAsset": "USDT"
      },
      "dataType": "TRADE"
    },
  ]
}
```

> Sample Push Data

```json
{
    "exchangeMarket": {
        "exchange": "COINBASE",
        "market": {
            "baseAsset": {
                "type": "SPOT",
                "asset": "BTC"
            },
            "quoteAsset": "USDT"
        }
    },
    "price": 30157.8,
    "quantity": 0.01048,
    "side": "Buy"
}
```

### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|-|[[Trade]](#trade)|True|List of trades that have occurred since last message|