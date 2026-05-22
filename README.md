# GSY Energy Web Proxy Library

GSY proxy library for interconnecting with the Energy Web infrastructure (Energy Web Client Gateway and Energy Web Digital Spine). It provides a Python client that handles authentication, message exchange, and order submission against the Energy Web Client Gateway. That way, the user of the library can interact with Energy Web services without dealing with the underlying HTTP and Websocket connections. The library also includes a price updater that periodically refreshes the prices of posted bids and offers over the lifetime of a market slot, so that orders remain competitive as the market evolves without requiring the caller to manage the order updates.

## Installation

Install from source:

```bash
pip install git+https://github.com/gridsingularity/gsy-ew-proxy-library.git
```

Or, for local development:

```bash
git clone https://github.com/gridsingularity/gsy-ew-proxy-library.git
cd gsy-ew-proxy-library
pip install -e ".[test]"
```

## Usage

Instantiate the client with the URL of the Energy Web endpoint and your credentials, then call the appropriate methods to submit bids and offers:

```python
from gsy_ew_proxy import GSYEnergyWebProxyClient

client = GSYEnergyWebProxyClient(
    endpoint="https://digital-spine.example.org",
    api_key="<your-api-key>",
)

# Submit a bid
client.submit_bid(
    market_id="<market-id>",
    energy_kWh=1.5,
    price=0.20,
)

# Submit an offer
client.submit_offer(
    market_id="<market-id>",
    energy_kWh=2.0,
    price=0.25,
)
```

Refer to the docstrings of `GSYEnergyWebProxyClient` for the full set of supported operations.

## Running tests

```bash
pytest
```
