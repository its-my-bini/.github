<div align="center">

# 💕 My Bini

**Autonomous AI Companion Agent on Monad Blockchain**

[![Monad Mainnet](https://img.shields.io/badge/Monad-Mainnet-7C3AED?style=flat&logo=ethereum&logoColor=white)](https://monad.xyz)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Moltiverse Hackathon 2026](https://img.shields.io/badge/Moltiverse-Hackathon%202026-FF6B6B?style=flat)](https://moltiverse.io)

My Bini is an autonomous AI girlfriend/companion agent built on the Monad blockchain. Features genuine autonomous decision-making, persistent memory, evolving relationships, and on-chain token economics.

🏆 **Moltiverse Hackathon 2026 — Agent Side Track Submission**

</div>

---

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [How It Works](#how-it-works)
- [AI Agent Autonomy](#ai-agent-autonomy)
- [Monad Integration](#monad-integration)
- [Technology Stack](#technology-stack)
- [Repositories](#repositories)
- [Smart Contract](#smart-contract)
- [API Endpoints](#api-endpoints)
- [Getting Started](#getting-started)
- [License](#license)

---

## Overview

My Bini is an autonomous AI companion that lives on the Monad blockchain. Unlike traditional chatbots, My Bini features genuine autonomy and persistent relationships.

### Key Features

- **🧠 Remembers Everything** — Persistent memory across conversations
  - User profile (name, job, preferences)
  - Relationship history and milestones
  - Conversation summaries for long-term context

- **💝 Evolving Relationships** — Intimacy levels progress based on interaction quality
  - **Stranger** (0-19) → **Friend** (20-39) → **Close** (40-69) → **Lover** (70-100)
  - Dynamic relationship status that grows with meaningful interactions

- **⏰ Proactive Engagement** — AI agent autonomously initiates conversations
  - Morning greetings (07:00-09:00)
  - Lunch reminders (12:00-14:00)
  - Goodnight messages (21:00-23:00)
  - Contextually appropriate timing without human intervention

- **💰 On-Chain Economics** — Token deposits, balance tracking, and transactions verified on Monad blockchain
  - 1 MON = 250 in-app tokens
  - Message costs based on word count
  - On-chain verification via smart contract

- **🎭 Multiple Personas** — Different AI girlfriend personalities
  - **Sweet** — Caring and gentle
  - **Tsundere** — Initially cold but warm underneath
  - **Playful** — Fun-loving and energetic
  - Each with unique backgrounds, hobbies, likes, and dislikes

- **🔄 Autonomous Summarization** — Background workers automatically summarize conversations for long-term memory

- **📊 Streak & Reward System** — Daily login rewards with streak bonuses, tracked autonomously

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         FRONTEND (Next.js)                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌─────────────┐│
│  │ Wallet       │  │  Chat UI     │  │   Persona    │  │   Token     ││
│  │ Connect      │  │ (Socket.io   │  │   Select     │  │ Management  ││
│  │ (RainbowKit  │  │  + REST)     │  │              │  │ (Deposit/   ││
│  │  + Wagmi)    │  │              │  │              │  │  Withdraw)  ││
│  └──────────────┘  └──────────────┘  └──────────────┘  └─────────────┘│
└─────────────────────────────────────────────────────────────────────────┘
                                    ↕
┌─────────────────────────────────────────────────────────────────────────┐
│                       BACKEND (Bun + Hapi.js)                           │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │ API Routes: /auth, /chat, /personas, /token                      │  │
│  └──────────────────────────────────────────────────────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────┐ │
│  │ AI Service   │  │   Memory     │  │    Token     │  │ Autonomous│ │
│  │ (DeepSeek    │  │   Service    │  │   Service    │  │  Workers  │ │
│  │  v3 LLM)     │  │ (Context     │  │ (Viem +      │  │ (BullMQ)  │ │
│  │              │  │  Build)      │  │  Monad RPC)  │  │           │ │
│  └──────────────┘  └──────────────┘  └──────────────┘  └───────────┘ │
│  ┌────────────────────────────────────────────────────────────────┐   │
│  │ • Summary Worker (auto-summarization)                          │   │
│  │ • Engagement Worker (proactive morning/lunch/night messages)   │   │
│  │ • Cron Service (hourly trigger)                                │   │
│  │ • Relationship Service (intimacy calc, streak rewards)         │   │
│  └────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↕
┌─────────────────────────────────────────────────────────────────────────┐
│                           DATA LAYER                                    │
│  ┌──────────────────────────────────┐  ┌──────────────────────────┐   │
│  │ PostgreSQL (Prisma ORM)          │  │ Redis                    │   │
│  │ • Users                          │  │ • BullMQ queues          │   │
│  │ • Personas                       │  │ • Caching                │   │
│  │ • Messages                       │  │ • Deduplication          │   │
│  │ • Memories                       │  │                          │   │
│  │ • Balances                       │  │                          │   │
│  │ • Transactions                   │  │                          │   │
│  │ • UsageLogs                      │  │                          │   │
│  └──────────────────────────────────┘  └──────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↕
┌─────────────────────────────────────────────────────────────────────────┐
│                        BLOCKCHAIN LAYER                                 │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │ Monad Mainnet                                                    │  │
│  │ MonadTreasury.sol: 0x26f942e7c1D1F45c575649ed386C2fef68C06a8c  │  │
│  └──────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## How It Works

### User Flow

1. **Connect Wallet** — Users connect via RainbowKit/WalletConnect
2. **Select Persona** — Choose from sweet, tsundere, or playful personalities
3. **Deposit MON** — Send MON to treasury contract (1 MON = 100 tokens)
4. **Chat** — Each message costs tokens based on word count
5. **Build Relationship** — Intimacy grows with meaningful interactions
6. **Receive Proactive Messages** — AI autonomously sends contextual greetings

### AI Agent Autonomous Flow

1. **CronService** triggers hourly
2. **EngagementWorker** checks:
   - User timezone for appropriate timing
   - Time window (07-09 morning, 12-14 lunch, 21-23 night)
   - Last interaction (anti-spam >2h gap)
   - Redis dedup (1 msg per routine per day)
3. **AI generates** contextual message (persona-aware, relationship-aware)
4. **Message saved** to DB + emitted via Socket
5. **PARALLEL**: SummaryWorker auto-summarizes last 75 messages
6. **PARALLEL**: Profile extraction (name, job, preferences from chat)
7. **PARALLEL**: Relationship tracking with status progression:
   - **Stranger** (0-19) → **Friend** (20-39) → **Close** (40-69) → **Lover** (70-100)

---

## AI Agent Autonomy

| Feature | Description |
|---------|-------------|
| **Proactive Engagement** | Independently decides when and what to message based on time-of-day, timezone, and relationship context |
| **Memory Management** | Automatically extracts personal information from conversations |
| **Conversation Summarization** | Background worker autonomously summarizes conversations for long-term context |
| **Relationship Evolution** | Intimacy levels change dynamically based on interaction patterns |
| **Contextual Reasoning** | Responses generated with full context (persona traits, relationship status, history, memories) |
| **Anti-Spam Intelligence** | Smart cooldown logic (2-hour gap, daily dedup per routine type) |
| **Streak Recognition** | Tracks consecutive daily interactions, rewards consistent engagement |

---

## Monad Integration

### Why Monad?

- **Fast Transaction Finality** — Rapid confirmation for deposits and withdrawals
- **Low Gas Costs** — Affordable on-chain operations
- **EVM Compatibility** — Easy integration with existing Ethereum tooling

### Smart Contract: MonadTreasury

**Contract Address:** `0x26f942e7c1D1F45c575649ed386C2fef68C06a8c`

**Functions:**
- `deposit(userId)` — Users deposit MON tokens
- `withdraw()` (onlyOwner) — Contract owner withdrawals
- `getBalance()` — Query contract balance

### On-Chain Verification Flow

1. User sends MON → Contract
2. Backend verifies on-chain via Monad RPC using Viem
3. Validates recipient/amount/prevents double-processing
4. Credits in-app tokens (1 MON = 100 tokens)

---

## Technology Stack

### Backend

- **Bun** — JavaScript runtime
- **Hapi.js** — HTTP server framework
- **Prisma** — PostgreSQL ORM
- **BullMQ** — Job queue for background workers
- **Redis/IORedis** — Queue management, caching
- **Socket.io** — WebSocket real-time communication
- **Viem** — Monad blockchain interaction
- **DeepSeek v3** — Large Language Model for AI responses
- **Luxon** — Timezone handling
- **Joi** — Request validation
- **Hapi Swagger** — API documentation

### Frontend

- **Next.js 16** — React framework
- **React 19** — UI library
- **RainbowKit** — Wallet connection UI
- **Wagmi v3** — React hooks for Ethereum
- **Viem** — Ethereum library
- **Socket.io Client** — WebSocket client
- **Framer Motion** — Animations
- **Tailwind CSS v4** — Styling
- **Lucide React** — Icons

### Smart Contract

- **Solidity ^0.8.20** — Smart contract language
- **Foundry (Forge)** — Development framework
- **Monad Mainnet** — Deployment network

### Infrastructure

- **PostgreSQL** — Primary database
- **Redis** — Caching and queues
- **Monad RPC** — Blockchain interaction

---

## Repositories

| Repository | Description | Language |
|------------|-------------|----------|
| [my-bini-backend](https://github.com/its-my-bini/my-bini-backend) | AI agent backend server, autonomous workers, API | TypeScript (Bun) |
| [my-bini-frontend](https://github.com/its-my-bini/my-bini-frontend) | Web application UI | TypeScript (Next.js) |
| [my-bini-contract](https://github.com/its-my-bini/my-bini-contract) | MonadTreasury smart contract | Solidity (Foundry) |

---

## Smart Contract

### MonadTreasury Interface

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

interface IMonadTreasury {
    // Events
    event Deposit(address indexed user, uint256 amount, string userId);
    event Withdrawal(address indexed owner, uint256 amount);

    // Functions
    function deposit(string memory userId) external payable;
    function withdraw(uint256 amount) external;
    function getBalance() external view returns (uint256);
    
    // View Functions
    function owner() external view returns (address);
    function totalDeposits() external view returns (uint256);
}
```

**Deployed Contract:** `0x26f942e7c1D1F45c575649ed386C2fef68C06a8c` on Monad Mainnet

---

## API Endpoints

### Authentication
- `POST /auth/wallet-login` — Login with wallet signature

### User
- `GET /user/profile` — Get user profile and stats
- `POST /user/select-persona` — Select AI companion persona

### Personas
- `GET /personas` — List all available personas

### Chat
- `POST /chat` — Send message to AI companion
- `GET /chat/history` — Retrieve chat history

### Token
- `GET /token/balance` — Get current token balance
- `POST /token/deposit` — Process MON deposit
- `POST /token/withdraw` — Withdraw tokens
- `POST /token/daily-reward` — Claim daily login reward

### Health
- `GET /health` — Service health check

### WebSocket Events
- `balance:update` — Token balance changed
- `message:receive` — New message from AI
- `notification` — System notification
- `typing` — AI is typing indicator

---

## Getting Started

Each repository contains detailed setup instructions:

- **Backend:** See [my-bini-backend README](https://github.com/its-my-bini/my-bini-backend#readme)
- **Frontend:** See [my-bini-frontend README](https://github.com/its-my-bini/my-bini-frontend#readme)
- **Smart Contract:** See [my-bini-contract README](https://github.com/its-my-bini/my-bini-contract#readme)

---

## License

All repositories are licensed under the [MIT License](../LICENSE).

---

<div align="center">

**Built with 💕 for the Moltiverse Hackathon 2026**

</div>
