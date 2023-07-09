# Introduction

> Scroll down for example requests and responses.

Welcome to the Astra API documentation for traders and developers. ASTRA eliminates the often complex, unpredictable, and unstable behavior of communciating with cryptocurrency exchanges.

ASTRA provides fast reliable connections to several exchanges to users.

ASTRA distills a myriad of different exchange specific data packets into ASTRA's unified data formats, designed to swiftly integrate with developers' trading systems.

Users leverage ASTRA by forwarding unified data formats (JSON's) containing exchange and market specific requests to the API which ASTRA transform into exchange compatible messages, speedily returning useful data.

The API is separated into three categories: Public HTTP API, Private HTTP API, and Websockets API. 

- Private HTTP API requests require authentication and enable those users to place orders and view user sepcific data.

- Public HTTP and Websockets API's are both public, accessible to all users.

### General Information

- REST Endpoint: `https://prod.astra-api.dev`
- WEBSOCKET Endpoint: `wss://prod.astra-api.dev/ws`

Features are continously in development, and this API documentation will routinely update as features are rolled out.

If you have suggestions, please reach out to contact@astra-api.dev.

### Supported Exchanges and Asset Types

- We currently support (select features) on BINANCE, COINBASE, KUCOIN, HUOBI, and OKX.

- We currently support asset types: SPOT and PERPETUALS.
