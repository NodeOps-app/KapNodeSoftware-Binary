# KapNode Software

This is a node software implementation for the Kap protocol, designed to monitor and report epochs on the blockchain.

## Prerequisites

- Docker installed on your system

## Environment Variables

The following environment variables are required to run the node. You can pass them directly to the Docker run command:

```bash
# Required
OPERATOR_PRIVATE_KEY=0x456...  # Your node's private key (address will be derived from this)
RPC_URL=https://your-rpc-endpoint  # Ethereum RPC endpoint
PROTOCOL_ADDRESS=0x2dd0F2DfFeDB4B3CA898046C4f24d99EDD2C8416  # Protocol contract address
```

## Running with Docker

### Using Docker Directly

Run the container with environment variables:

```bash
docker run -d \
  --name kapnode \
  -e OPERATOR_PRIVATE_KEY=0x456... \
  -e RPC_URL=https://your-rpc-endpoint \
  -e PROTOCOL_ADDRESS=0x2dd0F2DfFeDB4B3CA898046C4f24d99EDD2C8416 \
  reg.nodeops.xyz/public/kap:1.0.0
```

### Using Docker Compose

Create a `docker-compose.yml` file:

```yaml
version: '3.8'

services:
  node-software:
    image: reg.nodeops.xyz/public/kap:1.0.0
    environment:
      - OPERATOR_PRIVATE_KEY=0x456...
      - RPC_URL=https://your-rpc-endpoint
      - PROTOCOL_ADDRESS=0x2dd0F2DfFeDB4B3CA898046C4f24d99EDD2C8416
    restart: unless-stopped
```

Then run:
```bash
docker-compose up -d
```

## Monitoring

The node will automatically:
- Connect to the specified RPC endpoint
- Monitor for new epochs
- Report epochs to the protocol contract
- Handle transaction receipts and retries

## Troubleshooting

If you encounter issues:
1. Check the logs using `docker logs kapnode` or `docker-compose logs`
2. Verify all environment variables are correctly set
3. Ensure the RPC endpoint is accessible
4. Confirm the node has sufficient funds for gas fees

## Features

- Automatic epoch monitoring and reporting
- Transaction receipt management
- Retry mechanism for failed transactions
- Configurable polling intervals
- Robust error handling and logging
