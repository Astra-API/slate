## Ask

> Sample Data

```json
{
    "price": 27500.00,
    "quantity": 1,
}
```

Represents a sell order on a particular market.

| Name     | Type        | Required | Description                                   |
|----------|-------------|----------|-----------------------------------------------|
| price    | Float (f64) | True     | Price of the ask (in units of quoteAsset)     |
| quantity | Float (f64) | True     | Quantity of the ask (in units of baseAsset)   |