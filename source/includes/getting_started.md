# Getting Started

### 1. Create an account

First, create an account with us here: <https://terminal.astra-api.dev/settings/apikeys>. You can use your Astra account to access all of our products and services.

![Astra Terminal login page](astra-terminal-login-page.png)


### 2. Create an API key

Navigate to <https://terminal.astra-api.dev/settings/apikeys> and create an API key. The key will only be displayed once upon creation, so make sure you save it.

![Astra Terminal API keys page](astra-terminal-api-keys-page.png)


### 3. Send your first request

**Endpoints**

You can use the following endpoints to access our hosted API:

- REST endpoint: `https://prod.astra-api.dev`
- WebSocket endpoint: `wss://prod.astra-api.dev/ws`


**Authentication**

All requests to Astra API need to be authenticated

```
{
    "x-astra-api-key": "Bearer kadjfasfl.KjUBAhdIafaDFSCsajfaIowSADxkaw"
}
```

You can authenticate by specifying a header named `x-astra-api-key` with the value `Bearer {KEY}`, where you replace "KEY" with the value of your API key. For example, if the API key you created in the previous step was `kadjfasfl.KjUBAhdIafaDFSCsajfaIowSADxkaw`, you would include the header displayed to the right.

Requests to the public market data endpoints do not require any additional authentication beyond your Astra API key. Private endpoints also require you to provide your exchange API keys for the specific exchange(s) you are trading on. More info on how to do this will be released once we enable support for private endpoints (currently in development).

**Send a request**

> Sample Request

```bash
curl --location 'http://prod.astra-api.dev/orderbook?market=BINANCE-SPOT-BTC-USDT' \
--header 'x-astra-api-key: Bearer {ASTRA_API_KEY}'
```

> Sample Response

```json
{
    "bids": [
        {"price": 51485.41, "quantity": 4.10646},
        {"price": 51485.39, "quantity": 0.00975},
        {"price": 51485.38, "quantity": 0.00975},
    ],
    "asks": [
        {"price": 51485.42, "quantity": 2.21005},
        {"price": 51485.59, "quantity": 0.77624},
        {"price": 51485.89, "quantity": 0.38811},
    ]
}
```

Use your favorite HTTP client to send a market data request. Here's an example curl command you can use:

Replace `{ASTRA_API_KEY}` with the API key that you just generated. You should receive a response with a current snapshot of the orderbook for that market!
