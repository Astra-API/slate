# Introduction to Astra API

> Scroll down for example requests and responses.

### What is it?

Astra API is a unified API for crypto markets. The API provides direct market access (DMA), i.e. it gives you fine-grained read and write access to the underlying orderbook on many different trading venues - including centralized exchanges, DEXes, and OTC desks.

Astra API takes care of data normalization, so you don't have to implement 10 different integrations for 10 different trading venues. Instead, you can just build one integration using Astra's unified data format, and use it for every trading venue.


### Who is it for?

Astra API is perfect for any business that needs to build performant, robust, and easy-to-use connections to crypto markets. This includes: trading firms, individual traders, OTC desks, institutional investors, fintech companies, brokerages, neobanks, and exchanges.

Integrating with our API is easy. Any developer can get started with Astra API in minutes, using the documentation on this page.


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


### Supported asset types

We currently support the following asset types for each of the above exchanges:

- Spot
- Perpetual Futures
- Expiring Futures
  - for futures, we support both USD-margined and coin-margined contracts
- Options
- (coming soon!) Leveraged Tokens
- (coming soon!) Spot Margin


### Supported endpoints

See below for a detailed list of the endpoints we support:

- [Public market data via WebSocket](#websockets-api)
- [Public market data via REST](#public-rest-api)
- [Private trading data via REST](#private-rest-api)


### How it works

If you are using Astra API for fetching real-time market data, all you need to get started is an API key, which you can get by following the steps [below](#getting-started).

In order to use Astra API for order management, execution, or position management, you need to first do the following for each exchange you wish to trade on:

1. Create an account
2. Perform KYC verification if applicable
  - This is common for centralized exchanges, but typically not for DEXes
3. Deposit funds onto the exchange
4. Get approved for each asset type you want to trade
  - Many exchanges will ask you to go through a quiz or signup process on their website in order to trade futures, options, and other margin products

You will then export your API keys from each exchange to use them with Astra API. More details on how to do this coming soon, once we add support for private exchange endpoints.

<!-- See below for a walkthrough of how to export your API keys from Binance. -->

<b>If you would like to self-host Astra API on your own servers, see [below](#self-hosting).</b>



<aside class="notice">
<b>NOTE:</b> Astra API is still in its alpha release, so you may observe some occasional unexpected behaviour for edge cases. If you see something that looks off, please notify us at <a href="mailto:contact@astra-api.dev">contact@astra-api.dev</a> and we will look into it ASAP.
<br/>
<br/>
Additionally, the API surface is still in flux, and may change as we get closer to a stable release. If you need a stable API for your use-case, please contact us.
</aside>


<!-- ### Features

- Real-time L2 market data via REST and WebSocket
- Multi-asset support, including spot, perpetuals, expiring futures and options markets
- Normalization of data for all endpoints
- Low latency
- (coming soon!) Order placement, cancellation, and smart order routing
- (coming soon!) Fetching user data like fills, orders, positions, balances, and margin info
- (coming soon!) Colocation with exchanges
- (coming soon!) Historical market data
- (coming soon!) Transfers endpoints
- (coming soon!) Support for leveraged tokens, spot margin, and more -->


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
