# 🎯 Week 57: Decentralized Finance (DeFi) Engines

> **Duration:** 24 hours | **Difficulty:** 🔴 Advanced | **Prerequisites:** Week 53 (Blockchain Basics) & Week 55 (Anchor Framework)

## 📌 Goal
Understand Decentralized Finance (DeFi) mathematical architectures, build automated market maker pricing pools, model collateral lending rates, and integrate price feeds.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Implement a Constant Product ($x \cdot y = k$) AMM swap program
- ✅ Write on-chain logic to manage Liquidity Provider (LP) tokens
- ✅ Understand Slippage, Impermanent Loss, and price impact calculations
- ✅ Model collateral lending vaults and liquidation thresholds
- ✅ Query and integrate real-time Pyth or Chainlink price feeds in smart programs
- ✅ Deploy a local DEX swap engine

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 53 (AMM theory), Week 55 (Anchor Program constraints).
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🔴 Advanced

---

## 📖 Concepts & Theory

### 1. Constant Product AMM Math
Uniswap V2 style exchanges use the invariant $x \cdot y = k$:
- If a user swaps $\Delta x$ amount of Token A into the pool, they receive $\Delta y$ amount of Token B:
  $$(x + \Delta x)(y - \Delta y) = k$$
- Solving for $\Delta y$ yields the output token amount (excluding fees):
  $$\Delta y = \frac{y \cdot \Delta x}{x + \Delta x}$$

```
                Pool State: x * y = k
                ┌──────────────────┐
Token A (In) ──►│ x = x + delta x  │
                │ y = y - delta y  │──► Token B (Out)
                └──────────────────┘
```

### 2. Impermanent Loss (IL)
The difference in value between holding tokens in an AMM pool vs. simply holding them in a wallet.
- Occurs when the price ratio of the pooled tokens changes.
- **Formula**:
  $$IL = \frac{2\sqrt{r}}{1 + r} - 1 \quad \text{where } r \text{ is the new price ratio}$$

---

## 💻 Daily Study Plan

### 📅 Monday: AMM Mathematics & Swaps
- Study constant product mathematics. Calculate slippage and output prices on paper.
- Write a node script simulating trades, adjusting invariants, and tracking fee splits.

### 📅 Tuesday: Building a Solana AMM Pool
- Write the structural definitions for an Anchor DEX pool (storing two token vault addresses and LP supply).
- Implement the `swap()` instruction applying constant product checks.

### 📅 Wednesday: Liquidity Provisioning (LP)
- Implement `deposit_liquidity()` and `withdraw_liquidity()` instructions.
- Calculate and mint proportional LP tokens to depositors.

### 📅 Wednesday: Lending & CDPs
- Study collateral debt architectures. Formulate liquidation health checks.
- Code a mock lending program checking asset valuations before loan approvals.

### 📅 Friday: Projects Implementation
- Build the **DEX Swap Engine** program and write integration tests.

### 📅 Saturday: Oracles Integration
- Learn how to integrate the Pyth Network Oracle to fetch SOL/USD prices on Devnet.
- Write program conditions checking oracle prices before execution.

### 📅 Sunday: Revision & Interview Prep
- Review Impermanent Loss formulas and flash-loan structures.

---

## 🧪 Projects & Implementation Guide

### Project 1: Constant Product Swap Engine
- **Architecture**: Anchor program initializing a token pool, accepting deposits/withdrawals of liquidity, and executing swaps.
- **Folder Structure**:
  ```
  swap-engine/
  ├── programs/swap-engine/src/lib.rs
  ├── tests/swap.ts
  └── Anchor.toml
  ```
- **Implementation Guide**: Use the safe math library (`checked_mul`, `checked_div`) in Rust to prevent integer overflows during constant product calculations.

### Project 2: Yield Optimizer Calculator
- **Architecture**: App calculating interest returns across different liquidity pool weight ratios.

### Project 3: Decentralized Lending Vault
- **Architecture**: Program permitting users to borrow stable tokens against collateral deposits.

---

## 📝 Practice Exercises
1. Calculate the output of a swap if Token A pool has 100 tokens, Token B pool has 500 tokens, and the user swaps 10 Token A.
2. Calculate the impermanent loss if the price of one token in a pool doubles.
3. Write a Rust function that calculates the collateral health factor of a user borrowing stablecoins.
4. Write a script to retrieve the latest price of BTC from the Pyth Oracle on Solana Devnet.

---

## 💼 Interview Questions & Answers
- **Q**: What is Slippage in AMM models?
- **A**: Slippage is the difference between the expected price of a trade and the actual executed price. In AMMs, since trades shift the ratio of tokens in the pool ($x/y$), execution prices degrade dynamically based on the trade volume relative to the pool's liquidity depth.

---

## 📖 Official Resources
- [Uniswap V2 Smart Contracts Reference](https://docs.uniswap.org/contracts/v2/concepts/protocol-overview/how-uniswap-works)
- [Pyth Network Developer Documentation](https://docs.pyth.network/)
