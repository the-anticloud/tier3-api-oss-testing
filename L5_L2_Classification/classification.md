# L5 Narrow / L2 General Classification — api-oss-testing
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign test framework: property-based, fuzz, and integration testing for Anticloud

## L5 Narrow
api-oss-testing specializes in sovereign test framework: property-based, fuzz, and integration testing for anticloud within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-testing is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B generates test cases: given a function signature and docstring, PAX produces pytest test cases including edge cases and security-relevant inputs.

## AIOSS Audit Relevance
Every test run (test suite hash + pass/fail counts + coverage hash + fuzz corpus hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
NIST SSDF PW.8 (security testing), ISO/IEC 29119 (software testing)
