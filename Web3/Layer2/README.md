# ⚡ Layer 2 Scaling Solutions Reference

Layer 2 (L2) refers to secondary frameworks and protocols built on top of a primary blockchain (Layer 1) to drastically increase transaction throughput and lower fee costs.

---

## 🏛️ Scaling Taxonomy

| L2 Paradigm | Security Location | Execution | Data Availability |
|---|---|---|---|
| **Optimistic Rollups** | L1 | Off-chain | L1 (Calldata / Blobs) |
| **ZK-Rollups** | L1 | Off-chain | L1 (Calldata / Blobs) |
| **Validiums** | L1 Proofs / Off-chain Data | Off-chain | Off-chain Data Availability Committee |
| **State Channels** | L1 Settlement | Off-chain P2P | Off-chain participants |
| **Sidechains** | Independent Consensus | Off-chain | Sidechain Validators |

---

## 🌐 EIP-4844 (Proto-Danksharding) & Blobs

Ethereum EIP-4844 introduced **Blob Data Space** specifically designed for L2 Rollup data availability, reducing Layer 2 transaction costs by up to 10x-100x compared to traditional calldata storage.

---

## 🔗 Learning Links
- [Ethereum Layer 2 Scaling Primer](https://ethereum.org/en/layer-2/)
- [Polygon Network Documentation](https://docs.polygon.technology/)
- [Advanced Scaling & Layer 2 (Week 59)](../../weeks/Week-59.md)
