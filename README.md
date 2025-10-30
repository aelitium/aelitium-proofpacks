# AELITIUM Proof-Packs

Technical artifacts repository for **independent validation and reproducibility** of ΛELITIUM releases.
Each proof-pack is a **self-contained, deterministic build** including checksums, signatures, and validation scripts — designed for **independent technical review and audit**.

---

## What is AELITIUM?

**ΛELITIUM** transforms complex business workflows into **transparent, auditable microservices**.
It's designed for organizations that need to prove compliance, trace decisions, and ensure reproducibility across critical processes.

**Core Value:** Anyone (compliance officer, auditor, CTO) can verify *how* a decision was made, *when*, and *why* — without reverse-engineering code.

**Why Proof-Packs?**
Each release is cryptographically signed and bit-for-bit reproducible. Independent validators can rebuild the entire stack from source, verify checksums, and confirm zero tampering between development and production.

**Use Case Example:**
A fintech validates loan approvals with full audit trails. Regulators can replay any decision from 6 months ago, see the exact logic applied, and verify no retroactive changes occurred.

---

## Current Release

**[v4.2.1-pilot-secure-clean](https://github.com/aelitium/aelitium-proofpacks/releases/tag/v4.2.1-pilot-secure-clean)**
Clean proof-pack (no Python cache), reproducible TAR with fixed timestamps and sorted file order.
Ready for CTO audit.

---

## Quick Start

```bash
# Download and verify
wget https://github.com/aelitium/aelitium-proofpacks/releases/download/v4.2.1-pilot-secure-clean/proofpack-v4.2.1-pilot-secure-clean.tar.gz
wget https://github.com/aelitium/aelitium-proofpacks/releases/download/v4.2.1-pilot-secure-clean/SHA256SUMS.txt
sha256sum -c SHA256SUMS.txt

# Extract and run
tar -xzf proofpack-v4.2.1-pilot-secure-clean.tar.gz
cd proofpack-v4.2.1-pilot-secure-clean
make db-migrate && make dev
./test-e2e-curls.sh
```

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│  ΛELITIUM Core Platform (v4.2.1)                    │
└─────────────────────────────────────────────────────┘
         │
         ├── NEXUS       → Decision Logic Engine
         ├── PRAGMA      → Policy Enforcement Layer
         ├── SIGMA       → Risk Scoring & Analytics
         ├── STEWARD     → Consent & Access Management
         ├── AUDIT       → Immutable Event Logging
         └── CORE        → Orchestration & API Gateway
                │
                ▼
         PostgreSQL + SQLite
```

**Key Design Principles:**
- Structured event logging with audit trail (every decision is recorded)
- API key authentication with rate limiting and metrics
- Cryptographic proof of build integrity
- GDPR-compliant data management (export, deletion, redaction)

---

## Contents

Each release contains:
- Complete source code for **6 FastAPI microservices**
- Security closure documentation (`SECURITY_CLOSURE.md`)
- CTO runbook with architecture overview (`CTO_RUNBOOK_QUICKFIX.md`)
- E2E validation scripts and health checks
- SHA256 checksums and GPG detached signatures

---

## Verification

All artifacts are signed with the following GPG key:
```
F5DFC4559FC7F4E35F7B47362A67D0F4EBD3D532
```

To verify:
```bash
gpg --verify SHA256SUMS.txt.asc SHA256SUMS.txt
```

---

> **Purpose:** These proof-packs demonstrate ΛELITIUM's audit-grade reproducibility — a foundation for ethical automation and transparent system design.
