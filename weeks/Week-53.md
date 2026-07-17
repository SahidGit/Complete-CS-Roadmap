# 🎯 Week 53: Blockchain Architecture & Consensus Mechanics

> **Duration:** 24 hours | **Difficulty:** 🟡 Intermediate | **Prerequisites:** Week 51 (Cryptography)

## 📌 Goal
Understand decentralized networks, master transaction blocks, examine consensus algorithms (Proof of Work vs. Proof of Stake), and simulate a blockchain from scratch.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Model a cryptographically linked transaction block chain
- ✅ Understand and simulate Proof of Work (PoW) mining difficulty
- ✅ Contrast Proof of Work vs. Proof of Stake (PoS) validator consensus
- ✅ Understand transaction states (mempool, signatures, gas fees)
- ✅ Explore standard token interfaces (ERC-20, ERC-721, SPL)

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 51 (Cryptography & hashing math), basic Javascript/Rust syntax.
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🟡 Intermediate

---

## 📖 Concepts & Theory

### 1. Structure of a Block
A blockchain is a linked list of data blocks secured by hash links:
- **Block Header**: Contains the block version, timestamp, difficulty target, nonce, Merkle Root of transactions, and the **Previous Block's Hash** (linking the chain).
- **Block Body**: Contains list of transaction data records.

```
Block 1 (Parent)                  Block 2 (Child)
┌────────────────────────┐        ┌────────────────────────┐
│ Prev Hash: 000000000   │        │ Prev Hash: HASH_BLOCK1 │◄─── Cryptographic Link
│ Timestamp: ...         │        │ Timestamp: ...         │
│ Nonce: 49302           │        │ Nonce: 12049           │
│ Hash: HASH_BLOCK1      │        │ Hash: HASH_BLOCK2      │
└────────────────────────┘        └────────────────────────┘
```

### 2. Consensus Algorithms
Decentralized nodes must agree on which block is added to the chain next:
- **Proof of Work (PoW)**: Nodes (miners) compete to solve a complex hash puzzle (finding a nonce that produces a block hash starting with $D$ leading zeros).
- **Proof of Stake (PoS)**: Validators lock native tokens (Stake) as collateral. A validator is chosen pseudo-randomly to sign the next block based on stake weight.

---

## 💻 Daily Study Plan

### 📅 Monday: Blockchain Data Structures
- Learn block header parameters.
- Build a basic `Block` and `Blockchain` class in Javascript/Rust.

### 📅 Tuesday: Proof of Work Simulation
- Learn how mining difficulty targets restrict output hashes.
- Write a mining loop that increments a `nonce` until the block hash matches difficulty targets.

### 📅 Wednesday: Proof of Stake & Validators
- Learn about slashing rules, validator selection, and finality checkpoints.
- Study the concept of Sybil Attacks and how staking/mining mitigates them.

### 📅 Thursday: Transactions & Mempool
- Learn how transactions are signed using private keys and stored in a mempool before selection.
- Understand transaction fees (gas) and execution prioritization.

### 📅 Friday: Projects Implementation
- Build the **Mini Blockchain** and **Token Simulator** projects.

### 📅 Saturday: Labs & Exercises
- Simulate adding nodes, syncing state, and resolving longest-chain conflicts.

### 📅 Sunday: Revision & Interview Prep
- Contrast block production times and consensus security margins.

---

## 🧪 Projects & Implementation Guide

### Project 1: Mini Blockchain Simulator
- **Architecture**: A Javascript/Python module implementing block mining (PoW), cryptographic links, and a validation runner.
- **Folder Structure**:
  ```
  mini-blockchain/
  ├── Block.js
  ├── Blockchain.js
  └── test.js
  ```
- **Implementation Guide**: Compute hashes using SHA-256. Implement `isChainValid()` by checking hash links and difficulty constraints.

### Project 2: Token Interface Simulator
- **Architecture**: Program simulating ledger balance adjustments, mints, and transfers similar to ERC-20 rules.

### Project 3: Block Explorer API
- **Architecture**: Simple Express API showing block details, transactions history, and address balances.

---

## 📝 Practice Exercises
1. Implement a mining function that takes a block and mines it (finds the nonce) for a difficulty of 4 (hash must start with "0000").
2. Write a function `isChainValid()` that verifies a blockchain's link safety and hashes consistency.
3. Simulate a fork conflict where two nodes submit different blocks, and resolve it using the "longest chain rule".
4. Design a ledger system that validates transfer transactions against account balances.

---

## 💼 Interview Questions & Answers
- **Q**: What is the "Longest Chain Rule" in Nakamoto Consensus?
- **A**: If a blockchain splits (forks) due to two miners producing valid blocks simultaneously, nodes continue building on the branch they received first. Once one branch becomes longer (contains more cumulative PoW difficulty), all nodes automatically switch to that longer chain, discarding the shorter one.

---

## 📖 Official Resources
- [Bitcoin Whitepaper (Satoshi Nakamoto)](https://bitcoin.org/bitcoin.pdf)
- [Ethereum Whitepaper](https://ethereum.org/en/whitepaper/)
