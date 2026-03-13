# Architecture

CloakFund consists of five major layers.

Frontend  
Backend  
Blockchain  
Treasury  
Encrypted Storage

---

## System Overview

User Wallet  
↓  
Next.js Frontend  
↓  
Rust Backend API  
↓  
Stealth Address Generator  
↓  
Base Blockchain  
↓  
BitGo MPC Treasury  
↓  
Fileverse Encrypted Storage

---

## Frontend

Built with Next.js and TypeScript.

Responsibilities:

wallet connection  
ENS identity input  
payment link generation  
dashboard balance view  
receipt decryption

---

## Backend

Implemented in Rust.

Responsibilities:

stealth address generation  
blockchain deposit watcher  
treasury consolidation  
receipt encryption  
external integrations
