# XRPL Overnight

![Solidity](https://img.shields.io/badge/Solidity-0.8-363636)
![Next.js](https://img.shields.io/badge/Next.js-Frontend-000000)
![NestJS](https://img.shields.io/badge/NestJS-Backend-E0234E)
![Chainlink](https://img.shields.io/badge/Chainlink-Functions%20%2B%20Automation-375BD2)

A decentralized platform for **collateralized overnight credit operations** using tokenized Brazilian National Treasury bonds (NTBt) and a simulated CBDC (Drex). Built for the interbank reserve market.

## Overview

In most countries, central banks require minimum reserves from financial institutions. When banks lack sufficient liquidity, they resort to interbank credit operations -- a market that moves **trillions of dollars weekly** worldwide. XRPL Overnight brings this market on-chain by tokenizing Brazilian government bonds as collateral and automating interest accrual through Chainlink oracles.

### The Problem

- **High transaction costs** with multiple intermediaries in traditional interbank operations
- **Lack of liquidity** due to communication inefficiencies between institutions
- **Limited transparency** making regulatory auditing difficult
- **Counterparty risk** without automated enforcement of obligations

### The Solution

- **Smart contracts** for tokenizing treasury bonds (TFPt) and the Brazilian Real (RealTokenizado), simulating Drex (Brazilian CBDC)
- **Chainlink Functions** to fetch real-time Selic interest rate data from the Central Bank of Brazil API
- **Chainlink Automation** to update NTBt token prices daily based on the Selic rate
- **Collateralized credit** -- banks use tokenized government bonds to secure overnight loans on-chain

## Architecture

```
packages/
  hardhat/        — Solidity smart contracts (Scaffold-ETH 2)
    contracts/
      Credpix.sol              — Main credit operations contract
      TFPt.sol                 — Tokenized Treasury Bond (Titulo Publico Federal tokenizado)
      RealTokenizado.sol       — Simulated Drex (Brazilian CBDC)
      SelicOracle.sol          — Chainlink Functions oracle for Selic rate
      ComputeProfitRefactored.sol — Interest calculation engine
  nextjs/         — Frontend application (Next.js + Tailwind CSS)
backend/
  bacen-api/      — Central Bank API service (NestJS + MongoDB)
```

## Smart Contracts

| Contract | Description |
|---|---|
| `Credpix.sol` | Core contract for collateralized credit operations |
| `TFPt.sol` | ERC20 tokenized Brazilian treasury bond |
| `RealTokenizado.sol` | Simulated Brazilian CBDC (Drex) |
| `SelicOracle.sol` | Chainlink Functions client fetching Selic rate from BACEN API |
| `ComputeProfitRefactored.sol` | On-chain interest/profit calculation |

## Tech Stack

- **Smart Contracts:** Solidity, Hardhat, Scaffold-ETH 2
- **Frontend:** Next.js, Tailwind CSS, TypeScript
- **Backend:** NestJS, MongoDB, Mongoose
- **Oracles:** Chainlink Functions + Chainlink Automation
- **Auth:** ParticleAuth (Web2-style crypto onboarding)

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 LTS
- [Yarn](https://yarnpkg.com/) v1 or v3+
- [Git](https://git-scm.com/)

### Installation

```bash
yarn install
```

### Run Frontend

```bash
yarn start
```

Visit `http://localhost:3000`.

### Run Backend API

```bash
cd backend/bacen-api
yarn install
yarn start:dev
```

## Documentation

- [Smart Contracts Documentation](./docs/smartContracts.md)

## Presentation

- [YouTube Demo](https://www.youtube.com/watch?v=4G25kevHUio)

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE) for details.
