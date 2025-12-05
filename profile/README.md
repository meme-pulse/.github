<p align="center">
  <img src="https://raw.githubusercontent.com/meme-pulse/.github/refs/heads/main/meme-pulse.png" alt="Meme Pulse Logo" width="120" />
</p>

<h1 align="center">Meme Pulse</h1>

<p align="center">
  <strong>Social Virality Rewards + AI-Powered Liquidity</strong>
</p>

<p align="center">
  A full-stack DEX that turns social media virality into on-chain rewards — with AI-powered liquidity management.
</p>

<p align="center">
  <a href="#-core-innovations">Core Innovations</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-repositories">Repositories</a> •
  <a href="#-deployed-contracts">Contracts</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Network-Memecore_Testnet-purple" alt="Network" />
  <img src="https://img.shields.io/badge/Chain_ID-43522-blue" alt="Chain ID" />
  <img src="https://img.shields.io/badge/AMM-Liquidity_Book-green" alt="AMM" />
  <img src="https://img.shields.io/badge/AI-Claude_Sonnet-orange" alt="AI" />
</p>

---

## 🔥 Core Innovations

### 1️⃣ Viral Score Rewards

We calculate **"Viral Scores"** by aggregating social engagement data from Memex API:

| Metric       | Weight |
| ------------ | ------ |
| Posts        | ×100   |
| Views        | ×1     |
| Likes        | ×20    |
| Reposts      | ×50    |
| Replies      | ×30    |
| Unique Users | ×200   |

Scores are processed with **time-decay algorithms** (24h half-life) and submitted on-chain via cryptographically signed epoch updates.

**Top 3 viral tokens receive automatic protocol fee reductions:**

| Rank    | Protocol Fee | Boost           |
| ------- | ------------ | --------------- |
| 🥇 1st  | 10%          | **5x Boost**    |
| 🥈 2nd  | 20%          | **2.5x Boost**  |
| 🥉 3rd  | 40%          | **1.25x Boost** |
| Default | 50%          | -               |

### 2️⃣ AI-Powered DLMM Strategy

Liquidity Book (DLMM) is notoriously complex — choosing the right bin step, price range, and distribution shape can overwhelm even experienced LPs.

Meme Pulse integrates **Claude AI** to analyze:

- 📊 Real-time market volatility & volume trends
- 📈 Historical price data & fee APRs across pools
- 💧 Liquidity distribution across bins
- 🎯 Volume/TVL ratios and market conditions

Based on your risk preference (**Aggressive / Defensive / Auto**), our AI recommends:

| Output              | Description                                |
| ------------------- | ------------------------------------------ |
| **Optimal Pool**    | Best bin step (fee tier) to use            |
| **Bin Range**       | minBinId → maxBinId                        |
| **Distribution**    | SPOT / CURVE / BID_ASK                     |
| **Risk Assessment** | Expected APR, IL risk, rebalance frequency |

**Turn a 10-step manual process into a one-click experience.**

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              MEME PULSE                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────┐         ┌─────────────────┐         ┌──────────────┐ │
│   │   Memex API     │         │  Viral Score    │         │   On-Chain   │ │
│   │  (Social Data)  │────────▶│    Server       │────────▶│   Reporter   │ │
│   └─────────────────┘         └─────────────────┘         └──────────────┘ │
│                                      │                           │         │
│                                      │ Score + Signature         │         │
│                                      ▼                           ▼         │
│   ┌─────────────────┐         ┌─────────────────┐         ┌──────────────┐ │
│   │   Claude AI     │         │    Envio        │         │  LB Factory  │ │
│   │  (Strategy)     │◀───────▶│   Indexer       │◀───────▶│  + LB Pairs  │ │
│   └─────────────────┘         └─────────────────┘         └──────────────┘ │
│          │                           │                                     │
│          │ AI Recommendation         │ GraphQL                             │
│          ▼                           ▼                                     │
│   ┌─────────────────────────────────────────────────────────────────────┐  │
│   │                         Frontend (React)                            │  │
│   │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌───────┐  │  │
│   │  │   Swap   │  │   Pool   │  │ AI Pool  │  │Portfolio │  │Leader │  │  │
│   │  │          │  │  Detail  │  │  Detail  │  │          │  │ board │  │  │
│   │  └──────────┘  └──────────┘  └──────────┘  └──────────┘  └───────┘  │  │
│   └─────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### The Flywheel

```
Viral Token → Lower Fees → More Trading → More Liquidity
      ↑                                          │
      │                                          ▼
More Attention ← Better Yields ← AI Optimizes LP Positions
```

---

## 🛠 Tech Stack

