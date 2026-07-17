# 💸 DeFi Engineering Reference

Decentralized Finance (DeFi) replaces traditional centralized financial services with automated, trustless smart contract protocols.

---

## 🏗️ Core Algorithms

### 1. Automated Market Makers (AMM)
AMMs allow assets to be traded automatically by using liquidity pools instead of traditional order books.
- **Constant Product Formula (Uniswap V2)**:
  $$x \cdot y = k$$
  - $x$: Token A pool quantity.
  - $y$: Token B pool quantity.
  - $k$: Constant invariant.
- When executing a swap, the product of $x$ and $y$ must remain equal to $k$ (excluding fee margins).

```
Token A Swap (In) ──► [ Liquidity Pool ] ──► Token B (Out)
                       Formula: x * y = k
```

### 2. Collateralized Debt Positions (CDP)
Users lock collateral (e.g. ETH) in a smart contract to mint or borrow stablecoins (e.g. DAI).
- **Collateralization Ratio**:
  $$Ratio = \frac{Collateral\ Value}{Debt\ Value}$$
- If this ratio falls below a liquidation threshold (e.g. 150%), the contract automatically liquidates the collateral at a discount to cover the debt.

### 3. Decentralized Oracles (Chainlink)
Smart contracts cannot access external web APIs (due to consensus deterministic rules). **Oracles** retrieve and push real-world data (like coin prices) onto the blockchain.

---

## 🔗 Learning Links
- [DeFi Math and AMM Weekly Guide](../../weeks/Week-57.md)
- [Uniswap V2 Core Whitepaper](https://uniswap.org/whitepaper.pdf)
