# 🎯 Week 56: Web3 & Frontend Wallet Integration

> **Duration:** 24 hours | **Difficulty:** 🟡 Intermediate | **Prerequisites:** Week 54 (Solana Web3.js)

## 📌 Goal
Build modern Web3 frontend applications, integrate wallet adapters (Phantom, Solflare, WalletConnect), securely request transaction signatures, and bind client UI states to smart program accounts.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Integrate the Solana Wallet Adapter libraries into a React application
- ✅ Connect Phantom/Solflare wallets and manage connection lifecycle states
- ✅ Fetch, render, and update UI balances in real time
- ✅ Bind and send transaction signing prompts to user wallets
- ✅ Deserialize and parse on-chain program accounts to render inside React states
- ✅ Design responsive Web3 dashboards

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 7 (React), Week 54 (Solana Web3.js client).
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🟡 Intermediate

---

## 📖 Concepts & Theory

### 1. The Web3 Wallet Loop
In a Web3 application, the frontend is responsible for the user interface, while the wallet browser extension handles security (private keys).

```
[ React UI ] ──► Request Action ──► [ Wallet Extension ] ──► Sign & Send ──► [ RPC / Blockchain ]
     ▲                                                                              │
     └────────────────────── Stream State Updates ──────────────────────────────────┘
```

### 2. Solana Wallet Adapter Libraries
To integrate wallets into React, use three standard modular packages:
- `@solana/wallet-adapter-base`: Common interfaces and events.
- `@solana/wallet-adapter-react`: React Hooks (`useWallet()`, `useConnection()`) and Context providers (`WalletProvider`, `ConnectionProvider`).
- `@solana/wallet-adapter-react-ui`: Pre-styled React UI components (like the `WalletMultiButton`).

---

## 💻 Daily Study Plan

### 📅 Monday: Wallet Adapter Context Configuration
- Study the context structure of `ConnectionProvider` and `WalletProvider` in React.
- Set up a clean React boilerplate incorporating wallet adapter provider configurations.

### 📅 Tuesday: Wallet State Hooks
- Use the `useWallet()` hook to access the current connection state (`connected`, `publicKey`, `sendTransaction`).
- Render fallback components if the user's wallet is not connected.

### 📅 Wednesday: Querying Custom States
- Fetch and deserialize Anchor data accounts from React components using the generated IDL.
- Set up React states and loading templates.

### 📅 Thursday: Triggering Signed Transactions
- Construct transactions inside React, prompt the user's connected wallet to sign, and stream completion confirmations.
- Use toast alerts to notify users of block confirmations.

### 📅 Friday: Projects Implementation
- Build the **Token Swap UI** and **Wallet Portfolio Dashboard** projects.

### 📅 Saturday: Labs & Optimization
- Implement automatic network re-connection and handle user reject-to-sign transaction errors gracefully.

### 📅 Sunday: Revision & Interview Prep
- Review wallet security boundaries and transaction confirmation stages.

---

## 🧪 Projects & Implementation Guide

### Project 1: Web3 Wallet Portfolio Dashboard
- **Architecture**: A React application connecting wallets, listing all custom token balances (SPL tokens), and showing transaction history logs.
- **Folder Structure**:
  ```
  portfolio-dashboard/
  ├── src/
  │   ├── App.jsx
  │   ├── components/WalletButton.jsx
  │   └── hooks/useFetchBalances.js
  ├── package.json
  └── vite.config.js
  ```
- **Implementation Guide**: Use the `@solana/wallet-adapter` packages. Query token accounts using `connection.getParsedTokenAccountsByOwner()`.

### Project 2: DApp Token Swap UI
- **Architecture**: A swap client interface showing token exchange forms and executing swaps on Devnet.

### Project 3: Anchor Program Web Client
- **Architecture**: React application linking instructions of the Week 55 Voting DApp.

---

## 📝 Practice Exercises
1. Setup a React application displaying the connected user's SOL balance.
2. Implement a button that requests the user to sign a custom string text signature verification payload.
3. Write a custom React hook that subscribes to the user's balance updates using WebSockets (`onAccountChange`).
4. Design a clean, responsive modal window listing all supported Solana wallets.

---

## 💼 Interview Questions & Answers
- **Q**: Why shouldn't a frontend application hold or collect the user's private key?
- **A**: Frontends are vulnerable to Cross-Site Scripting (XSS) and phishing attacks. Letting the frontend manage private keys exposes users to complete fund drains. Modern Web3 DApps delegate private key management and signing operations exclusively to secure browser extensions (wallets) via sandbox bridges.

---

## 📖 Official Resources
- [Solana Wallet Adapter GitHub Repository](https://github.com/solana-labs/wallet-adapter)
- [Solana Developers: Integrating Wallets Guide](https://solana.com/developers)
