# Data Flow

The data flows through the system in the following high-level sequence:
**User → Frontend → Rust API → Blockchain → Watcher → Database → UI**

---

## Payment Flow

The specific life cycle of a transaction is detailed below:

1. **Generate address**
2. **Send funds**
3. **Detect deposit**
4. **Update dashboard**
5. **Store encrypted receipt**

---

## Architecture Diagram

```mermaid
flowchart TD
    %% Main Application Entities
    A((User))
    B[Frontend]
    C{Rust API}
    D[(Blockchain)]
    E[Watcher]
    F[(Database)]
    G[UI]

    %% Main Application Flow
    A -->|Interacts| B
    B -->|API Request| C
    E -->|Logs/Updates| F
    F -->|Displays Data| G

    %% Payment Flow Subgraph
    subgraph "Payment Flow"
        direction TB
        H[Generate Address]
        I[Send Funds]
        J[Detect Deposit]
        K[Update Dashboard]
        L[Store Encrypted Receipt]
    end

    %% Correlating Main Entities with Payment Flow
    C -->|Initiates| H
    H -->|Executes Transfer| I
    I -->|On-chain Tx| D
    D -->|Monitors| E
    D -->|Emits Event| J
    J -->|Reflects Status| K
    K -->|Encrypts| L
    L -->|Persists| F
```
