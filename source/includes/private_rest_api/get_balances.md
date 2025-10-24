## Get Balances

`GET /balances/{account_id}`

Fetches the balances of this account. Returns a mapping of instrument IDs to their balance details.

If you have a balances in a blockchain token, the response will contain fields identifying the network
and contract address of the token.

Some instruments, like popular stablecoins (USDC, USDT) and native tokens (BTC, ETH), are considered blockchain-agnostic in our systems, and will show up without a network or address.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to fetch balances for|

> Sample Response

```json
{
  "123e4567-e89b-12d3-a456-426614174000": {
    "instrumentId": "123e4567-e89b-12d3-a456-426614174000",
    "symbol": "BTC",
    "amount": "1.21",
    "network": null,
    "address": null 
  },
  "456e7890-e89b-12d3-a456-426614174001": {
    "instrumentId": "456e7890-e89b-12d3-a456-426614174001",
    "symbol": null,
    "amount": "5.67",
    "network": "ethereum",
    "address": "0x1f9840a85d5aF5bf1D1762F925BDADdC4201F984"
  },
  "789e0123-e89b-12d3-a456-426614174002": {
    "instrumentId": "789e0123-e89b-12d3-a456-426614174002",
    "symbol": "USD",
    "amount": "10.11",
    "network": null,
    "address": null
  }
}
```

### Response

The response is a JSON object where:
- **Keys** are instrument IDs (UUIDs)
- **Values** are balance objects containing detailed information about each asset

|Name|Type|Description|
|---|---|---|
|instrumentId|UUID|The unique identifier for the instrument|
|symbol|String or null|The symbol of the asset (e.g., "BTC", "ETH", "SOL")|
|amount|String|The current balance amount as a decimal string|
|network|String or null|The blockchain network for this asset (e.g., "bitcoin", "ethereum", "solana")|
|address|String or null|The contract address for this token on the specified network|
