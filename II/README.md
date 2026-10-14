# Independent Insurance — OPTIMUM

**Project:** OPTIMUM  
**Category:** CHIP_QUANTIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `0df84f23884f7c5b6cc76c0bdc9597edd306034f`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `fb3e048733def183545f54c361be7b3694567b68b56d71f2e66a3cf173b2c2eb`  
**Date:** October 2026

## Why AI-specific cover matters

Deploying AI in a regulated sector creates liability surfaces that ordinary
technology cover does not reach: inference liability, audit-trail liability,
data-breach liability and IP-infringement liability.

## How this project's architecture reduces insurable risk

| Risk | Cloud AI | OPTIMUM with AIOSS |
|---|---|---|
| Audit-trail loss | high — vendor-controlled logs | low — append-only chain, verifiable offline |
| Data breach in transit | high — data transits external servers | low — no external endpoint |
| Compliance violation | high — cannot satisfy air-gap requirements | low — structural |
| IP liability | moderate | low — pinned provenance chain |

## Evidence package for an insurer

- AIOSS chain verification for head `fb3e048733def183545f54c361be7b3694567b68b56d71f2e66a3cf173b2c2eb`
- The 16-check register with per-check evidence hashes
- Framework control mapping in `BENCH.json`

## Contact

lois@0-1.gg
