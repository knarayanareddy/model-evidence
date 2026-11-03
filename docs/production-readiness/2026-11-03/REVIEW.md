# model-evidence review

## Scope and verdict

Stage: **spec** / documentation-only. Pinned source revision: `dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55`. Sampled sources: local `README.md` 1-33 and remote pinned reads of `SPEC.md` 1-33, `ARCHITECTURE.md` 1-35, `IMPLEMENTATION_PLAN.md` 1-35, `VERIFICATION_PLAN.md` 1-35, and `EVIDENCE.md` 1-21. Runtime was **not run**. The snapshot tree is complete and contains only the six documentation files; no application code, workflows, or generated artifacts were present in the reviewed tree.

## Architecture and product boundary

The repo is a design package, not a runnable product. README says the repository contains specifications and implementation plans and that no evaluator, adapter, or certification service is implemented ([README:3-5](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/README.md#L3-L5)). The intended first version is an offline evidence bundle and rule evaluator, not a solver, workflow manager, certification authority, or scientific judge ([SPEC:7](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/SPEC.md#L7-L7)). Architecture keeps import isolated and untrusted, then evaluates rules into a JSON report for human inspection ([ARCHITECTURE:7](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/ARCHITECTURE.md#L7-L7)). The explicit external ecosystems to compare against are AiiDA, EasyVVUQ, CFDverify, FMI, MPhys, preCICE, and MuPIF ([EVIDENCE:7-13](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/EVIDENCE.md#L7-L13)). No nested app boundary is evidenced.

## Findings ledger

| ID | Severity | Class | Evidence | Impact | Recommended correction |
|---|---|---|---|---|---|
| ME-1 | High | owner decision | [README:23-25](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/README.md#L23-L25), [SPEC:7,11](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/SPEC.md#L7-L11), [IMPLEMENTATION_PLAN:7](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/IMPLEMENTATION_PLAN.md#L7-L7) | The required “actual exchange” and reuse-vs-build decision are not yet evidenced; the current repo is still a proposal. | Name an independent producer/consumer pair, document the real exchange, and record the stop/reuse decision before any implementation claim. |
| ME-2 | High | owner decision | [ARCHITECTURE:34](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/ARCHITECTURE.md#L34-L34), [SPEC:20,31](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/SPEC.md#L20-L31) | Scientific/data/governance ownership, thresholds, exclusions, and decision procedure are still deferred to future humans. | Assign named scientific, data, and governance owners; freeze the pre-run protocol, thresholds, and decision procedure before any run or claim. |
| ME-3 | Medium | unverified risk | [ARCHITECTURE:32,34](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/ARCHITECTURE.md#L32-L34), [SPEC:27,31](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/SPEC.md#L27-L31) | A current-status claim could overstate what an offline bundle can prove; freshness and revocation must stay explicit. | Label assessments historical vs current-required, require verified head freshness for current claims, and return indeterminate when freshness is unproven. |
| ME-4 | Medium | owner decision | [README:31-33](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/README.md#L31-L33), [EVIDENCE:17-21](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/EVIDENCE.md#L17-L21) | License, rights-permitting excerpts, and external interoperability are unresolved, so compatibility claims would be premature. | Select a license, secure rights for offline excerpts or copies, and verify an independent consumer before interoperability claims. |

## Five disciplines and owner questions

- **Code:** N/A. No executable source tree is present; only documentation and future-task descriptions are evidenced.
- **Automation:** N/A for now. No workflow, hook, or CI file is in the reviewed tree; verification is only planned in `VERIFICATION_PLAN.md`.
- **DevOps/operations:** partially applicable. Release ownership, rollback, freshness, and correction policy are explicitly planned, but no deployment target or operational drill exists yet ([ARCHITECTURE:22,32-34](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/ARCHITECTURE.md#L22-L22), [SPEC:24-27](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/SPEC.md#L24-L27)).
- **Security:** applicable. The docs already require hostile-input handling, revocation handling, explicit stale/indeterminate states, and preservation of source attribution vs local facts ([ARCHITECTURE:7,18-24,28,32-34](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/ARCHITECTURE.md#L7-L34), [SPEC:13-17,23-27](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/SPEC.md#L13-L27)).
- **UX/accessibility:** N/A. No user interface is shipped. If a CLI or report UI lands later, it must distinguish unknown, not-applicable, stale, and indeterminate states clearly ([ARCHITECTURE:28,32](https://github.com/knarayanareddy/model-evidence/blob/dd1d1ef74e6738f490dc577cd9fb93ff7d5b1c55/ARCHITECTURE.md#L28-L32)).

## Production blockers and owner questions

1. Which independent producer/consumer pair is the real P0 exchange?
2. Who owns scientific, data, and governance decisions for thresholds, exclusions, and approval?
3. Is the first deliverable historical-only, or does the owner require current-required freshness semantics?
4. What license and rights cover the offline references and excerpts?
5. Is an external consumer already available for interoperability testing, or is that still a blocker?

## Evidence and limitations

Inspected: local `README.md` 1-33; remote pinned reads of `SPEC.md` 1-33, `ARCHITECTURE.md` 1-35, `IMPLEMENTATION_PLAN.md` 1-35, `VERIFICATION_PLAN.md` 1-35, and `EVIDENCE.md` 1-21. Not inspected: runtime execution, tests, hidden files outside the snapshot, local GitHub Actions state, deployment targets, and any unpublished branch/PR state. No code or package install was run. [Plan](REMEDIATION_PLAN.md).
