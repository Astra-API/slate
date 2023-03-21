

# Astra Websockets API v1.0.0

> Scroll down for code samples, example headers and payloads. Select a language for code samples from the tabs above or the mobile navigation menu.

This is Astra's unified crypto trading API.

Default `content-Type`: `application/json`

Servers:

* `public` - Protocol: `wss` 
    >Public server available without authorization.
Once the socket is open you can subscribe to a public channel by sending a subscribe request message.

    * <a href="wss://api.greyduckcapital.xyz/ws">wss://api.greyduckcapital.xyz/ws</a>

# Default

## /

<h3 id="root-publish">publish</h3>

`sendMessage`:

<h4 id="root-publish-sendMessage">sendMessage</h4>

> Code Samples

```javascript--nodejs
const hermes = require('hermesjs');
const app = hermes();

app.from.client.send({
  topic: '/',
  payload: undefined
});

```

```javascript
//Coming soon...

```

```ruby
# Coming soon...

```

```python
//Coming soon...

```

```java
/* asyncapi-java-tools */
try (JmsServer client = builder.build()) {

  client..()
    .publish(undefined)
    .toCompletableFuture()
    .get();
}

```

```go
//Coming soon...

```

<aside class="success">
This operation does not require authentication
</aside>

<h3 id="root-subscribe">subscribe</h3>

`processMessage`:

<h4 id="root-subscribe-processMessage">processMessage</h4>

> Code Samples

```javascript--nodejs
const hermes = require('hermesjs');
const app = hermes();

app.from.client.send({
  topic: '/',
  payload: undefined
});

```

```javascript
//Coming soon...

```

```ruby
# Coming soon...

```

```python
//Coming soon...

```

```java
/* asyncapi-java-tools */
try (JmsServer client = builder.build()) {

  client..()
    .publish(undefined)
    .toCompletableFuture()
    .get();
}

```

```go
//Coming soon...

```

<aside class="success">
This operation does not require authentication
</aside>

