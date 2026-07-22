# 🏛️ Decentralized Autonomous Organizations (DAOs) Reference

DAOs are blockchain-governed organizations managed by smart contracts, transparent rules, and tokenized voting without centralized management.

---

## ⚙️ Core DAO Components

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│ Governance Token│ ────► │ Voting & Proposal│ ────► │  Timelock & Exec│
│  (Token/SPL)    │       │     Contract    │       │    Treasury     │
└─────────────────┘       └─────────────────┘       └─────────────────┘
```

1. **Governance Tokens**: Minted tokens granting voting power proportional to token holdings or delegated stakes.
2. **Proposal Engine**: On-chain mechanism to create proposals, record user votes (For/Against/Abstain), and compute quorum.
3. **Timelock Controller**: Introduces execution delays to allow community members to review or exit before approved changes execute on-chain.
4. **Multisig Treasuries**: Shared vaults requiring multiple cryptographic approvals (e.g. 3-of-5 signers) to authorize payouts (Squads on Solana, Gnosis Safe on EVM).

---

## 🛡️ Governance Attack Vectors & Defense

- **Flash Loan Voting Attacks**: Attackers borrow governance tokens in a single transaction to pass malicious proposals.
  - *Defense*: Snapshot block weights or checkpointing token balances at past block numbers.
- **Low Quorum Exploits**: Low participation allowing malicious minority passes.
  - *Defense*: Minimum quorum thresholds and mandatory timelocks.

---

## 🔗 Learning Links
- [Solana Realms Governance](https://app.realms.today/)
- [OpenZeppelin Governor Contracts](https://docs.openzeppelin.com/contracts/4.x/governance)
- [Squads Protocol Documentation](https://squads.so/)
