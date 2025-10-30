# AELITIUM Proof-Packs

Technical artifacts repository for independent validation of AELITIUM releases.
Each proof-pack is a self-contained, reproducible build with SHA256 checksums, GPG signatures, and E2E validation scripts.

## Current Release

**[v4.2.1-pilot-secure-clean](https://github.com/aelitium/aelitium-proofpacks/releases/tag/v4.2.1-pilot-secure-clean)** — Clean proof-pack (no Python cache), ready for CTO audit.

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

## Contents

Each release contains:
- Complete source code for 6 FastAPI microservices
- Security closure documentation (`SECURITY_CLOSURE.md`)
- CTO runbook with architecture details (`CTO_RUNBOOK_QUICKFIX.md`)
- E2E validation scripts and health checks
- SHA256 checksums + GPG detached signatures

## Verification

All artifacts are signed with GPG key:
```
F5DFC4559FC7F4E35F7B47362A67D0F4EBD3D532
```

Verify signatures:
```bash
gpg --verify SHA256SUMS.txt.asc SHA256SUMS.txt
```

