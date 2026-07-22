# 🔮 Blockchain Oracles Reference

Blockchains are deterministic closed loops unable to natively initiate external HTTP calls or fetch real-world data (prices, weather, sports outcomes). Oracles bridge off-chain data feeds into on-chain smart contract environments.

---

## ⚡ The Oracle Problem & Models

```
[ External API / Exchange ] ──► [ Off-Chain Nodes / Aggregators ] ──► [ Oracle Contract ] ──► [ Your DApp ]
```

### 1. Push Oracle Model (e.g. Chainlink)
- Decentralized node network continuously monitors external asset prices and writes price updates to on-chain price feed contracts whenever prices deviation threshold triggers.

### 2. Pull Oracle Model (e.g. Pyth Network)
- Off-chain publishers continuously post signed price updates to an off-chain network (Pythnet).
- When a user submits a transaction requiring a price check, the user **pulls** the latest price update payload and submits it in the same transaction to be verified on-chain.

---

## 📊 Pyth Solana Example (Rust Anchor)

```rust
use anchor_lang::prelude::*;
use pyth_sdk_solana::load_price_feed_from_account_info;

pub fn process_swap(ctx: Context<SwapContext>) -> Result<()> {
    let price_account_info = &ctx.accounts.pyth_price_feed;
    let price_feed = load_price_feed_from_account_info(price_account_info).unwrap();
    
    // Get current price with max 60 seconds age check
    let current_price = price_feed.get_price_no_older_than(
        Clock::get()?.unix_timestamp,
        60
    ).ok_or(ErrorCode::StalePrice)?;

    msg!("Asset price: {} * 10^{}", current_price.price, current_price.expo);
    Ok(())
}
```

---

## 🔗 Learning Links
- [Pyth Network Documentation](https://docs.pyth.network/)
- [Chainlink Developer Docs](https://docs.chain.link/)
- [DeFi Protocol Architecture (Week 57)](../../weeks/Week-57.md)
