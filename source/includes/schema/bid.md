## Bid

> Sample Data

```json
//  This is a sample Bid in relation to the 
//  BTC USDT Market example above.
{
    "price": 27879.5,
    "quantity": 1.5,
}
```
A bid represents the price at which a buyer is willing to purchase a financial instrument or asset in a trading market. ASTRA represents a bid through a `Bid` across all exchanges.

 For usage, refer to 'Public HTTP API' > 'Get BBO'. 

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|Float (f64)|True|Price of the bid (in units of quoteAsset)|
|quantity|Float (f64)|True|Quantity of the bid (in units of baseAsset)|