# 🔷 Ethereum Development Reference

Ethereum is a decentralized, open-source blockchain featuring smart contract functionality through the Ethereum Virtual Machine (EVM).

---

## ⚙️ Core EVM Concepts

### 1. Account Types
- **Externally Owned Accounts (EOAs)**: Controlled by private keys (e.g. MetaMask wallets). Have an ETH balance and nonce. Can initiate transactions.
- **Contract Accounts**: Controlled by deployed EVM code. Possess code storage, storage trie balance, and nonce. Executed when receiving transactions from EOAs or call instructions from other contracts.

### 2. The Gas Model
- Every EVM instruction costs a fixed unit of **Gas** (e.g. `SSTORE` costs more than `ADD`).
- **Gas Fee = Base Fee + Priority Tip**.
- Prevents infinite loops and network denial of service.

### 3. Core ERC Token Standards
- **ERC-20**: Standardized interface for fungible tokens (balances, transfers, allowances).
- **ERC-721**: Standard for Non-Fungible Tokens (NFTs) representing unique assets.
- **ERC-1155**: Multi-token standard managing fungible, semi-fungible, and non-fungible assets in a single contract.

---

## 💻 Solidity Contract Example (ERC-20 Token Stub)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleToken {
    string public name = "OpenCS Token";
    string public symbol = "OCS";
    uint8 public decimals = 18;
    uint256 public totalSupply;

    mapping(address => uint256) public balanceOf;
    mapping(address => mapping(address => uint256)) public allowance;

    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);

    constructor(uint256 initialSupply) {
        totalSupply = initialSupply * 10**uint256(decimals);
        balanceOf[msg.sender] = totalSupply;
    }

    function transfer(address to, uint256 value) public returns (bool success) {
        require(balanceOf[msg.sender] >= value, "Insufficient balance");
        balanceOf[msg.sender] -= value;
        balanceOf[to] += value;
        emit Transfer(msg.sender, to, value);
        return true;
    }
}
```

---

## 🔗 Learning Links
- [Solidity Official Documentation](https://docs.soliditylang.org/)
- [Ethereum Yellow Paper](https://ethereum.github.io/yellowpaper/paper.pdf)
- [OpenZeppelin Contracts Library](https://docs.openzeppelin.com/)
