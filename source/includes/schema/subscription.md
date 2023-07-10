## Subscription

> Sample Data

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

`Subscription` messages are the single unified data format Astra will convert into the specifc formatting, syntax, and related details an exchange requires to retrieve information.

Example 1:

Developers use `Subcription` to specify which update channels they'd like to subscribe to. Information about different types of channels are found in 'Websocket API'. 


|Name|Type|Required|Description|
|---|---|---|---|---|
|exchange|[[Exchange](#exchange)]|True|Exchange to fetch data from.|
|market|[[Market](#market)]|True|Market details. See Schema > #Market.|
|dataType|[[Data Type](#data-type)]|True|Type of market updates.|


### Data Type

|Value|Description|
|---|---|
|ORDERBOOK|Orderbook updates|
|TRADE|Trade updates|
