# Orbit

> Non-custodial pull payments and atomic batch payroll on Stellar Soroban.

[![Stellar](https://img.shields.io/badge/Stellar-Soroban-7B68EE?style=flat-square&logo=stellar)](https://stellar.org)
[![Rust](https://img.shields.io/badge/Rust-no__std-orange?style=flat-square&logo=rust)](https://github.com/Orbit-xyz/Orbit/tree/main/contracts/soroban)
[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat-square&logo=nextdotjs)](https://github.com/Orbit-xyz/Orbit/tree/main/apps/frontend)
[![Network](https://img.shields.io/badge/network-testnet-yellow?style=flat-square)](https://stellar.expert/explorer/testnet/contract/CAZBZBUWBSQYK2RZ6WHMXVDLIQHSU5WD7ANZYL6HLNSCRUOTNYCDYQNG)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](https://github.com/Orbit-xyz/Orbit)

---

## Overview

Orbit makes recurring stablecoin billing work without custody. A subscriber signs once, sets a spending ceiling on the token (SAC allowance), and keeps their funds. The merchant can pull a fixed amount only after each billing interval has passed on the ledger.

```mermaid
sequenceDiagram
    participant User as Subscriber
    participant Orbit as OrbitContract
    participant Merchant

    User->>Orbit: approve + create_vault (signed once)
    loop every interval
        Merchant->>Orbit: pull_funds
        Orbit->>Merchant: transfer_from(user -> merchant)
    end
```

## Contract Functions

| Function | Auth | Description |
|---|---|---|
| `create_vault(user, merchant, token, amount_per_interval, interval_seconds)` | user | Records billing terms. Moves no funds. |
| `pull_funds(user, merchant)` | merchant | Pulls one cycle if `now >= last_pull + interval`. |
| `batch_disburse(sender, token, splits)` | sender | Pays many recipients in one atomic transaction. |

## Deployment

| Parameter | Value |
| :--- | :--- |
| **Orbit Contract ID** | [`CAZBZBUWBSQYK2RZ6WHMXVDLIQHSU5WD7ANZYL6HLNSCRUOTNYCDYQNG`](https://stellar.expert/explorer/testnet/contract/CAZBZBUWBSQYK2RZ6WHMXVDLIQHSU5WD7ANZYL6HLNSCRUOTNYCDYQNG) |
| **Network** | Stellar Testnet |
| **Settlement Asset** | USDC via SAC |

## Repositories

| Repo | Contents |
|---|---|
| [**Orbit**](https://github.com/Orbit-xyz/Orbit) | Soroban contract, Merchant Control Center, Merchant API, Checkout Widget SDK |
| [**orbit-docs**](https://github.com/Orbit-xyz/orbit-docs) | Developer documentation guides, contract reference, API reference |

## Links

- **Live App**: [orbit-lemon-mu.vercel.app](https://orbit-lemon-mu.vercel.app/)
- **Docs**: [orbit-docs-eta.vercel.app](https://orbit-docs-eta.vercel.app)

---

MIT. Orbit Contributors.
