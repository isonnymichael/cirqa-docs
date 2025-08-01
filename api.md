# Cirqa API Reference

<div class="cirqa-logo-container" style="text-align: center; margin-bottom: 30px;">
  <img src="assets/images/logo.svg" alt="Cirqa Logo" style="max-width: 200px;">
</div>

<div class="cirqa-highlight">

The Cirqa API provides developers with programmatic access to the Cirqa protocol. This reference documentation covers API endpoints, authentication, rate limits, and example usage. Whether you're building a portfolio tracker, a trading bot, or integrating Cirqa into your DeFi application, this guide will help you get started.

</div>

## API Overview

The Cirqa API is organized around REST principles. It uses standard HTTP response codes, authentication, and verbs. All responses are returned in JSON format.

### Base URL

```
https://api.cirqa.io/v1
```

### Authentication

The Cirqa API uses API keys for authentication. You can obtain an API key by registering on the [Cirqa Developer Portal](https://developers.cirqa.io).

Include your API key in the request header:

```
Authorization: Bearer YOUR_API_KEY
```

### Rate Limits

The API is rate-limited to ensure fair usage and system stability:

- **Free tier**: 60 requests per minute
- **Developer tier**: 300 requests per minute
- **Enterprise tier**: Custom limits

Rate limit information is included in the response headers:

```
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 59
X-RateLimit-Reset: 1620000000
```

## API Endpoints

<div class="cirqa-note">

All endpoints return standardized response formats with appropriate HTTP status codes. Error responses include detailed error messages to help with debugging.

</div>

### Markets

#### Get All Markets

```
GET /markets
```

Returns a list of all available markets in the Cirqa protocol.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `page` | integer | Page number for pagination (default: 1) |
| `limit` | integer | Number of results per page (default: 20, max: 100) |

**Response Example:**

```json
{
  "status": "success",
  "data": {
    "markets": [
      {
        "id": "usdc",
        "name": "USD Coin",
        "symbol": "USDC",
        "decimals": 6,
        "supply_apy": "0.0325",
        "borrow_apy": "0.0412",
        "total_supply": "10000000.00",
        "total_borrow": "7500000.00",
        "utilization_rate": "0.75",
        "collateral_factor": "0.85",
        "reserve_factor": "0.10",
        "price": "1.00"
      },
      // Additional markets...
    ],
    "pagination": {
      "total": 15,
      "page": 1,
      "limit": 20,
      "pages": 1
    }
  }
}
```

#### Get Market Details

```
GET /markets/{market_id}
```

Returns detailed information about a specific market.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `market_id` | string | The unique identifier of the market |

**Response Example:**

```json
{
  "status": "success",
  "data": {
    "id": "usdc",
    "name": "USD Coin",
    "symbol": "USDC",
    "decimals": 6,
    "supply_apy": "0.0325",
    "borrow_apy": "0.0412",
    "total_supply": "10000000.00",
    "total_borrow": "7500000.00",
    "utilization_rate": "0.75",
    "collateral_factor": "0.85",
    "reserve_factor": "0.10",
    "price": "1.00",
    "liquidity": "2500000.00",
    "supply_cap": "50000000.00",
    "borrow_cap": "40000000.00",
    "interest_rate_model": {
      "base_rate": "0.02",
      "multiplier": "0.15",
      "jump_multiplier": "3.00",
      "kink": "0.80"
    }
  }
}
```

### User Data

#### Get User Account

```
GET /users/{address}
```

Returns information about a user's account, including supplied and borrowed assets.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `address` | string | The user's blockchain address |

**Response Example:**

```json
{
  "status": "success",
  "data": {
    "address": "0x1234567890abcdef1234567890abcdef12345678",
    "health_factor": "1.75",
    "total_supplied_usd": "50000.00",
    "total_borrowed_usd": "25000.00",
    "borrowing_power_usd": "17500.00",
    "supplied_assets": [
      {
        "market_id": "usdc",
        "symbol": "USDC",
        "amount": "30000.00",
        "amount_usd": "30000.00",
        "apy": "0.0325",
        "is_collateral": true
      },
      // Additional supplied assets...
    ],
    "borrowed_assets": [
      {
        "market_id": "eth",
        "symbol": "ETH",
        "amount": "10.5",
        "amount_usd": "25000.00",
        "apy": "0.0412"
      },
      // Additional borrowed assets...
    ]
  }
}
```

#### Get User Transactions

```
GET /users/{address}/transactions
```

Returns a list of a user's transactions on the Cirqa protocol.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `address` | string | The user's blockchain address |
| `page` | integer | Page number for pagination (default: 1) |
| `limit` | integer | Number of results per page (default: 20, max: 100) |
| `type` | string | Filter by transaction type (supply, withdraw, borrow, repay, liquidate) |

**Response Example:**

```json
{
  "status": "success",
  "data": {
    "transactions": [
      {
        "id": "0xabcdef1234567890abcdef1234567890abcdef1234567890abcdef1234567890",
        "type": "supply",
        "market_id": "usdc",
        "amount": "10000.00",
        "timestamp": 1620000000,
        "block_number": 12345678
      },
      // Additional transactions...
    ],
    "pagination": {
      "total": 45,
      "page": 1,
      "limit": 20,
      "pages": 3
    }
  }
}
```

### Protocol Data

#### Get Protocol Stats

```
GET /stats
```

Returns overall statistics about the Cirqa protocol.

**Parameters:**

None

**Response Example:**

```json
{
  "status": "success",
  "data": {
    "total_supply_usd": "100000000.00",
    "total_borrow_usd": "75000000.00",
    "total_unique_users": 5000,
    "total_markets": 15,
    "total_transactions": 150000,
    "daily_supply_volume_usd": "5000000.00",
    "daily_borrow_volume_usd": "3000000.00"
  }
}
```

#### Get Historical APY

```
GET /markets/{market_id}/apy/history
```

Returns historical APY data for a specific market.

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `market_id` | string | The unique identifier of the market |
| `period` | string | Time period (day, week, month, year) (default: month) |
| `resolution` | string | Data resolution (hour, day, week) (default: day) |

**Response Example:**

```json
{
  "status": "success",
  "data": {
    "market_id": "usdc",
    "period": "month",
    "resolution": "day",
    "supply_apy": [
      {
        "timestamp": 1620000000,
        "value": "0.0325"
      },
      // Additional data points...
    ],
    "borrow_apy": [
      {
        "timestamp": 1620000000,
        "value": "0.0412"
      },
      // Additional data points...
    ]
  }
}
```

## Websocket API

For real-time updates, Cirqa provides a WebSocket API:

```
wss://api.cirqa.io/v1/ws
```

### Authentication

Authenticate with your API key when connecting:

```json
{
  "action": "authenticate",
  "api_key": "YOUR_API_KEY"
}
```

### Subscribing to Updates

Subscribe to specific events:

```json
{
  "action": "subscribe",
  "channels": ["markets", "user:0x1234567890abcdef1234567890abcdef12345678"]
}
```

### Event Types

- **market_update**: Updates to market data (rates, liquidity, etc.)
- **user_transaction**: New user transactions
- **user_position_update**: Changes to a user's positions
- **protocol_update**: Overall protocol statistics updates

## SDK Integration

For easier integration, Cirqa provides official SDKs in multiple languages:

### JavaScript/TypeScript

```bash
npm install @cirqa/sdk
```

```javascript
import { CirqaClient } from '@cirqa/sdk';

const client = new CirqaClient('YOUR_API_KEY');

// Get all markets
async function getMarkets() {
  const markets = await client.markets.getAll();
  console.log(markets);
}

// Get user account
async function getUserAccount(address) {
  const account = await client.users.getAccount(address);
  console.log(account);
}
```

### Python

```bash
pip install cirqa-sdk
```

```python
from cirqa_sdk import CirqaClient

client = CirqaClient('YOUR_API_KEY')

# Get all markets
markets = client.markets.get_all()
print(markets)

# Get user account
account = client.users.get_account('0x1234567890abcdef1234567890abcdef12345678')
print(account)
```

## Error Handling

The API uses standard HTTP status codes to indicate the success or failure of requests:

- **200 OK**: The request was successful
- **400 Bad Request**: The request was invalid
- **401 Unauthorized**: Authentication failed
- **403 Forbidden**: The API key doesn't have permission
- **404 Not Found**: The requested resource doesn't exist
- **429 Too Many Requests**: Rate limit exceeded
- **500 Internal Server Error**: Server error

Error responses include detailed information:

```json
{
  "status": "error",
  "error": {
    "code": "invalid_parameter",
    "message": "Invalid market_id parameter",
    "details": {
      "parameter": "market_id"
    }
  }
}
```

## Best Practices

- Cache responses when appropriate to reduce API calls
- Implement exponential backoff for rate limit errors
- Use the WebSocket API for real-time data needs
- Monitor your API usage through the developer dashboard

<div class="cirqa-warning">

Never expose your API key in client-side code. Always make API calls from your server to protect your credentials.

</div>

## Support

If you encounter any issues or have questions about the API, please contact our developer support:

- **Developer Discord**: [Join our Discord](https://discord.gg/cirqa)
- **Email Support**: [developers@cirqa.io](mailto:developers@cirqa.io)
- **Documentation Issues**: [GitHub Repository](https://github.com/cirqa/docs)

<div class="cta-container" style="display: flex; justify-content: center; gap: 20px; margin-top: 40px;">
  <a href="https://developers.cirqa.io" class="cta-button" style="background-color: #6E76E5; color: white; padding: 12px 24px; border-radius: 4px; text-decoration: none; font-weight: bold;">Developer Portal</a>
  <a href="https://github.com/cirqa/sdk" class="cta-button" style="background-color: #6E76E5; color: white; padding: 12px 24px; border-radius: 4px; text-decoration: none; font-weight: bold;">SDK Repository</a>
</div>