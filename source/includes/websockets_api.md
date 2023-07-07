# Websockets API

<!-- Default `content-Type`: `application/json` -->

The Websocket endpoint is available without authentication. Once the socket is connected, you can subscribe to a channel by sending a `subscribe` message, detailed in Schema.

Endpoint: `wss://prod.astra-api.dev/ws`

## Subscribing

You can subscribe to a channel by sending a `subscribe` message through the websocket connection:

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
|» subscribe|Subscribe to a channel|
|» unsubscribe|Unsubscribe from a channel|

<!-- 
### Subscription

|Parameter|Type|Default|Description|
|---|---|---|---|
|exchange|string|*required*|Action to perform|
|market|string|*required*|Exchange to subscribe/unsubscribe|
|dataType|[DataType](#datatype)|*required*|ID of an order on an exchange| -->

### DataType

|Value|Description|
|---|---|
|» orderbook|Orderbook updates|
|» trade|Trade updates|


## Orderbook Channel

Subscribe to any exchanges orderbook snapshot updates. 

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


## Trades Channel

Subscribe to any exchange's latest trade updates. Updates recieved are the latest trades
from the respective 

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
    "exchange_market": {
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
|trades|[[Trade]](#trade)|True|List of trades that have occurred since last message|