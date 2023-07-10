## Trades Channel

Subscribe to any exchange's latest trade updates. There is one `Trade` update per message sent.

> Sample Message

```json
{
    "action": "SUBSCRIBE",
    "payload": {
        "exchange": "BINANCE",
        "market": {
            "baseAsset": {
                "type": "SPOT",
                "asset": "ETH"
            },
            "quoteAsset": "USDT"
        },
        "dataType": "TRADE"
    }
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

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|action|[Action](#action)|True|Interaction with a specific channel|
|payload|[Subscription](#subscription)|True|Subscription data type describing trade update specifics|

### Action

|Value|Description|
|---|---|
|SUBSCRIBE|Subscribe to a channel|
|UNSUBSCRIBE|Unsubscribe from a channel|

### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|-|[[Trade]](#trade)|True|List of trades that have occurred since last message|