# 🌐 Web3 & Blockchain Reference Hub

Welcome to the Web3 & Blockchain Engineering reference library. This section covers core cryptography math, Rust systems programming, decentralized networks (Solana & Ethereum), smart contract frameworks (Anchor & Solidity), decentralized finance (DeFi) engines, audits, and scaling protocols (Rollups, Layer 2, Bridges).

---

## 📁 Directory Map

| Section | Link | Description |
| :--- | :--- | :--- |
| **Cryptography** | [Cryptography/](./Cryptography/README.md) | SHA-256, ECDSA signatures, Merkle Trees, and public/private key pairs. |
| **Rust** | [Rust/](./Rust/README.md) | Systems engineering: Memory safety, ownership/borrowing, and lifetimes. |
| **Solana** | [Solana/](./Solana/README.md) | Account-based state architectures, PDAs, and transaction serialization. |
| **Anchor Framework** | [Anchor/](./Anchor/README.md) | Rust eDSL framework for building secure Solana programs. |
| **Smart Contracts** | [Smart-Contracts/](./Smart-Contracts/README.md) | EVM/Solidity and SVM/Rust execution systems. |
| **Ethereum** | [Ethereum/](./Ethereum/README.md) | EVM bytecode execution, Gas structures, and ERC standard interfaces. |
| **DeFi** | [DeFi/](./DeFi/README.md) | Automated Market Makers (AMM), DEX pricing, and lending calculations. |
| **Auditing & Security** | [Auditing/](./Auditing/README.md) | Reentrancy mitigations, static analysis, and smart contract vulnerability audits. |

---

## 🚀 Key Architectural Paradigms

1. **SVM (Solana Virtual Machine) vs EVM (Ethereum Virtual Machine)**:
   - **EVM**: State is coupled inside smart contracts (global storage). Transactions run sequentially.
   - **SVM**: State is completely decoupled from logic. Programs are stateless (stored in Executable accounts); variables are stored in separate data accounts. Transactions run in parallel if they write to different accounts.
2. **Deterministic Execution**: Smart contracts are immutable logic pieces. They receive inputs, execute code, and perform state transitions deterministically across validator nodes.

---

> [!TIP]
> Go to **[Weeks 51–60](../weeks/)** for the step-by-step weekly Web3 study schedule, labs, and Capstone projects.
