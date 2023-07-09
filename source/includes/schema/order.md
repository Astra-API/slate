## Order

> Sample Data

```json
{
    "id": "123456789",
    "baseAsset": {
      "type": "SPOT",
      "asset": "BTC"
    }, 
    "quoteAsset": "USD",
    "price": 20000.00,
    "quantity": 1.2,
    "side": "buy"
  }
```

Astra represents all orders you've initiated in this `Order` similar to a `Trade` object, in addition to including the specific order `id` tied to the order.

<aside class="success">
Similarity in order and trade objects is intuitive! <code>Trade</code> updates returned from Astra are <code>Order</code> messages from other traders.
</aside>

|Name|Type|Required|Description|
|---|---|---|---|---|
|id|String|True|ID of the order on the exchange|
|baseAsset|[[Base Asset](#base-asset)]|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|
|price|number|True|Price of the order (in units of quoteAsset)|
|quantity|number|True|Quantity of the order (in units of baseAsset)|
|side|String|True|Buy or sell order|