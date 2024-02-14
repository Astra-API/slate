# WebSocket API

<!-- Default `content-Type`: `application/json` -->

<!-- The WebSocket endpoint is available without authentication. Once the socket is connected, you can subscribe to a channel by sending a `Subscription` message, detailed in Schema. -->

You can use the WebSocket API to stream real-time market data.

**Endpoint: `wss://prod.astra-api.dev/ws`**

### Authentication

Remember to specify an authentication header with your API key, as described [above](#3-send-your-first-request). Otherwise, your requests will fail.
