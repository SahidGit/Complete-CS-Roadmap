# 🔑 Cryptography Reference

This section details foundational cryptographic primitives used to secure blockchain state transitions, wallet authorizations, and block consensus.

---

## 🏗️ Core Primitives

### 1. Hash Functions (SHA-256 / Keccak-256)
- One-way deterministic functions mapping arbitrary input lengths to fixed-size outputs.
- *Properties*: Pre-image resistance, Second pre-image resistance, Collision resistance.
- Used to chain blocks, create unique transaction IDs, and construct Merkel trees.

### 2. Merkle Trees
A cryptographic tree structure where every leaf node is labeled with the cryptographic hash of a data block, and every non-leaf node is labeled with the cryptographic hash of its child nodes.
- Allows $O(\log N)$ validation of dataset inclusion without holding the entire dataset.

```
                  [ Root Hash ] (Merkle Root)
                 /             \
          [ Hash A-B ]     [ Hash C-D ]
          /         \       /         \
      [Hash A]   [Hash B] [Hash C]   [Hash D]
         |          |        |          |
      (Tx A)     (Tx B)   (Tx C)     (Tx D)
```

### 3. Public-Key Cryptography (ECDSA / Ed25519)
- **Public Key**: Derives from the private key via one-way elliptic curve point multiplication. Serves as your identity (address).
- **Private Key**: A randomly generated 256-bit number. Used to generate digital signatures to authorize transactions.
- **Elliptic Curves**: Ethereum uses **secp256k1**; Solana uses **Ed25519** (faster signatures, better security properties).

---

## 🔗 Learning Links
- [Cryptography Weekly Guide](../../weeks/Week-51.md)
- [Official Solana Cookbook: Keys & Wallets](https://solanacookbook.com/)
