## Subscribing

You can subscribe to multiple different exchange's specific Trade or Orderbook Updates channel concurrently by forwarding an list of `Subscription` messages through the websocket connection. 

To understand more about how ASTRA handles the subscribing of exchanges, please see the `Subcription` data type in the Schema tab.

> Sample message

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
    {
      "exchange": "COINBASE",
      "market": {
        "baseAsset": "ETH",
        "quoteAsset": "USD"
      },
      "dataType": "TRADE"
    }
  ]
}
```

### Message

|Parameter|Type|Default|Description|
|---|---|---|---|
|action|[Action](#action)|True|Action to perform|
|subscriptions|[[Subscription]](#subscription)|True|List of subscription objects defining specifics of each subscribed channel|


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