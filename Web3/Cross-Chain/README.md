# 🌉 Cross-Chain Interoperability Reference

Cross-Chain interoperability solutions enable state transfers, asset transfers, and arbitrary message passing across distinct blockchain networks (e.g. Ethereum ↔ Solana).

---

## 🏗️ Bridge Models & Architectures

```
[ Chain A ] ── Lock Asset ──► [ Bridge Vault ]
                                    │
                            (Validator Signatures)
                                    │
[ Chain B ] ◄── Mint Synthetic ── [ Bridge Contract ]
```

1. **Lock-and-Mint**: User locks native assets on Chain A. A multi-sig validator relay detects the deposit and mints equivalent wrapped tokens (e.g. wETH) on Chain B.
2. **Burn-and-Mint**: User burns wrapped tokens on Chain B. Relayers release locked native tokens on Chain A.
3. **Liquidity Pools**: Relies on liquidity pools across chains to swap native assets directly without wrapped tokens.

---

## 🔒 Major Protocols & Messaging Networks

- **LayerZero**: Omnichain interoperability protocol using ultra-light nodes and relayer-oracle separation for cross-chain execution.
- **Chainlink CCIP (Cross-Chain Interoperability Protocol)**: Secure cross-chain messaging standard using Chainlink decentralized oracle networks.
- **Wormhole**: Generic message passing protocol routing messages between Solana, Ethereum, BSC, and Polygon via 19 Guardian nodes.

---

## ⚠️ Bridge Security Hazards

Cross-chain bridges represent major honeypots for security exploits.
- **Wormhole Exploit (2022)**: Signature verification bypass allowing 120k ETH minting without collateral.
- **Ronin Bridge Exploit (2022)**: Compromise of 5 out of 9 validator private keys.

---

## 🔗 Learning Links
- [Wormhole Developer Documentation](https://docs.wormhole.com/)
- [LayerZero Protocol Docs](https://layerzero.network/)
- [Cross-Chain Scaling (Week 59)](../../weeks/Week-59.md)
