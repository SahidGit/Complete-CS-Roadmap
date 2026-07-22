# 🌀 Layer 2 Rollups Reference

Rollups execute transactions off-chain, bundle hundreds of transactions into a single compressed batch root, and post transaction data back to Layer 1 (L1) for data availability and security guarantees.

---

## ⚖️ Optimistic vs ZK Rollups

```
                     ┌────────────────────────┐
                     │    Off-Chain Batch     │
                     └───────────┬────────────┘
                                 │
                 ┌───────────────┴───────────────┐
                 ▼                               ▼
       [ Optimistic Rollup ]              [ ZK Rollup ]
  Assumes validity by default.        Generates Validity Proof
  Requires 7-day challenge window    (zk-SNARK) off-chain.
  via Fraud Proofs.                  Instant L1 finality verification.
```

### 1. Optimistic Rollups
- **Examples**: Arbitrum, Optimism, Base.
- **Mechanism**: Sequencers commit state roots to L1. If state root is invalid, verifiers submit a **Fraud Proof** asserting incorrect state execution.

### 2. ZK-Rollups
- **Examples**: zkSync Era, Starknet, Scroll, Linea.
- **Mechanism**: Sequencers execute transactions and generate a cryptographic validity proof. The proof is verified by L1 smart contracts instantly upon submission.

---

## 🔗 Learning Links
- [L2BEAT Rollup Analytics & Security](https://l2beat.com/)
- [Arbitrum Developer Docs](https://docs.arbitrum.io/)
- [Optimism Docs](https://docs.optimism.io/)
