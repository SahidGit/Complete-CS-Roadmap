# 🛡️ Smart Contract Auditing Reference

Smart contracts are immutable: once deployed, they cannot be updated easily. Therefore, auditing code is a critical step in the development lifecycle.

---

## ⚠️ Common Smart Contract Vulnerabilities

### 1. Reentrancy (EVM/Solidity)
Occurs when a contract sends funds to an untrusted contract before updating its balance state. The target contract can trigger fallback functions to recursively withdraw funds until the pool is empty.

```
Contract A                        Contract B (Attacker)
   │                                 │
   ├─► withdraw() ──────────────────►│
   │                                 ├─► fallback()
   │                                 │    (Recursive call)
   │◄─ withdraw() ───────────────────┤
```
- *Mitigation*: Use the **Checks-Effects-Interactions** pattern, or apply reentrancy guard modifiers (e.g. OpenZeppelin's `nonReentrant`).

### 2. Underflows & Overflows
Math errors occurring when values exceed their maximum or minimum storage limits.
- *Mitigation*: Use Solidity 0.8+ (which throws compiler exceptions on overflows) or Rust's safe math methods (`checked_add`, `checked_sub`).

### 3. Missing Access Controls
Private variables or admin functions (like `withdrawFees()`) exposed publicly without authorization modifiers.
- *Mitigation*: Restrict execution using OpenZeppelin's `Ownable` (`onlyOwner`) or Anchor constraints (`#[account(mut, has_one = authority)]`).

---

## 🛠️ Static Analysis Tools
- **Slither**: A Solidity static analysis framework written in Python. Detects common bugs and generates contract dependency graphs.
- **Mythril**: A security analysis tool for EVM bytecode using symbolic execution.

---

## 🔗 Official Documentation
- [OWASP Smart Contract Security Top 10](https://owasp.org/)
- [OpenZeppelin Contracts Library](https://docs.openzeppelin.com/contracts/)
- [Solana Security Guide Cookbook](https://solanacookbook.com/)
