## Get Deposit Address

`GET /deposit-address/{account_id}`

Fetches the deposit address for a specific account and network. Returns the address where users can send funds to be credited to their account.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to get the deposit address for|
|network|String|True|The blockchain network (e.g., "bitcoin", "ethereum", "base")|

> Sample Request

```bash
GET /deposit-address/{account_id}?network=bitcoin
```

> Sample Response

```json
{
  "address": "bc1qexample1234567890abcdef1234567890"
}
```

### Response

|Name|Type|Description|
|---|---|---|
|address|String|The deposit address for the specified network|

### Networks

|Network|Description|
|---|---|
|bitcoin|Bitcoin network|
|ethereum|Ethereum mainnet (coming soon)|
|base|Base network (coming soon)|
|arbitrum|Arbitrum network (coming soon)|
|solana|Solana network (coming soon)|
|avalanche|Avalanche C-Chain (coming soon)|
|optimism|Optimism network (coming soon)|
|polygon|Polygon network (coming soon)|
|bsc|Binance Smart Chain (coming soon)|
|algorand|Algorand network (coming soon)|
|noble|Noble network (coming soon)|
|stellar|Stellar network (coming soon)|
|sui|Sui network (coming soon)|
