# Students — OPTIMUM

**Project:** OPTIMUM  
**Category:** CHIP_QUANTIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `0df84f23884f7c5b6cc76c0bdc9597edd306034f`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `fb3e048733def183545f54c361be7b3694567b68b56d71f2e66a3cf173b2c2eb`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `0df84f23884f7c5b6cc76c0bdc9597edd306034f`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `fb3e048733def183545f54c361be7b3694567b68b56d71f2e66a3cf173b2c2eb`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
