## Get Balances

`GET /balances/{account_id}`

Fetches the balances of this account. Returns a mapping of asset symbols to their current balances.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to fetch balances for|

> Sample Response

```json
{
  "BTC": "1.21",
  "ETH": "5.67",
  "SOL": "10.11",
  "USDC": "1000.00"
}
```

### Response

The response is a JSON object where:
- **Keys** are asset symbols (strings)
- **Values** are the current balance amounts (strings representing decimal numbers)

|Name|Type|Description|
|---|---|---|
|asset|String|The symbol of the asset (e.g., "BTC", "ETH", "USDC")|
|balance|String|The current balance amount as a decimal string|
