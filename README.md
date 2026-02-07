# Fund Me — USD-Denominated ETH Funding Contract

A minimal, production-ready smart contract that allows users to fund a contract owner with ETH donations denominated in USD.  
The contract enforces a minimum USD value per donation using Chainlink price feeds and is built with Foundry following modern smart contract development best practices.

---

## About

This project implements a decentralized funding mechanism where:
- Users can donate ETH
- Donations are validated against a minimum USD threshold
- ETH/USD pricing is fetched via Chainlink price feeds
- Donors are tracked on-chain for potential future rewards or logic extensions
- Only the contract owner can withdraw accumulated funds

The contract is designed to be **simple, secure, and extensible**, making it suitable as a foundation for crowdfunding, grants, or on-chain donation systems.

---

## Features

- ETH donations denominated in USD
- Chainlink Price Feed integration
- Minimum USD contribution enforcement
- Secure owner-only withdrawals
- Donor tracking
- Modular & testable architecture
- Automated scripts and Makefile workflow
- Compatible with EVM & zkSync environments

---

## Tech Stack

- **Solidity** `^0.8.19`
- **Foundry** (Forge, Cast, Anvil)
- **Chainlink Price Feeds**
- **foundry-devops** (zkSync & environment-aware testing)
- **Makefile** for workflow automation

---

## Requirements

- [Foundry](https://book.getfoundry.sh/)
- Git
- Node.js (optional, for tooling/extensions)

Install Foundry:
```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

---

## Quick Start

Clone the repository:
```bash
git clone git@github.com:gandalf-blockchain/foundry-fund-me.git
cd foundry-fund-me
```

Install dependencies:
```bash
forge install
```

Build contracts:
```bash
forge build
```

Run tests:
```bash
forge test
```

Verbose testing:
```bash
forge test -vvv
```

---

## Environment Variables

Create a `.env` file (never commit this):
```
PRIVATE_KEY=your_private_key
RPC_URL=your_rpc_url
ETHERSCAN_API_KEY=your_api_key
```

`.env` is ignored via `.gitignore`.

---

## Deployment

Deploy locally:
```bash
make deploy
```

Deploy to a live network:
```bash
make deploy ARGS="--network sepolia"
```

Deployment scripts are automated using Makefile to reduce human error.

---

## Testing Across Environments

This project supports environment-aware testing, including zkSync.

Examples:
```bash
forge test
forge test --zksync
```

Conditional test helpers:
- `skipZkSync`
- `onlyZkSync`
- `onlyVanillaFoundry`

These ensure assumptions valid on EVM are not incorrectly applied to zkSync.

---

## Security Considerations

- Uses Solidity `^0.8.x` for built-in overflow checks
- Owner-only withdrawals enforced
- External price feed reads are isolated
- Environment-specific behavior explicitly tested
- `.env` and sensitive files excluded from version control

---
