# Orbit Protocol

Non-Custodial Pull Payments and Atomic Batch Payroll Engine on Stellar Soroban

---

## Overview

Orbit Protocol is decentralized, non-custodial payments infrastructure built natively on **Stellar Soroban**. It makes recurring subscription charges and coordinated payroll possible without custodial escrow or manual wallet approval for every billing cycle.

Through Soroban-native **Allowance Vaults**, Orbit separates payment authorization from fund custody. Subscribers grant merchants a time-bounded, spending-capped allowance while keeping full custody of their assets. Merchants can pull approved USDC only when the interval has elapsed and the amount is within the approved cap.

## Core Components

- **Allowance Vaults**: non-custodial recurring payments enforced by ledger timestamps and spending caps.
- **Batch Payroll Engine**: atomic payouts to many recipient wallets in a single transaction. If any transfer fails, the whole batch reverts.
- **Merchant Control Center**: subscription plans, subscriber management, payment links, and settlement treasury (Next.js 15).
- **Hosted Checkout and Widget SDK**: `/pay/[id]` checkout pages and the embeddable `<OrbitCheckout />` React component with Freighter support.
- **Developer Portal**: API keys, HMAC-signed webhooks, and integration docs.

## Deployment

| Parameter | Value |
| :--- | :--- |
| **Orbit Contract ID** | [`CAZBZBUWBSQYK2RZ6WHMXVDLIQHSU5WD7ANZYL6HLNSCRUOTNYCDYQNG`](https://stellar.expert/explorer/testnet/contract/CAZBZBUWBSQYK2RZ6WHMXVDLIQHSU5WD7ANZYL6HLNSCRUOTNYCDYQNG) |
| **Settlement Asset** | Native Testnet USDC |
| **Network** | Stellar Testnet |

## Repositories

- [**Orbit**](https://github.com/Orbit-xyz/Orbit): Soroban contracts, Merchant Control Center, and Checkout Widget SDK.

---

Licensed under the MIT License.
