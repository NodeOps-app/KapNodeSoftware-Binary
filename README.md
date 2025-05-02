# KapNode Software

This is a node software implementation for the Kap protocol, designed to monitor and report epochs on the blockchain.

## Prerequisites

- Docker and Docker Compose installed on your system
- Environment variables configured (see Environment Variables section)

## Environment Variables

Create a `.env` file in the project root with the following variables:

```bash
# Required
OPERATOR_PRIVATE_KEY=0x456...  # Your node's private key (address will be derived from this)
RPC_URL=https://your-rpc-endpoint  # Ethereum RPC endpoint
PROTOCOL_ADDRESS=0x2dd0F2DfFeDB4B3CA898046C4f24d99EDD2C8416  # Protocol contract address
```

You can copy the example environment file:
```bash
cp env.example .env
```

Then edit the `.env` file to add your specific values.

## Running with Docker

### Using Docker Compose (Recommended)

1. Build and start the container:
```bash
docker-compose up -d
```

2. View logs:
```bash
docker-compose logs -f
```

### Using Docker Directly

1. Build the Docker image:
```bash
docker build -t kapnode .
```

2. Run the container:
```bash
docker run -d \
  --name kapnode \
  --env-file .env \
  kapnode
```

3. View logs:
```bash
docker logs -f kapnode
```

## Monitoring

The node will automatically:
- Connect to the specified RPC endpoint
- Monitor for new epochs
- Report epochs to the protocol contract
- Handle transaction receipts and retries

## Troubleshooting

If you encounter issues:
1. Check the logs using `docker-compose logs` or `docker logs kapnode`
2. Verify all environment variables are correctly set in your `.env` file
3. Ensure the RPC endpoint is accessible
4. Confirm the node has sufficient funds for gas fees

## Features

- Automatic epoch monitoring and reporting
- Transaction receipt management
- Retry mechanism for failed transactions
- Configurable polling intervals
- Robust error handling and logging

## Project Structure

- `main.go` - Application entry point
- `node/` - Node implementation
- `env/` - Environment configuration
- `utils/` - Utility functions
- `contracts/` - Smart contract bindings
- `logger/` - Logging implementation

## License

[Add your license information here] 
