## Subscribing

You can subscribe to multiple different exchange's specific Trade or Orderbook Updates channel concurrently by forwarding an list of `Subscription` messages through the WebSocket connection. 

To understand more about how Astra handles the subscribing of exchanges, please see the `Subcription` data type in the Schema tab.

> Sample message

```json
{
  "action": "SUBSCRIBE",
  "payload": {
      "exchange": "BINANCE",
      "market": {
        "baseAsset": {
          "type": "SPOT",
          "asset": "BTC"
        },
        "quoteAsset": "USDT"
      },
      "dataType": "ORDERBOOK"
    }
}
```

### Message

|Parameter|Type|Default|Description|
|---|---|---|---|
|action|[Action](#action)|True|Action to perform|
|payload|[Subscription](#subscription)|True|A subscription object defining specifics of the to be subscribed channel|


### Action

|Value|Description|
|---|---|
|SUBSCRIBE|Subscribe to a channel|
|UNSUBSCRIBE|Unsubscribe from a channel|

<!-- 
### Subscription

|Parameter|Type|Default|Description|
|---|---|---|---|
|exchange|string|*required*|Action to perform|
|market|string|*required*|Exchange to subscribe/unsubscribe|
|dataType|[DataType](#datatype)|*required*|ID of an order on an exchange| -->