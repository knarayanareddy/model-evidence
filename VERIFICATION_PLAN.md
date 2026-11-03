# Verification plan

**Status:** draft. **Date:** 2026-11-03. Tests below are planned, not run. IDs describe future behavioral assertions, not existing test commands. The future implementer must document real command names and expected exit codes after designing the CLI; none are assumed here.

## Planned tests

| Test | Assertion and evidence |
|---|---|
| **TEST-01** | Independent maintainers inspect the real exchange and overlap matrix; record an attributable need or stop, not a simulated partner. |
| **TEST-02** | Record-only: different bytes under one semantic ID create conflict; same bytes with different context remain distinct; digest check detects altered bytes. |
| **TEST-03** | Record-only: `unknown` and justified `not_applicable` round-trip separately; missing units and conflicting dimensions, meaning or frames remain explicit. |
| **TEST-04** | Record-only: migration preserves original bytes and linkage, reports loss, rejects unknown major versions, and hashes canonical bytes reproducibly. |
| **TEST-05** | Capture-only: import claims and a deliberately observed fact; source attribution, method and uncertainty remain distinct; a claim cannot become fact through migration. |
| **TEST-06** | Capture-only: two real, pinned CFD adapter runs produce inspectable complementary source-linked records; induce and retain an actual failed/incomplete run with no invented output. No claim of two solvers or experimental validation. |
| **TEST-07** | Capture-only: use identified synthetic fixtures to record changed model, dataset, solver, adapter, dependency, environment and rule identities separately; verify references distinguish them without executable rules or stale-outcome evaluation. |
| **TEST-08** | Known true gives satisfied, known false gives unsupported, missing/stale gives indeterminate; mixed false plus unknown follows documented precedence, with explanations. |
| **TEST-09** | Inside bounds without supporting rule evidence is indeterminate; a satisfied rule cannot emit `validated`, certification, a global score or an automatic evidence fusion. |
| **TEST-10** | Freeze a complete expert protocol before a controlled run; change a threshold and recompute the local digest: independently anchored commitment still detects substitution. Missing anchor is indeterminate. |
| **TEST-11** | Export bundle, disconnect network, import/inspect/check/evaluate it; verify stable documented machine-readable outputs and non-success for malformed input. |
| **TEST-12** | Duplicate source and shared sample ancestry remain visible, not double counted; deliberate calibration/validation leakage is flagged; unknown overlap never counts as independence. |
| **TEST-13** | Alter referenced artifact, history, rules or dependency identity; detection prevents a fresh satisfied result. A wholly replaced bundle and locally replaced hashes must fail against the separately retained anchor. |
| **TEST-14** | Test path traversal, escaping symlinks, malicious archives, oversized inputs, XML entities, deserialization payloads and plugins; no unauthorized code execution, network or filesystem escape. Measure isolation on target platforms. |
| **TEST-15** | Boundary values, incompatible or ambiguous units, frame mismatches and unknown versus N/A cannot silently pass. Total pressure and static pressure with identical units/dimensions must not convert or match by units alone; valid mappings preserve the original and reference conditions. |
| **TEST-16** | Independent external consumer exchanges an actual bundle using an agreed upstream interface; compare identifiers, units, lineage, status and documented loss offline. |
| **TEST-17** | Exercise correction, revocation and supersession through export/import; reports surface affected histories. Run compatibility, reader rollback and release/retraction governance drill. |
| **TEST-18** | Record-only: snapshot identity, declared as-of timestamp, known head and versioned freshness policy survive export and migration without claiming a later current status. |
| **TEST-19** | Evaluator: change each recorded model, dataset, solver, adapter, dependency, environment or rule identity independently; affected conclusions are stale/indeterminate, never silently reused. |
| **TEST-20** | Evaluator: disconnect with a bundle at an older head, then supply an independently trusted newer revocation head. A current-required assessment is indeterminate until the newer history is reconciled; if its revocation is supplied it takes effect. Historical assessment remains explicitly labeled with its original as-of/head and never claims current status. Also test missing freshness proof and unchanged head with a policy-expired attestation. |

## Complete requirement → task → test matrix

| Requirement | Task(s) | Test(s) |
|---|---|---|
| EVID-R01 | TASK-00 | TEST-01 |
| EVID-R02 | TASK-01 | TEST-02 |
| EVID-R03 | TASK-01, TASK-03, TASK-04 | TEST-03, TEST-15 |
| EVID-R04 | TASK-01, TASK-02, TASK-04 | TEST-06, TEST-12 |
| EVID-R05 | TASK-01, TASK-02 | TEST-05, TEST-06 |
| EVID-R06 | TASK-01 | TEST-02, TEST-04 |
| EVID-R07 | TASK-01, TASK-02, TASK-03 | TEST-07, TEST-19 |
| EVID-R08 | TASK-03, TASK-04 | TEST-08, TEST-09, TEST-15 |
| EVID-R09 | TASK-03 | TEST-08, TEST-09 |
| EVID-R10 | TASK-03, TASK-04 | TEST-10, TEST-13 |
| EVID-R11 | TASK-02 | TEST-06 |
| EVID-R12 | TASK-03, TASK-05 | TEST-11, TEST-16 |
| EVID-R13 | TASK-04 | TEST-13, TEST-14 |
| EVID-R14 | TASK-01, TASK-03, TASK-06 | TEST-13, TEST-17, TEST-20 |
| EVID-R15 | TASK-05 | TEST-16 |
| EVID-R16 | TASK-06 | TEST-17 |
| EVID-R17 | TASK-01, TASK-03 | TEST-18, TEST-20 |

Tests verify implementation behavior and recorded procedure, not scientific correctness. Domain reviewers must independently approve datasets, thresholds, relevance and interpretation before any scientific claim. Preserve the exact fixtures, commands, environment, reports and reviewer decisions as future test evidence.
