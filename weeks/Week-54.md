# 🎯 Week 54: Solana Architecture & Web3.js

> **Duration:** 24 hours | **Difficulty:** 🔴 Advanced | **Prerequisites:** Weeks 51–53

## 📌 Goal
Understand the Solana Virtual Machine (SVM), master the decoupled account-based state model, interact with RPC nodes, and build clients using `@solana/web3.js`.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Understand Solana's stateless program and stateful account decoupling model
- ✅ Differentiate between System, Executable, and Token accounts
- ✅ Generate and manage keypairs and derive Program Derived Addresses (PDAs)
- ✅ Construct, serialize, sign, and broadcast transactions
- ✅ Fetch account data and stream updates via JSON-RPC connections
- ✅ Code client applications using `@solana/web3.js`

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 51 (Keys & Wallets), Week 53 (Transactions & Gas), basic Javascript.
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🔴 Advanced

---

## 📖 Concepts & Theory

### 1. The Solana Account Model
On Solana, programs are **stateless**. This contrasts with Ethereum, where contract code and state are stored in the same account.
- **Executable Account**: Holds compiled code (read-only).
- **Data Account**: Holds variables/state (owned by a program, writable).

```
[ Writable Transaction ] ──► [ Executable Program Account ]
                                  │
                                  ▼ (Reads & Writes data to)
                             [ User Data Account ]
```

### 2. Transactions & Instructions
A Solana transaction contains:
- **Signatures**: Array of cryptographic signatures authorizing the action.
- **Message**: Contains instructions, header limits, and an array of all accounts referenced in the instruction (flagged as read-only or writable).
- **Instruction**: The unit of execution containing:
  - `programId`: The address of the program handling this instruction.
  - `keys`: Array of accounts referenced by the instruction.
  - `data`: A raw byte array containing parameters for the program.

---

## 💻 Daily Study Plan

### 📅 Monday: Account Internals & Rent
- Study the account structure (lamports, data, owner, executable, rent_epoch).
- Learn about Solana **Rent exemption** (minimum balance required to store data on-chain).

### 📅 Tuesday: JavaScript client setup (@solana/web3.js)
- Install `@solana/web3.js`. Connect to Devnet RPC.
- Generate keypairs, request devnet test airdrops (`requestAirdrop`), and check balances.

### 📅 Wednesday: Constructing Transactions
- Learn how to construct `TransactionInstruction` blocks manually.
- Add instructions to a transaction, fetch the recent blockhash, sign, and send.

### 📅 Thursday: Program Derived Addresses (PDAs)
- Study `PublicKey.findProgramAddressSync()`.
- Learn how seeds and a bump seed are used to generate keys off the Ed25519 curve.

### 📅 Friday: Projects Implementation
- Build the **Solana Wallet App** and **SPL Token Creator** client templates.

### 📅 Saturday: Labs & RPC Queries
- Practice streaming real-time network transfers using `onAccountChange()` websocket bindings.

### 📅 Sunday: Revision & Interview Prep
- Review rent calculation rates and transaction serialization formats.

---

## 🧪 Projects & Implementation Guide

### Project 1: Solana Web Wallet App
- **Architecture**: A Javascript/HTML dashboard generating keys, checking Devnet balances, and transferring SOL using `@solana/web3.js`.
- **Folder Structure**:
  ```
  wallet-app/
  ├── index.html
  ├── app.js
  └── package.json
  ```
- **Implementation Guide**: Use `SystemProgram.transfer()` to construct instruction blocks, and connect it to a simple frontend UI.

### Project 2: SPL Token Creator
- **Architecture**: App constructing mint, metadata, and token accounts to create custom Solana tokens.

### Project 3: Real-Time Network Monitor
- **Architecture**: Script subscribing to public RPC ports to stream transactions.

---

## 📝 Practice Exercises
1. Connect to Devnet and fetch the balance of a public key.
2. Build and send a transaction containing a memo instruction using the Memo Program.
3. Compute the rent-exemption fee for an account storing 100 bytes of data.
4. Derive a Program Derived Address (PDA) using a string seed and a dummy program ID.

---

## 💼 Interview Questions & Answers
- **Q**: Why are transactions cheaper and faster on Solana compared to Ethereum?
- **A**: Solana utilizes **Proof of History (PoH)** to establish chronological order of events without nodes having to wait to sync with each other. Furthermore, because transactions declare exactly which accounts they will read and write to upfront, the runtime can execute non-conflicting transactions in parallel (using Sealevel engine) rather than sequentially.

---

## 📖 Official Resources
- [Solana Docs: Account Model](https://docs.solana.com/developing/programming-model/accounts)
- [Solana CookBook: Transaction reference](https://solanacookbook.com/)
