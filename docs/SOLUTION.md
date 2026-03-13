# Solution

CloakFund separates identity from payment addresses.

Users maintain a public ENS identity while each payment uses a unique stealth address.

Example:

alice.eth

Payments:

Payment 1 → 0x91AF  
Payment 2 → 0x4B3C  
Payment 3 → 0xAA1D  

These addresses cannot be linked together by observers.

---

## Key Components

Identity Layer

ENS name represents the user identity.

Payment Layer

Each payment uses a stealth address.

Treasury Layer

Funds are consolidated into BitGo MPC vaults.

Data Layer

Encrypted receipts stored using Fileverse.

Automation Layer

Optional AI monitoring via HeyElsa.
