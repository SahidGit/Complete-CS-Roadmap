# 🛡️ Zero-Knowledge (ZK) Cryptography Reference

Zero-Knowledge (ZK) cryptography allows one party (the Prover) to prove mathematically to another party (the Verifier) that a statement is true without revealing any information beyond the statement's validity.

---

## 🔑 Key Concepts & Terminology

### 1. ZK-SNARK vs ZK-STARK

| Metric | ZK-SNARK | ZK-STARK |
|---|---|---|
| **Full Form** | Zero-Knowledge Succinct Non-Interactive Argument of Knowledge | Zero-Knowledge Scalable Transparent Argument of Knowledge |
| **Proof Size** | Very Small (~200-400 bytes) | Larger (~10-100 KB) |
| **Trusted Setup** | Required (except Halo2 / Plonk) | Not Required (Transparent) |
| **Quantum Resistance** | No (based on elliptic curves) | Yes (based on hash functions) |

### 2. ZK Circuit
A mathematical representation of computations expressed as arithmetic constraint systems (R1CS).
- Popular domain-specific languages: **Circom**, **Noir**, **Leo**, **Cairo**.

---

## 🛠️ Typical ZK Workflow

```
[ Secret Inputs (Witness) + Public Inputs ]
                    │
                    ▼
          [ Prover & ZK Circuit ]
                    │
                    ▼
             [ ZK Proof ]
                    │
                    ▼
[ On-Chain Verifier Contract / Client ] ──► Valid / Invalid
```

---

## 🔗 Learning Links
- [Circom & SnarkJS Guide](https://docs.circom.io/)
- [Aztec Noir Language](https://noir-lang.org/)
- [ZK Cryptography Guide (Week 59)](../../weeks/Week-59.md)
