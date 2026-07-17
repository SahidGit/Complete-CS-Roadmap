# 🎯 Week 55: Anchor Framework & Smart Contracts

> **Duration:** 24 hours | **Difficulty:** 🔴 Advanced | **Prerequisites:** Week 52 (Rust) & Week 54 (Solana)

## 📌 Goal
Master the Anchor Framework (the standard Rust eDSL for Solana), write secure on-chain programs, enforce account state constraints, test DApps, and deploy to Devnet.

---

## 🎓 Learning Objectives
By the end of this week, you will:
- ✅ Understand Anchor's macro expansion patterns (`#[program]`, `#[derive(Accounts)]`)
- ✅ Define structured on-chain program accounts in Rust
- ✅ Apply security constraints (`init`, `mut`, `seeds`, `has_one`)
- ✅ Generate and compile Interface Definition Languages (IDL)
- ✅ Write local integration tests using Mocha / TypeScript
- ✅ Build, configure, and deploy Solana programs via Anchor CLI

---

## 📚 Prerequisites & Study Hours
- **Prerequisites**: Week 52 (Rust borrows and macros), Week 54 (Solana Account layouts).
- **Estimated Study Hours**: 24 hours
- **Difficulty**: 🔴 Advanced

---

## 📖 Concepts & Theory

### 1. The Anatomy of an Anchor Program
Anchor simplifies Solana program development by abstracting validation checks and serialization logic:
- `#[program]`: Defines the entry point and RPC handler instructions.
- `#[derive(Accounts)]`: Validates incoming account buffers at the runtime level.
- `Account<'info, T>`: Deserializes the raw byte data of an account into a Rust struct type `T`.

```
Transaction ──► [ Account Validation: #[derive(Accounts)] ] ──► [ Exec Instruction: #[program] ]
```

### 2. Constraints & Validation
Secure your program using Anchor's declarative constraints:
- `init`: Allocates and creates the account.
- `payer`: Specifies the account paying the rent-exemption fee.
- `space`: Sets the size of the account.
- `seeds` / `bump`: Enforces PDA validation.
- `has_one`: Verifies a field matches a target key (e.g. confirming user authority).

```rust
#[derive(Accounts)]
pub struct CreateUser<'info> {
    #[account(
        init,
        payer = authority,
        space = 8 + 32 + 8, // 8-byte discriminator + 32-byte pubkey + 8-byte integer
        seeds = [b"user-profile", authority.key().as_ref()],
        bump
    )]
    pub user_profile: Account<'info, UserProfile>,
    #[account(mut)]
    pub authority: Signer<'info>, // Must sign the tx
    pub system_program: Program<'info, System>,
}
```

---

## 💻 Daily Study Plan

### 📅 Monday: Anchor Installation & CLI
- Install the Solana CLI, Rust, and the Anchor CLI (`avm`).
- Initialize a template project: `anchor init my-program`. Study the project layout.

### 📅 Tuesday: Account Contexts & Initialization
- Study the `Accounts` context struct.
- Write instruction handlers that initialize user accounts using `init` and `payer` constraints.

### 📅 Wednesday: PDA Constraints & Custom Logic
- Learn how Anchor handles PDAs using `seeds` and `bump` constraints automatically.
- Write a program that updates user state profiles securely.

### 📅 Thursday: Testing with Anchor
- Study the auto-generated `tests/` folder.
- Write TypeScript integration tests using `@coral-xyz/anchor` to invoke program instructions.

### 📅 Friday: Projects Implementation
- Build the **Voting DApp** program and write its integration tests.

### 📅 Saturday: Deployments
- Configure `Anchor.toml` to point to Devnet.
- Build (`anchor build`) and deploy (`anchor deploy`) the program.

### 📅 Sunday: Revision & Interview Prep
- Review account size limits and the role of the 8-byte account discriminator.

---

## 🧪 Projects & Implementation Guide

### Project 1: On-Chain Voting DApp
- **Architecture**: Anchor program initializing a global config, creating individual candidate counters, and recording votes securely.
- **Folder Structure**:
  ```
  voting-dapp/
  ├── Anchor.toml
  ├── programs/voting-dapp/src/lib.rs
  └── tests/voting-dapp.ts
  ```
- **Implementation Guide**: Restrict users from voting multiple times by using a user-specific PDA acting as a voting receipt.

### Project 2: Escrow Program
- **Architecture**: A program enabling token trades between two users using an intermediate PDA vault.

### Project 3: Basic Staking App
- **Architecture**: Program storing user token deposits, computing staking rewards over time.

---

## 📝 Practice Exercises
1. Write an Anchor program that initializes a counter account and increments the counter on RPC request.
2. Write a Mocha test that verifies the counter increments correctly.
3. Apply a constraint that restricts increment actions to the creator of the account.
4. Implement a custom error handler in Rust using `#[error_code]` enums.

---

## 💼 Interview Questions & Answers
- **Q**: What is the 8-byte account discriminator in Anchor?
- **A**: The first 8 bytes of an Anchor-managed data account store a SHA-256 hash slice of the account's type name. When querying or writing to an account, Anchor verifies these 8 bytes to prevent **Account Type Confusion** attacks (ensuring a user cannot pass a token account where a profile account is expected).

---

## 📖 Official Resources
- [Anchor Language Official Documentation Book](https://www.anchor-lang.com/)
- [Solana Developers: Anchor Course Guides](https://solana.com/developers)
