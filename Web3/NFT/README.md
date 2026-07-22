# 🖼️ Non-Fungible Tokens (NFTs) Reference

Non-Fungible Tokens (NFTs) represent unique, non-interchangeable digital assets recorded on a blockchain.

---

## 📐 Token Standards

### 1. Ethereum Standards
- **ERC-721**: Individual unique tokenId mapping to owner addresses (`ownerOf(tokenId)`).
- **ERC-1155**: Multi-token standard handling batch minting, transfers, and semi-fungible tickets.

### 2. Solana Standards (Metaplex)
- Uses standard **SPL Token** accounts with `supply = 1` and `decimals = 0`.
- **Metaplex Token Metadata**: Attaches a PDA account storing token name, symbol, uri (JSON metadata pointer), and seller fee basis points (royalties).

---

## 📦 Decentralized Metadata Storage

To prevent central server dependency, NFT metadata (JSON files & media files) is pinned to decentralized storage networks:
- **IPFS (InterPlanetary File System)**: Content-addressed peer-to-peer storage using SHA-256 hashes (`ipfs://...`).
- **Arweave**: Permanent decentralized file store with pay-once, store-forever token economics.

---

## 🎨 Metaplex Metadata Schema Example

```json
{
  "name": "OpenCS Builder #001",
  "symbol": "OCS",
  "description": "Exclusive OpenCS Web3 Developer Badge",
  "image": "https://arweave.net/example-image-hash",
  "attributes": [
    { "trait_type": "Track", "value": "Solana Rust" },
    { "trait_type": "Level", "value": "Master" }
  ],
  "properties": {
    "files": [{ "uri": "https://arweave.net/example-image-hash", "type": "image/png" }],
    "category": "image"
  }
}
```

---

## 🔗 Learning Links
- [Metaplex Developer Portal](https://developers.metaplex.com/)
- [OpenZeppelin ERC-721 Standard](https://docs.openzeppelin.com/contracts/4.x/erc721)
- [IPFS Documentation](https://docs.ipfs.tech/)
