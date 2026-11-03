# model-evidence remediation plan

All items below are proposed work for a spec-stage repository. No current evaluator, workflow, or test command is asserted.

## Phases and dependency map

| Phase | Entry | Exit |
|---|---|---|
| P0 — discovery and rights | ME-1 owner decision open; real producer/consumer candidate identified | Real exchange, overlap matrix, and rights decision recorded |
| P1 — contract freeze | P0 complete; named scientific/data/governance owners available | Versioned schema, identity, freshness, and history rules frozen |
| P2 — adapter feasibility | P1 complete; licensed source inputs and pinned environments available | Two adapter mappings and retained failure bundle exist |
| P3 — evaluator semantics | P2 complete; pre-run protocol and independent anchor frozen | CLI/report semantics for satisfied/unsupported/indeterminate are fixed |
| P4 — adversarial and freshness gate | P3 complete; hostile-input corpus and freshness cases defined | Negative tests and stale/revocation behavior pass |
| P5 — interoperability and governance | P4 complete; independent consumer and maintainers available | Exchange, rollback, and correction policy are reviewed |

## Task detail

### ME-T1 — Discovery, exchange, and rights (ME-1, ME-4; EVID-R01, R15)
Observed paths: `README.md` 23-33, `SPEC.md` 7, 11, 25, 31-33, `EVIDENCE.md` 17-21.

1. Identify one independent producer and one independent consumer for the actual exchange.
2. Compare existing tools, overlap, and rights with the real use case; record stop/reuse or build decision.
3. Select the intended license and document which artifacts may be copied, excerpted, or bundled.
Deliverable: named exchange, rights note, and go/stop decision.
Verification: both sides confirm the same exchange and rights scope.
- [ ] Real participants are named.
- [ ] Rights for referenced artifacts are recorded.
- [ ] Reuse-vs-build decision is explicit.

### ME-T2 — Contract freeze and identity model (ME-2; EVID-R02–R07)
Observed paths: `SPEC.md` 11-18, `ARCHITECTURE.md` 11-24.

1. Freeze semantic IDs, context fields, quantity states, evidence kinds, and history events.
2. Specify canonicalization, digest rules, migration rules, and record immutability.
3. Write the ownership table for scientific, data, and governance decisions.
Deliverable: versioned contract and ownership matrix.
Verification: reviewers walk through conflicting bytes, unknown states, and immutable-history cases.
- [ ] Identity and history fields are versioned.
- [ ] Unknown vs not-applicable is explicit.
- [ ] Owner roles are named.

### ME-T3 — Adapter feasibility and retained failure (ME-1, ME-4; EVID-R04–R06, R11)
Observed paths: `IMPLEMENTATION_PLAN.md` 8-9, 18-20; `VERIFICATION_PLAN.md` 13-15.

1. Map the two proposed adapters to real source outputs and label the exact inputs.
2. Capture one successful and one failed/incomplete run as immutable records.
3. Preserve raw outputs, lineage, and status without inventing missing observations.
Deliverable: adapter mapping notes plus a retained failure bundle.
Verification: the failed run still reads as failed, and the success bundle stays distinct.
- [ ] Two adapter mappings exist.
- [ ] At least one failure is retained.
- [ ] No fabricated output is introduced.

### ME-T4 — Evaluator semantics and freshness (ME-3; EVID-R08–R09, R12, R17)
Observed paths: `ARCHITECTURE.md` 26-34, `VERIFICATION_PLAN.md` 16-19, 26-28.

1. Freeze the pre-run protocol, freshness policy, and as-of snapshot semantics.
2. Implement the CLI/report contract for satisfied, unsupported, and indeterminate.
3. Define the historical/current-required split and the exact stale/revoked behavior.
Deliverable: semantics spec for the evaluator and report output.
Verification: stale, missing, and current-required cases produce the expected status.
- [ ] Historical and current-required are distinct.
- [ ] Freshness failure yields indeterminate.
- [ ] Output is machine-readable and stable.

### ME-T5 — Adversarial gate and data protection (preventive; EVID-R13–R14)
Observed paths: `ARCHITECTURE.md` 7, 23-24, 32-34; `VERIFICATION_PLAN.md` 21-23, 25.

1. Define hostile-input cases: traversal, symlink escape, bombs, XML entities, and unsafe deserialization.
2. Define correction, revocation, and supersession records with preserved history.
3. Record the negative-test corpus and the unresolved-risk register.
Deliverable: adversarial corpus and data-protection checklist.
Verification: each negative case is rejected or flagged with the expected status.
- [ ] Hostile inputs are enumerated.
- [ ] Revocation/supersession records are preserved.
- [ ] Residual risk is documented, not hidden.

### ME-T6 — Interoperability and governance (ME-4; EVID-R10, R15–R16)
Observed paths: `EVIDENCE.md` 17-21; `IMPLEMENTATION_PLAN.md` 12-13, 22-23.

1. Choose the independent consumer and the external workflow to compare.
2. Run the round-trip exchange offline and document loss, version, and license constraints.
3. Define release ownership, correction/retraction, and rollback policy.
Deliverable: interoperability note and governance policy.
Verification: the consumer can replay the bundle, and the rollback procedure is reviewable.
- [ ] Independent consumer is chosen.
- [ ] Loss/compatibility is recorded.
- [ ] Release and rollback owners are named.

## Task dependency map

| Task | Depends on |
|---|---|
| ME-T1 | none |
| ME-T2 | ME-T1 |
| ME-T3 | ME-T1, ME-T2 |
| ME-T4 | ME-T2, ME-T3 |
| ME-T5 | ME-T4 |
| ME-T6 | ME-T1, ME-T4, ME-T5 |

## Acceptance, approval, and rollback

- [ ] The real exchange is documented before any implementation claim.
- [ ] Scientific, data, and governance owners approve the frozen protocol.
- [ ] Negative tests fail when the corresponding check is removed.
- [ ] Historical/current semantics are explicit in every report.
- [ ] Interoperability is reviewed by an independent consumer.
- [ ] Release policy includes correction, revocation, and rollback.

Rollback means stop distributing the affected bundle, preserve immutable records, and return to the last reviewed compatible reader or contract. It does not delete history or rewrite prior assessments.
