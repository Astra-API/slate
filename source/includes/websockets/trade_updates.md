## Trades Channel

> Sample Request

```
wss://prod.astra-api.dev/ws?market=BINANCE-PERP-BTC-USDT&dataType=TRADE
```

> Sample Data Message

```json
{
    "trades": [
        {
            "price": 47104.0,
            "quantity": 0.003,
            "side": "SELL",
            "time": 1707527023484
        },
        {
            "price": 47100.1,
            "quantity": 0.0015,
            "side": "BUY",
            "time": 1707527025010
        }
    ]
}
```

Streams trade updates from the specified market.

For each exchange, we've used whichever endpoint returns the most fine-grained trade updates with the lowest latency. For some exchanges, this is one update per trade, and for some exchanges, batched updates are the best that is available. [Contact us](mailto:contact@astra-api.dev) for more information about how this is implemented under the hood.


### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|trades|Array<[Trade](#trade)>|True|List of trades that have occurred since last message|


<!-- ### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|action|[Action](#action)|True|Interaction with a specific channel|
|payload|[Subscription](#subscription)|True|Subscription data type describing trade update specifics|

### Action

|Value|Description|
|---|---|
|SUBSCRIBE|Subscribe to a channel|
|UNSUBSCRIBE|Unsubscribe from a channel|

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
``` -->
