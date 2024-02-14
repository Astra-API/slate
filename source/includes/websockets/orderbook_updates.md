## Orderbook Channel

> Sample Request

```
wss://prod.astra-api.dev/ws?market=BINANCE-PERP-BTC-USDT&dataType=ORDERBOOK
```

> Sample Data Message

```json
{
    "updateId": 37828320367,
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

Streams L2 orderbook updates from the specified market.

For each exchange, we've used whichever endpoint returns the most fine-grained orderbook updates with the lowest latency. For some exchanges, this is one update per tick, and for some exchanges, batched updates are the best that is available. [Contact us](mailto:contact@astra-api.dev) for more information about how this is implemented under the hood.


### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|updateId|u64|True|Sequence ID for the orderbook update. <br/><br/> The exact format of this parameter may differ depending on the exchange, but it can be used to sequence updates. For any given market, updates with larger sequence IDs occurred later in time|
|bids|Array<[Bid](#bid)>|True|List of updates to bids. <br/><br/> An update with parameters `updateId`,`price` and `quantity` means that the aggregated bid at price `price` was updated from its old quantity to `quantity` at the time indicated by the sequence number `updateId`|
|asks|Array<[Ask](#ask)>|True|List of updates to asks|


<!-- ### Action

|Value|Description|
|---|---|
|SUBSCRIBE|Subscribe to a channel|
|UNSUBSCRIBE|Unsubscribe from a channel| -->


<!-- ```json
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
``` -->


<!-- ### OrderbookUpdate
|Parameter|Type|Required|Description|
|---|---|---|---|
|side|string|True|Side for the update|
|price|number|True|Price level for the update|
|quantity|number|True|New quantity for bid at this price level|
|sequenceNumber|number|True|Sequence number for update| -->