# Implementation plan

**Status:** draft; no phase started. **Date:** 2026-11-03. All commands and tools below describe future work, not work performed. The tasks are sequential gates; independent maintainers and a scientific reviewer are not yet identified.

| Task | Dependencies and inputs | Output artifacts | Verification method and definition of done |
|---|---|---|---|
| **TASK-00 / P0: discovery** | None; actual producer and independent consumer, candidate CFD exchange, existing tools and [EVIDENCE.md](EVIDENCE.md). | Written exchange, permissions, overlap/capability and license matrix, decision and named owners. | TEST-01: both maintainers review the actual exchange; an attributable unmet need and reuse-vs-build decision are documented. If none, stop. |
| **TASK-01 / P1: contract** | TASK-00; agreed context and producer samples. | Versioned schemas, canonicalization and hash rules, immutable bundle format, migration and fixtures. | TEST-02–TEST-04 and TEST-18 exercise records and migrations without an evaluator; original bytes survive, unsupported majors fail, losses are reported. |
| **TASK-02 / P2: adapters** | TASK-01; licensed, runnable AiiDA and CFDverify inputs in the same CFD discipline, pinned environments. | Two adapter mappings, real run logs, raw outputs, success and failure bundles. | TEST-05–TEST-07 verify capture and identities without rule evaluation; missing/failed results remain missing/failed. |
| **TASK-03 / P3: evaluator** | TASK-01, TASK-02; expert-owned frozen protocol, rules and independent anchor. | Local CLI, deterministic evaluator, versioned protocol and explanatory reports. | TEST-08–TEST-11, TEST-19 and TEST-20 verify outcomes, stale dependencies and offline freshness; no scientific validation label. |
| **TASK-04 / P4: adversarial gate** | TASK-01–TASK-03; threat model, test fixtures and isolation target. | Attack corpus, negative-test logs, remediation or unresolved-risk register. | TEST-12–TEST-15 pass, including config substitution, leakage and hostile inputs; independent reviewer signs off remaining risks. |
| **TASK-05 / P5: interoperability** | TASK-00–TASK-04; independent consumer and chosen FMI/MPhys/preCICE/MuPIF or other agreed external workflow. | Exchange bundle, consumer reproduction, field mapping and loss report. | TEST-16 passes with independently operated import/export, offline references and recorded versions; no claim of ecosystem-wide compatibility. |
| **TASK-06 / P6: governance** | TASK-04, TASK-05; maintainers and designated reviewers. | Compatibility/release policy, correction/retraction process, support and rollback procedure. | TEST-17 passes; owners approve release and a correction/revocation drill preserves history. |

## Ordered task substeps

- **TASK-00:** (1) Obtain permission and document the actual producer-to-consumer exchange. (2) Compare candidate tools, licenses and gaps with independent maintainers. (3) Record owners and go/stop decision.
- **TASK-01:** (1) Define typed records, identities, history and snapshot fields. (2) Specify canonicalization, immutable storage and migrations. (3) Verify record-only fixtures and migration loss reports.
- **TASK-02:** (1) Pin approved AiiDA and CFDverify environments and map their complementary source records. (2) Run both adapters against actual CFD outputs and capture provenance, dependencies and raw results. (3) Retain an induced real failure and check records without an evaluator. Neither adapter is claimed to represent a distinct solver or experimental validation.
- **TASK-03:** (1) Have experts freeze a protocol and independently anchor it before scientific runs. (2) Implement CLI, rules, snapshot-aware freshness and dependency checks. (3) Exercise outcomes and offline historical/current cases with explanations.
- **TASK-04:** (1) Define hostile-input and scientific-leakage scenarios. (2) Run the attack corpus against the candidate and isolation boundary. (3) Fix findings or record and review blocking residual risks.
- **TASK-05:** (1) Agree exchange format and rights with an independent consumer. (2) Exchange and inspect actual bundles offline. (3) Compare field mappings, loss and versions and record both reviewers' findings.
- **TASK-06:** (1) Assign maintainers and publish draft compatibility and issue policies. (2) Drill correction, retraction and reader rollback. (3) Review evidence and record the release decision.

## Phase entry and exit checklists

- **P0** Entry: [ ] willing independent maintainers and real exchange identified. Exit: [ ] overlap and unmet need recorded; [ ] go/stop and owners agreed.
- **P1** Entry: [ ] P0 go decision and usable samples. Exit: [ ] record-only TEST-02–TEST-04 and TEST-18 pass; [ ] version policy reviewed. No evaluator required.
- **P2** Entry: [ ] P1 contracts stable; [ ] authorized datasets and pinned tools available. Exit: [ ] capture-only TEST-05 and TEST-06 pass on source records; [ ] TEST-07 identity fixtures pass; [ ] real failure retained. No evaluator required.
- **P3** Entry: [ ] P2 evidence and qualified expert available; [ ] protocol precommitted before relevant runs. Exit: [ ] evaluator tests including TEST-19 and TEST-20 pass; [ ] scientific approval stays human.
- **P4** Entry: [ ] P3 evaluator and threat model available. Exit: [ ] attack cases pass; [ ] unresolved risks explicitly accepted or block advancement.
- **P5** Entry: [ ] P4 gate passed and independent consumer available. Exit: [ ] offline round-trip and loss report reviewed by both sides.
- **P6** Entry: [ ] interoperable candidate and accountable maintainers. Exit: [ ] correction/retraction and compatibility drill passed; [ ] release decision recorded.

P2's real engineering runs may be exploratory; they cannot establish scientific acceptance unless the protocol for those runs was frozen beforehand. If human review, data rights, external cooperation, or reproducible tool versions are unavailable, the corresponding gate remains blocked. Rollback means stop distributing the affected release, retain immutable records, publish a correction/revocation and return to the last compatible reader; it does not erase already shared copies.
