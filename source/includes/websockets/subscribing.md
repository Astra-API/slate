## Subscribing

You can have one active market data subscription per WebSocket connection. A "subscription" consists of a combination of a market and the data type you are subscribing to.

```
wss://prod.astra-api.dev/ws?market=BINANCE-PERP-BTC-USDT&dataType=ORDERBOOK
```

These are specified as query parameters in the initial connection request, as shown:

<aside class="notice">
We will soon be adding support for switching the active subscription for a WebSocket connection that is already open.
</aside>

<!-- You can subscribe to multiple different exchange's specific Trade or Orderbook Updates channel concurrently by forwarding an list of `Subscription` messages through the WebSocket connection.  -->

<!-- To understand more about how Astra handles the subscribing of exchanges, please see the `Subcription` data type in the Schema tab. -->

<!-- > Sample message

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
``` -->

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|market|[Market](#market)|True|The market which you are requesting data for|
|dataType|[DataType](#data-type)|True|The type of market data you want to stream|

<!-- ### Message

|Value|Description|
|---|---|
|SUBSCRIBE|Subscribe to a channel|
|UNSUBSCRIBE|Unsubscribe from a channel| -->

<!-- 
### Subscription

|Parameter|Type|Default|Description|
|---|---|---|---|
|exchange|string|*required*|Action to perform|
|market|string|*required*|Exchange to subscribe/unsubscribe|
|dataType|[DataType](#datatype)|*required*|ID of an order on an exchange| -->