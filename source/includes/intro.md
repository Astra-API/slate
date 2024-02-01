# Introduction

## Astra API

> Scroll down for example requests and responses.

Astra API is a unified API for crypto trading. It provides direct market access (DMA) to multiple trading venues, including crypto exchanges, DEXes, and OTC desks. Features include:

- Real-time L2 market data via REST and WebSocket
- Multi-asset support, including spot, perpetuals, expiring futures and options markets
- Normalization of data for all endpoints
- Low latency
- (coming soon!) Order placement, cancellation, and smart order routing
- (coming soon!) Fetching user data like fills, orders, positions, balances, and margin info
- (coming soon!) Colocation with exchanges
- (coming soon!) Historical market data
- (coming soon!) Transfers endpoints
- (coming soon!) Support for leveraged tokens, spot margin, and more

Astra API is perfect for trading firms, OTC desks, fintechs, brokerages, neobanks, and other businesses who want a performant, robust, and easy-to-use DMA product.

### Supported exchanges

We currently support:

- Binance
- Coinbase
- OKX
- HTX (Huobi)
- Kraken
- KuCoin

<!-- - dYdX V4 -->

The list is growing quickly, and we plan to add support for several more exchanges and DEXes in the coming months. If there's a specific trading venue that you'd like us to prioritize, please [contact us](mailto:contact@astra-api.dev).

If you're an exchange or other trading venue, and you want us to integrate with your platform, please [contact us](mailto:contact@astra-api.dev).

### Supported endpoints

See below for a detailed list of the endpoints we support:

- [Public market data via WebSocket](#websockets-api)
- [Public market data via REST](#public-rest-api)
- [Private trading data via REST](#private-rest-api)


<aside class="notice">
<b>NOTE:</b> Astra API is still in its alpha release, so you may observe some occasional unexpected behaviour for edge cases. If you see something that looks off, please notify us at <a href="mailto:contact@astra-api.dev">contact@astra-api.dev</a> and we will look into it ASAP.
<br/>
<br/>
Additionally, the API surface is still in flux, and may change as we get closer to a stable release. If you need a stable API for your use-case, please contact us.
</aside>

## How does it work?




<!-- ## OTC

We've also used our expertise in exchange connectivity to build a best-in-class OTC desk serving transactions of all sizes.

Our OTC service provides access to deep liquidity across all assets, chains, and  

, access deep liquidity 


Our OTC service is 



In addition to Astra

market access to crypto markets, while also accessing the full spectrum of liquidity and never compromising on pr

seamless access to crypto markets without the hassle of dealing


The API is separated into three categories: Public HTTP API, Private HTTP API, and Websockets API. 

- Private HTTP API requests require authentication and enable those users to place orders and view user sepcific data.

- Public HTTP and Websocket API's are both public, accessible to all users. -->
