## Get Express Deposit Address

`GET /express-deposit-address`

Fetches the express deposit address for a specific coin and network. Express deposits are processed faster, but *must* be sent from a linked address.

Express deposits have the following requirements:

- Must be sent from a [linked address](https://terminal.astra-api.dev/settings/linkedAddresses)
- For UTXO chains (Bitcoin, etc.), all input UTXOs must be from linked addresses
- Processed faster than standard deposits

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|coin|String|True|The coin symbol (e.g., "BTC", "ETH", "USDC")|
|network|String|True|The blockchain network (e.g., "bitcoin", "ethereum", "base")|

> Sample Response

```json
{
  "address": "bc1qexample1234567890abcdef1234567890"
}
```

### Response

|Name|Type|Description|
|---|---|---|
|address|String|The express deposit address for the specified coin and network|

