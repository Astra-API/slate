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
    "side": "BUY"
  }
```

Astra represents all orders you've initiated in this `Order` similar to a `Trade` object, in addition to including the specific order `id` tied to the order.

<aside class="success">
Similarity in order and trade objects is intuitive! <code>Trade</code> updates returned from Astra are <code>Order</code> messages from other traders.
</aside>

|Name|Type|Required|Description|
|---|---|---|---|---|
|id|String|True|ID of the order on the exchange|
|baseAsset|[Asset](#asset)|True|Base asset of market|
|quoteAsset|[Abstract Spot Asset](#abstract-spot-asset)|True|Quote asset of market|
|price|Float (f64)|True|Price of the order (in units of quoteAsset)|
|quantity|Float (f64)|True|Quantity of the order (in units of baseAsset)|
|side|[Side](#side)|True|Buy or sell order|

### Side 

|Value|Description|
|---|---|
|SELL|Taker is selling the asset|
|BUY|Taker is buying the asset|