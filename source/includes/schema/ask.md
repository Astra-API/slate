## Ask

> Sample Data

```json
//  This is a sample Ask in relation to the 
//  BTC USDT Market example above.
{
    "price": 27500.00,
    "quantity": 1,
}
```



An ask represents the price at which a buyer is willing to purchase a financial instrument or asset in a trading market. Astra represents a bid through a `Bid` across all exchanges.Astra represents an ask through an `Ask` across all exchanges.


|Name|Type|Required|Description|
|---|---|---|---|---|
|price|Float (f64)|True|Price of the ask (in units of quoteAsset)|
|quantity|Float (f64)|True|Quantity of the ask (in units of baseAsset)|
