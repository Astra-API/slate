# Websockets API

Default `content-Type`: `application/json`

The Websocket endpoint is available without authentication. Once the socket is connected, you can subscribe to a channel by sending a 'subscribe' message.

Endpoint: TBD

## Subscribing

You can subscribe to a channel by sending a `subscribe` message through the websocket connection:

```json
{
  "action": "subscribe",
  "subscriptions": [

  ]
}
```

### Message

|Parameter|Type|Default|Description|
|---|---|---|---|
|action|[Action](#action)|*required*|Action to perform|
|subscriptions|[[Subscription]](#subscription)|true|Exchange to subscribe/unsubscribe|
|orderId|string|true|ID of an order on an exchange|

### Action

|Value|Description|
|---|---|
|» subscribe|Subscribe to a channel|
|» unsubscribe|Unsubscribe from a channel|


### Subscription

|Parameter|Type|Default|Description|
|---|---|---|---|
|exchange|string|*required*|Action to perform|
|market|string|*required*|Exchange to subscribe/unsubscribe|
|dataType|[DataType](#datatype)|*required*|ID of an order on an exchange|

### DataType

|Value|Description|
|---|---|
|» orderbook|Orderbook updates|
|» trade|Trade updates|


## Orderbook Channel

### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|bids|[[OrderbookUpdate]](#orderbookupdate)|true|List of updates to bids|
|asks|[[OrderbookUpdate]](#orderbookupdate)|true|List of updates to asks|

### OrderbookUpdate
|Parameter|Type|Required|Description|
|---|---|---|---|
|side|string|true|Side for the update|
|price|number|true|Price level for the update|
|quantity|number|true|New quantity for bid at this price level|
|sequenceNumber|number|true|Sequence number for update|


## Trades Channel

### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|trades|[[Trade]](#trade)|true|List of trades that have occurred since last message|