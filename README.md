<p align="center">
  <img width="90%" alt="token-management" src="assets/logo.png">
</p>
<p align="center">
  Manage, Trade, and Exchange User-Created Tokens Effortlessly On-Chain
</p>
<p align="center">
  <a href="https://github.com/ava-labs/hypersdk/actions/workflows/static-analysis.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/static-analysis.yml/badge.svg" /></a>
  <a href="https://github.com/ava-labs/hypersdk/actions/workflows/unit-tests.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/unit-tests.yml/badge.svg" /></a>
  <a href="https://github.com/ava-labs/hypersdk/actions/workflows/sync-tests.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/sync-tests.yml/badge.svg" /></a>
  <a href="https://github.com/ava-labs/hypersdk/actions/workflows/load-tests.yml"><img src="https://github.com/ava-labs/hypersdk/actions/workflows/load-tests.yml/badge.svg" /></a>
</p>

---

The [`token-management`](./examples/token-management) module demonstrates how the `hypersdk` can be integrated to create a seamless token minting and trading platform. With the `token-management` application, users can generate their own tokens, mint additional units, adjust metadata, and burn tokens. It also features an on-chain marketplace, where users can create and fulfill trade orders directly.

## Overview

This module serves as a complete example of how blockchain-based token trading and minting functions can be achieved using the `hypersdk`. The trading mechanism is optimized to process transactions with minimal latency, supported by an in-memory order book that simplifies interactions with trade data in real-time. The concise logic required to handle trade orders ensures efficiency, making this a useful resource for developers interested in decentralized exchanges.

## Software Status
`token-management` is currently in **ALPHA** and should not be used in production environments. The framework is actively evolving, and significant changes are expected as the platform is optimized and security improvements are applied.

## Key Features

### Token Minting & Management
Create, mint, and transfer tokens in a few simple steps. Asset creators have full control, including the ability to update token details, mint additional units, and manage ownership. The platform’s underlying storage design is highly efficient, supporting parallel processing of transactions for optimal performance.

### Decentralized Trading
Fully on-chain trading capabilities allow users to create and manage orders, with support for partial fills. Each token trade is recorded securely on-chain, making the process transparent and secure. The in-memory order book helps manage orders without the need for external databases, simplifying the process for clients.

### Order Management
Orders are a core feature of the system, and the platform efficiently manages trade operations with minimal storage requirements. This streamlined design enables high scalability, with provisions for parallelizing transaction execution across multiple orders.

#### In-Memory Order Book
To further streamline the user experience, the system maintains an in-memory order book that synchronizes with the on-chain data. This approach makes it easier to query trade offers and ensures real-time updates for users participating in token exchanges.

#### Security and Anti-Front Running
The platform is designed to prevent price manipulation by restricting fill operations to specific orders. This reduces the chances of front-running attacks, ensuring fair execution of all transactions.

#### Partial Fills & Refunds
Traders can fill orders partially or over multiple transactions, and any excess tokens provided are refunded automatically. This is critical in preventing loss of tokens during concurrent trades.

### Cross-Chain Transfers with Avalanche Warp Messaging
The `token-management` application supports cross-chain transfers through Avalanche Warp Messaging, enabling secure token transfers between different instances of the application on separate subnets. This feature is designed to minimize the risk of malicious activity by only allowing native assets to be exported and imported between trusted environments.

## Demonstration
To test the system, you can launch a `token-management` subnet and explore its features using the included CLI. To get started, follow the commands below:

```bash
./scripts/run.sh
```

Once the system is up and running, use the CLI to create your own token, mint assets, and interact with the marketplace. Build the CLI tool as follows:

```bash
./scripts/build.sh
```

Next, import your keys and chains:

```bash
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```

This allows you to interact with the subnet and experiment with token minting and trading.

### Step 1: Create a Token
Run the following command to create a new token:

```bash
./build/token-cli action create-asset
```

### Step 2: Mint Tokens
After creating the token, mint additional units by using:

```bash
./build/token-cli action mint-asset
```

### Step 3: Trade Tokens
You can now trade the tokens you've created and minted by creating or filling orders on the decentralized marketplace.

## Conclusion
The `token-management` module showcases a flexible, blockchain-based solution for token minting and trading, with the added benefit of cross-chain communication and secure on-chain order handling. Its compact and efficient design makes it an excellent starting point for developers interested in blockchain applications.
