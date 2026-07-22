# 👛 Web3 Wallets & Key Management Reference

Web3 wallets store public and private keypairs, enable cryptographic message signing, construct transactions, and interface with decentralized RPC nodes.

---

## 🔑 Hierarchical Deterministic (HD) Wallets

HD Wallets generate a tree of keys from a single seed phrase using standardized Bitcoin Improvement Proposals (BIPs).

```
Mnemonic Seed (12/24 Words - BIP-39)
        │
        ▼
   Master Key (BIP-32)
        │
        ▼
Derivation Path (BIP-44: m/44'/60'/0'/0/0 for Ethereum, m/44'/501'/0'/0' for Solana)
        │
  ┌─────┴─────┐
  ▼           ▼
Key 0       Key 1
```

---

## 🌐 Wallet Connection Standards

### 1. Solana Wallet Adapter
- Modular libraries binding wallets (Phantom, Solflare, Backpack) to frontend apps using standard React hooks (`useWallet`, `useConnection`).

### 2. WalletConnect
- Open protocol communicating encrypted messages between dApps and mobile wallet applications via WebSocket relay servers.

### 3. EIP-1193 & EIP-6963 (Ethereum)
- JavaScript provider injected into `window.ethereum`, allowing dApps to request accounts and transaction signatures.

---

## 🛡️ Security Best Practices

1. **Never store raw private keys** on client apps or frontend code.
2. Use **hardware wallets** (Ledger, Trezor) for high-value transactions.
3. Utilize **Account Abstraction (ERC-4337)** or **Multisig (Squads / Gnosis)** for enterprise access management.

---

## 🔗 Learning Links
- [Solana Wallet Adapter Docs](https://github.com/solana-labs/wallet-adapter)
- [BIP-39 Mnemonic Specification](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)
- [Web3 Wallet Integration (Week 56)](../../weeks/Week-56.md)
