## Bid

> Sample Data

```json
{
    "price": 27879.5,
    "quantity": 1.5,
}
```

Represents a buy order on a particular market.

| Name     | Type | Required | Description                                   |
|----------|------|----------|-----------------------------------------------|
| price    | f64  | True     | Price of the bid (in units of quoteAsset)     |
| quantity | f64  | True     | Quantity of the bid (in units of baseAsset)   |