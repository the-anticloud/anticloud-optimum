# Educators — OPTIMUM

**Project:** OPTIMUM  
**Category:** CHIP_QUANTIZATION  
**Upstream:** see BENCH.json  
**Pinned commit:** `0df84f23884f7c5b6cc76c0bdc9597edd306034f`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `fb3e048733def183545f54c361be7b3694567b68b56d71f2e66a3cf173b2c2eb`  
**Date:** October 2026

## Teaching with OPTIMUM

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `fb3e048733def183545f54c361be7b3694567b68b56d71f2e66a3cf173b2c2eb` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
