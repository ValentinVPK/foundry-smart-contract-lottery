# Smart Contract Lottery

This project is part of the Cyfrin Updraft Foundry Fundamentals course, demonstrating the implementation of a decentralized lottery system using Solidity and Foundry.

## Overview

A decentralized lottery system where participants can enter by paying an entrance fee. The lottery is managed by a smart contract that randomly selects a winner and transfers the accumulated prize pool to them.

## Technologies Used

- **Foundry**: A blazing fast, portable, and modular toolkit for Ethereum application development
  - Forge: Testing framework
  - Cast: Command-line tool for interacting with EVM smart contracts
  - Anvil: Local Ethereum node
- **Solidity**: Smart contract programming language
- **Chainlink**: For price feeds and VRF (Verifiable Random Function)
- **Solmate**: For efficient and secure smart contract implementations

## Project Structure

```
├── src/                    # Source files containing smart contracts
├── test/                   # Test files for smart contracts
├── script/                 # Deployment and interaction scripts
├── lib/                    # External dependencies
│   ├── chainlink-brownie-contracts/  # Chainlink contracts
│   └── solmate/           # Solmate contracts
├── documentation/         # Project documentation
├── broadcast/            # Deployment transaction data
├── cache/               # Foundry cache
├── out/                 # Compiled contracts
├── .github/             # GitHub configuration
├── foundry.toml         # Foundry configuration
└── Makefile            # Build automation
```

## Getting Started

### Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation)
- Git

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd foundry-smart-contract-lottery
```

2. Install dependencies:

```bash
forge install
```

### Building

```bash
forge build
```

### Testing

```bash
forge test
```

### Deployment

1. Set up your environment variables in `.env`:

```
PRIVATE_KEY=your_private_key
RPC_URL=your_rpc_url
```

2. Deploy the contract:

```bash
forge script script/DeployLottery.s.sol:DeployLotteryScript --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast
```

## Features

- Decentralized lottery system
- Chainlink VRF for secure random number generation
- Price feed integration for ETH/USD conversion
- Automated winner selection
- Prize pool management

## Testing

The project includes comprehensive tests covering:

- Contract deployment
- Lottery entry functionality
- Winner selection
- Prize distribution
- Edge cases and error conditions

Run the tests with:

```bash
forge test
```

## License

This project is part of the Cyfrin Updraft Foundry Fundamentals course.
