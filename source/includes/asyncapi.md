# Websockets API

Default `content-Type`: `application/json`

The Websocket endpoint is available without authentication. Once the socket is connected, you can subscribe to a channel by sending a 'subscribe' message.

Endpoint: TBD

## Subscribing

You can subscribe to a channel by sending a `subscribe` message through the websocket connection:

> Example message

```json
{
  "action": "subscribe",
  "subscriptions": [
    {
      "exchange": "binance",
      "market": {
        "baseAsset": "BTC",
        "quoteAsset": "USDT"
      },
      "dataType": "orderbook"
    },
    {
      "exchange": "coinbase",
      "market": {
        "baseAsset": "ETH",
        "quoteAsset": "USD"
      },
      "dataType": "trade"
    }
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

> Example message

```json
{
  "bids": [
    {
      "side": "buy",
      "price": 27000.00,
      "quantity": 1.00
    },
    {
      "side": "buy",
      "price": 26000.00,
      "quantity": 2.00
    }
  ],
  "asks": [
    {
      "side": "sell",
      "price": 28000.00,
      "quantity": 1.00
    },
    {
      "side": "sell",
      "price": 29000.00,
      "quantity": 2.00
    }
  ],
}
```

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

> Example message

```json
{
  "trades": [
    {
      "price": 0,
      "quantity": 0,
      "side": "buy",
      "timestamp": 1679899308.07
    },
    {
      "price": 0,
      "quantity": 0,
      "side": "sell",
      "timestamp": 1679899208.07
    }
  ]
}
```

### Message

|Parameter|Type|Required|Description|
|---|---|---|---|
|trades|[[Trade]](#trade)|true|List of trades that have occurred since last message|