| Layer               | Technology                | Description                                     |
| ------------------- | ------------------------- | ----------------------------------------------- |
| **Smart Contracts** | Solidity + Foundry        | Liquidity Book AMM, ViralScoreReporter          |
| **Indexer**         | Envio                     | Real-time on-chain event indexing               |
| **Backend**         | Bun + Hono + PostgreSQL   | Viral score calculation, signing, Merkle proofs |
| **AI**              | Claude API (Anthropic)    | DLMM strategy generation                        |
| **Frontend**        | React + TypeScript + Vite | CEX-style trading UI                            |
| **Styling**         | Tailwind CSS              | Responsive, modern design                       |
| **Blockchain**      | Memecore Testnet (43522)  | EVM-compatible L2                               |

---

## 📁 Repositories

| Repository                                                                   | Description                                             | Status      |
| ---------------------------------------------------------------------------- | ------------------------------------------------------- | ----------- |
| [`meme-pulse-contracts`](https://github.com/meme-pulse/meme-pulse-contracts) | Liquidity Book AMM + ViralScoreReporter smart contracts | ✅ Deployed |
| [`meme-pulse-ui`](https://github.com/meme-pulse/meme-pulse-ui)               | React frontend with AI-powered LP interface             | ✅ Live     |
| [`meme-pulse-envio`](https://github.com/meme-pulse/meme-pulse-envio)         | Envio indexer for real-time on-chain data               | ✅ Running  |
| [`viral-score-server`](https://github.com/meme-pulse/viral-score-server)     | Backend for viral score calculation & epoch submission  | ✅ Running  |

---

## 📜 Deployed Contracts

### Memecore Testnet (Chain ID: 43522)

| Contract                    | Address                                                                                                                                      |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **LBFactory**               | [`0x1B279B36995A5AfBB75d82187F0025Ffef4572ED`](https://insectarium.blockscout.memecore.com/address/0x1B279B36995A5AfBB75d82187F0025Ffef4572ED) |
| **LBRouter**                | [`0x467777Edb64b83E3b883EB7Ec8A2B291888eD67b`](https://insectarium.blockscout.memecore.com/address/0x467777Edb64b83E3b883EB7Ec8A2B291888eD67b) |
| **LBQuoter**                | [`0x070C29CdF290c3681A25e3258cC1cdAa0a97300B`](https://insectarium.blockscout.memecore.com/address/0x070C29CdF290c3681A25e3258cC1cdAa0a97300B) |
| **LBPair (Implementation)** | [`0xFaBb4c3EFb914fEbae14060216273064789627a8`](https://insectarium.blockscout.memecore.com/address/0xFaBb4c3EFb914fEbae14060216273064789627a8) |
| **ViralScoreReporter**      | [`0x639323a363Da20E755c3D38C14d59FbCC67446bC`](https://insectarium.blockscout.memecore.com/address/0x639323a363Da20E755c3D38C14d59FbCC67446bC) |
| **LiquidityHelper**         | [`0xB4c4C4B4833E74FC60D74482Ec729C60C1E65Dc6`](https://insectarium.blockscout.memecore.com/address/0xB4c4C4B4833E74FC60D74482Ec729C60C1E65Dc6) |
| **Multicall3**              | [`0x709Bf66Fb11942dA03a1F7bf59bFA99293F68db9`](https://insectarium.blockscout.memecore.com/address/0x709Bf66Fb11942dA03a1F7bf59bFA99293F68db9) |
| **Wrapped Native (WM)**     | [`0x653e645e3d81a72e71328Bc01A04002945E3ef7A`](https://insectarium.blockscout.memecore.com/address/0x653e645e3d81a72e71328Bc01A04002945E3ef7A) |

> 📍 RPC URL: `https://rpc.insectarium.memecore.net`  
> 🔍 Explorer: `https://explorer.insectarium.memecore.net`

---

## 🎮 Features

### For Traders

- ⚡ **Fast Swaps** with Liquidity Book AMM
- 💰 **Lower Fees** on viral meme tokens
- 📊 **Real-time** price charts and analytics
- 🏆 **Leaderboard** of trending viral tokens

### For Liquidity Providers

- 🤖 **AI Strategy** recommendations
- 📈 **Concentrated Liquidity** with precise bin placement
- 🎯 **Risk Profiles**: Aggressive, Defensive, Auto
- 💎 **Fee Earnings** visualization

### For Meme Token Communities

- 🔥 **Viral Rewards**: Hype your token, earn fee discounts
- 📱 **Social Integration** with Memex

---

<p align="center">
  <strong>Go Viral. Trade Cheaper. Win Harder. 🚀</strong>
</p>

<p align="center">
  Built with ❤️ for the Memecore Hackathon
</p>
