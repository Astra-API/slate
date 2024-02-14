# Self hosting

### What is it?

Astra API is available in two modes: managed and self-hosted.

With managed hosting, we run all the infrastructure behind the scenes to give you fast, robust market access.

With self-hosting, we provide you with a lightweight proxy agent that you run on your own servers. Your business software can then interact directly with each exchange via our proxy.

To get started, create an account with us and create and Astra API key. If you are using our API only to access public market data, then this is all you need.

If you are placing/cancelling orders or fetching your private user data, you will need to bring your own exchange accounts and API keys. Once you have set up accounts on an exchange, you can export your API keys and use that with the Astra API.

### How to Self-Host?

For self-hosting, follow these steps:

1. **Install Docker:**
   Ensure Docker is installed on your server. If not, visit [Docker's official website](https://docs.docker.com/get-docker/) for instructions.

```bash
docker run -d --platform linux/amd64 -p 8080:8080 -p 9090:9090 --env ASTRA_API_KEY=$ASTRA_API_KEY --name astra-gateway -t docker.io/astraimages/gateway:v0.0.1-alpha
```

2. **Obtain your API key**
    Refer [above](#getting-started) for how to create an account and an Astra API key. Your API key is crucial for authentication and ensuring secure communication with the Astra API.

2. **Run the astra-gateway proxy**
   Execute the following command in a shell on your server. Replace `$ASTRA_API_KEY` in the command with your actual Astra API key.


### Data Privacy

For users of managed hosting, your data is encrypted in transit via HTTPS, and we never read any credentials that you transmit via our API. We have a strict no-logging policy for sensitive user data, which means that any credentials get destroyed as soon as they are used, and are never written to disk.

For users of self-hosting, you fully own your data. Your data, keys, and other credentials never leave your servers. Astra's proxy agent is self-contained, and only communicates with our servers to authenticate you and make sure you have a valid Astra API key.
