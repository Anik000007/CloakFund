# Data Flow

This document details the high-level architecture and data flow for the CloakFund platform.

## High-Level Architecture

The core data flow moves from the user interfaces down to the blockchain, while a dedicated watcher service observes the blockchain to update the application state asynchronously.

```mermaid
flowchart TD
    User([User]) -->|Interacts with| Frontend[Frontend UI]
    Frontend -->|API Requests| API[Rust API Server]
    API -->|Tx / Queries| Blockchain[(Blockchain Network)]

    Watcher[Blockchain Watcher] -->|Monitors Blocks & Events| Blockchain
    Watcher -->|Saves State| DB[(Database)]
    API -->|Reads State| DB

    subgraph CloakFund System
        Frontend
        API
        Watcher
        DB
    end
```

---

## Payment Flow

The payment flow involves setting up an isolated deposit address and observing it for incoming funds

### 1. Address Generation

- **Frontend:** Requests a new, unique deposit address for a specific user or campaign.
- **Rust API:** Securely generates the receiving address and tracks the intent in the database.

### 2. Transaction & Observation

- **User:** Sends crypto funds from their personal wallet to the generated deposit address.
- **Watcher:** Continuously scans the blockchain for new blocks and transactions to the generated addresses.

### 3. Settlement

- **Watcher:** Once a valid deposit is detected, it updates the transaction state and stores an encrypted receipt.
- **Frontend:** Recieves the updated status from the Backend API and updates the UI.

```mermaid
sequenceDiagram
    actor User
    participant UI as Frontend
    participant API as Rust API
    participant DB as Database
    participant Chain as Blockchain
    participant Watcher as Blockchain Watcher

    User->>UI: Initiates payment/donation
    UI->>API: Request new payment address
    API->>API: Generate unique address
    API->>DB: Store pending payment intent
    API-->>UI: Return payment address & payment details
    UI-->>User: Display QR code / address

    User->>Chain: Send crypto funds to address

    loop Continuous Monitoring
        Watcher->>Chain: Monitor for deposits
    end

    Chain-->>Watcher: Deposit detected (confirmations met)
    Watcher->>DB: Update transaction status to complete
    Watcher->>DB: Store encrypted receipt

    UI->>API: Check payment status
    API->>DB: Read updated status
    DB-->>API: Status Complete
    API-->>UI: Return success & receipt
    UI-->>User: Display payment success
```
