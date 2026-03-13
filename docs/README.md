# CloakFund

CloakFund is a privacy-first payment and treasury infrastructure for Web3.

It allows users to receive payments through a public ENS identity while preventing observers from tracing their wallet balances and transaction history.

Instead of sending funds to a single wallet address, CloakFund generates a new stealth address for every payment. These addresses appear unrelated on-chain but are aggregated in the CloakFund dashboard.

Funds can then be consolidated into a secure BitGo MPC treasury vault. Payment receipts are encrypted and stored using Fileverse.

The frontend is built using Next.js with TypeScript (TSX), while the backend is implemented entirely in Rust.

---

## Key Features

Stealth payments  
ENS identity layer  
Secure treasury vault  
Encrypted payment receipts  
Optional AI monitoring agent  

---

## Core Idea

Users keep a single public identity:

alice.eth

But each payment goes to a different address:

Payment 1 → 0x91AF  
Payment 2 → 0x4B3C  
Payment 3 → 0xAA1D  

The blockchain cannot link them together.

---

## Tech Stack

Frontend  
Next.js (TypeScript)

Backend  
Rust (Axum + Tokio)

Blockchain  
Base Network

Integrations  
ENS  
BitGo  
Fileverse  
HeyElsa
