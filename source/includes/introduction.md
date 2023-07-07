# Introduction

> Scroll down for example requests and responses.

Welcome to the Astra API documentation for traders and developers. The docs detail API infrastructure and functionality of connecting to various crypto exchanges.

The API is separated intow three categories: Public HTTP API, Private HTTP API, and Websockets API. 

-   Private HTTP API requests require authentication and enable users to place orders and view exchange specific account information

- Public HTTP and Websockets API's both public, though future support for private websocket API may arrive.

### General Information

- REST Feed: `https://prod.astra-api.dev`
- WEBSOCKET Feed: `wss://prod.astra-api.dev/ws`

- All `String` type parameters are passed in `UPPERCASE` only, unless written otherwise in a information tag.

- Features are continously in development, and this API documentation will routinely update as features are rolled out.

- If you have suggestions, please reach out to contact@astra-api.dev.

### Supported Exchanges and Asset Types

- We currently support (select features) on Binance, Coinbase, Huobi, and OKX.

- We currently support asset types: SPOT and FUTURES.
