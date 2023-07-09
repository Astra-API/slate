## Market

> Sample Data

```json
 {
    "baseAsset": {
        "type": "SPOT",
        "asset": "BTC"
    },
    "quoteAsset": "USDT"
  }
```

Definition: 

Astra represent asset pairs across every exchange through a `Market`. This represents an exchange agnostic tradeable market consisting of a base asset and quote asset.

Example 1: 

Developers use `Market` to define what asset pairs they'd like to receive updates for in `Subscription` messages.

Example 2:

ASTRA uses `Market` when returning the complete list of supported markets using the `/markets` REST endpoint. For examples, refer to 'Public HTTP API' > 'Get Markets'.

|Name|Type|Required|Description|
|---|---|---|---|---|
|baseAsset|[[Asset](#asset)]|True|Describes the type and name of asset|
|quoteAsset|[[Abstract Spot Asset](#abstract-spot-asset)]|True|Asset which price is in units of.|