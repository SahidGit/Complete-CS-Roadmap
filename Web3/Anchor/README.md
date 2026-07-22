# ⚓ Anchor Framework Reference

Anchor is the premier framework for building safe and efficient smart contracts (programs) on the Solana blockchain. It abstracts away low-level account serialization, boilerplate checks, and discriminator generation using Rust macros.

---

## 🏗️ Core Architecture & Macros

### 1. Macro Decorators
- `#[program]`: Defines the module containing all program instruction logic.
- `#[derive(Accounts)]`: Annotates a struct containing all account parameters required for an instruction.
- `#[account]`: Annotates custom data structures stored on-chain, adding an 8-byte anchor discriminator.

### 2. Account Constraints (`#[account(...)]`)
- `init`: Allocates memory and initializes a new account. Requires `payer`, `space`, and `seeds`.
- `mut`: Marks an account as mutable.
- `has_one = <field>`: Enforces that an account's field matches a key passed in the instruction Context.
- `seeds = [...], bump`: Enforces Program Derived Address (PDA) derivation and bump seed validation.
- `close = <destination>`: Closes an account and sends remaining lamports to the destination.

---

## 💻 Code Example: Counter Program

```rust
use anchor_lang::prelude::*;

declare_id!("Fg6PaFpoGXkYsidMpWTK6W2BeZ7FEfcYkg476zPFsLnS");

#[program]
pub mod anchor_counter {
    use super::*;

    pub fn initialize(ctx: Context<Initialize>) -> Result<()> {
        let counter = &mut ctx.accounts.counter;
        counter.count = 0;
        counter.authority = *ctx.accounts.user.key;
        Ok(())
    }

    pub fn increment(ctx: Context<Increment>) -> Result<()> {
        let counter = &mut ctx.accounts.counter;
        counter.count += 1;
        Ok(())
    }
}

#[derive(Accounts)]
pub struct Initialize<'info> {
    #[account(
        init,
        payer = user,
        space = 8 + 8 + 32,
        seeds = [b"counter", user.key().as_ref()],
        bump
    )]
    pub counter: Account<'info, Counter>,
    #[account(mut)]
    pub user: Signer<'info>,
    pub system_program: Program<'info, System>,
}

#[derive(Accounts)]
pub struct Increment<'info> {
    #[account(
        mut,
        has_one = authority,
        seeds = [b"counter", authority.key().as_ref()],
        bump
    )]
    pub counter: Account<'info, Counter>,
    pub authority: Signer<'info>,
}

#[account]
pub struct Counter {
    pub count: u64,
    pub authority: Pubkey,
}
```

---

## 🧪 Client Testing (TypeScript)

Anchor automatically builds an **Interface Definition Language (IDL)** file and generates a TypeScript client library.

```typescript
import * as anchor from "@coral-xyz/anchor";
import { Program } from "@coral-xyz/anchor";
import { AnchorCounter } from "../target/types/anchor_counter";

describe("anchor_counter", () => {
  const provider = anchor.AnchorProvider.env();
  anchor.setProvider(provider);
  const program = anchor.workspace.AnchorCounter as Program<AnchorCounter>;

  it("Initializes counter", async () => {
    const [counterPda] = anchor.web3.PublicKey.findProgramAddressSync(
      [Buffer.from("counter"), provider.wallet.publicKey.toBuffer()],
      program.programId
    );

    await program.methods
      .initialize()
      .accounts({
        counter: counterPda,
        user: provider.wallet.publicKey,
        systemProgram: anchor.web3.SystemProgram.programId,
      })
      .rpc();
  });
});
```

---

## 🔗 Learning Links
- [Anchor Framework Official Documentation](https://www.anchor-lang.com/)
- [Solana Anchor Guide (Week 55)](../../weeks/Week-55.md)
