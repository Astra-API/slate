## Orderbook Updates Channel

Subscribe to any exchanges orderbook updates. This makes use of the `Subscription` data type to record which type (ORDERBOOK) and the specific asset pair the developer is interested in.

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
        "dataType": "ORDERBOOK"
    }
}
```

> Sample Push Data

```json
{
    "updateId": 37828320367,
    "exchange": "BINANCE",
    "market": {
        "baseAsset": {
            "type": "SPOT",
            "asset": "BTC"
        },
        "quoteAsset": "USDT"
    },
    "bids": [
        {
            "price": 30708.01,
            "size": 1.26141
        },
        {
            "price": 30707.97,
            "size": 0.00571
        }
    ],
    "asks": [
        {
            "price": 30708.02,
            "size": 12.005
        },
        {
            "price": 30708.1,
            "size": 0.08388
        }
    ]
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|action|[Action](#action)|True|Interaction with a specific channel|
|payload|[Subscription](#subscription)|True|Subscription data type describing orderbook update specifics|

### Action

|Value|Description|
|---|---|
|SUBSCRIBE|Subscribe to a channel|
|UNSUBSCRIBE|Unsubscribe from a channel|

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