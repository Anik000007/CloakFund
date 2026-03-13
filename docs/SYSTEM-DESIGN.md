# System Design

The CloakFund system is event-driven.

---

## Payment Flow

1 User connects wallet.

2 User enters ENS identity.

3 Frontend requests payment link.

4 Backend generates stealth address.

5 Sender transfers funds.

6 Blockchain watcher detects payment.

7 Dashboard updates aggregated balance.

8 Receipt encrypted and stored.

9 Funds optionally consolidated into treasury.

---

## Services

Stealth Generator

Generates one-time addresses.

Watcher Service

Monitors blockchain events.

Treasury Engine

Handles consolidation.

Receipt Service

Encrypts and stores payment metadata.
