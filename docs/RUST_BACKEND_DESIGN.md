# Rust Backend Design

The backend is implemented entirely in Rust.

Rust was chosen for:

memory safety  
cryptographic reliability  
concurrency performance

---

## Core Modules

API Server

Handles frontend requests.

Stealth Generator

Uses ECDH cryptography to derive one-time addresses.

Watcher Service

Listens for blockchain events using ethers-rs.

Treasury Engine

Constructs consolidation transactions.

Encryption Service

Encrypts receipts before storage.

---

## Async Runtime

Tokio is used to manage concurrent services.

Watcher and API run as separate async tasks.
