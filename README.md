# proxy-web3
Web3_proxy is a fast caching and load balancing proxy for web3 (Ethereum or similar) JsonRPC servers.

Under construction! This code is under active development. If you want to run this proxy youself, send me a message on Twitter and I can explain things that aren't documented yet. Most RPC methods are supported, but filters are coming soon. And of course, more tests are always needed.

Signed transactions (eth_sendRawTransaction) are sent in parallel to the configured private RPCs (eden, ethermine, flashbots, etc.).

All other requests are sent to an RPC server on the latest block (llamanodes, alchemy, moralis, rivet, your own node, or one of many other providers). If multiple servers are in sync, they are prioritized by active_requests and request latency. Note that this means that the fastest server is most likely to serve requests and slow servers are unlikely to ever get any requests.

Each server has different limits to configure. The soft_limit is the number of parallel active requests where a server starts to slow down. The hard_limit is where a server starts giving rate limits or other errors.

