# Cryptography

CloakFund uses elliptic curve cryptography to generate stealth addresses.

---

## Stealth Address Generation

1 Sender generates ephemeral key.

2 Shared secret derived using ECDH.

3 Secret used to derive new payment address.

This ensures each payment uses a unique address.

---

## Encryption

Payment receipts are encrypted using authenticated symmetric encryption.

Recommended algorithms:

ChaCha20-Poly1305  
AES-GCM

---

## Key Principles

no private keys stored server-side  
ephemeral keys destroyed after use  
all encryption performed locally
