# Model-evidence layer: specification

**Status:** draft; documentation only. **Date:** 2026-11-03. **Owner:** unassigned.

## Problem and boundary

Hypothesis: maintainers exchanging aerodynamic CFD models may lack a portable way to inspect context-specific evidence alongside model artifacts. No unmet exchange has yet been demonstrated. P0 must document an actual exchange with independent maintainers and compare existing capabilities before proceeding. The proposed standalone local executable is an evidence reader and rule evaluator, not a solver, workflow manager, certification authority, or scientific judge. Two complementary adapters in this one discipline are proposed: AiiDA provenance export and CFDverify solution-verification output; they do not imply two solver implementations or experimental validation. Actual versions, APIs, datasets and feasibility remain P0/P2 decisions. They must ingest real outputs, not invented formats.

## Requirements

- **EVID-R01** — Before implementation, independent maintainers document an actual producer/consumer exchange, unmet need, and overlap; stop or reuse existing tools if no gap remains.
- **EVID-R02** — Identify model by semantic namespace/name/version plus content digest, and bind it to an explicit context of use, purpose, assumptions and decision scope; changes must not silently retain an old identity.
- **EVID-R03** — Record quantities, dimensions, units, coordinate/reference frame and conditions; unknown differs from not-applicable, with reasons. Conversion requires compatible physical meaning as well as dimensions; incompatible units, frames or semantics must never silently convert.
- **EVID-R04** — Separate calibration, numerical verification, independent validation and other evidence; record datasets and lineage. Common ancestry, overlapping samples or unknown independence are visible and not auto-fused.
- **EVID-R05** — Preserve attributed source claims separately from locally observed facts, with source, method, time, artifact digests and uncertainty where applicable; no claim is upgraded to observation merely by import.
- **EVID-R06** — Use versioned, immutable machine-readable records and migrations with original bytes retained, explicit loss reports and reproducible identity; reject unknown major versions.
- **EVID-R07** — Bind evidence and decisions to model, dataset, adapter, evaluator, dependency and execution-environment identities; changes or missing identity trigger explicit stale/indeterminate handling, not silent reuse.
- **EVID-R08** — Support explicit, versioned, context-of-use applicability rules with traceable inputs and reasons; being within declared bounds alone never establishes scientific validity.
- **EVID-R09** — Each rule returns `satisfied`, `unsupported`, or `indeterminate` under the semantics in [ARCHITECTURE.md](ARCHITECTURE.md); no rules-only authoritative validated label, universal trust score or automatic certification.
- **EVID-R10** — Before scientific runs, freeze a human-approved acceptance protocol and comparison thresholds, datasets, exclusions, independence and decision procedure, bound to an independently retained commitment; post-run edits invalidate the precommitment.
- **EVID-R11** — Two actual adapter runs, including a failed or incomplete run, preserve raw outputs, lineage and status without fabricating missing observations; failures cannot become satisfied evidence.
- **EVID-R12** — Provide an offline-capable local CLI for import, inspect, integrity check and evaluation, returning machine-readable explanations and stable documented exit behavior; no network needed for an exported bundle.
- **EVID-R13** — Treat archives, plugins, executable model components and paths as hostile; bounded parsing, isolation and explicit consent precede execution. Hashes detect differences against trusted commitments, not scientific truth.
- **EVID-R14** — Append corrections, revocations and supersessions with reasons, actor, time and affected identities; preserve old records and surface status during evaluation and offline export.
- **EVID-R15** — Demonstrate actual external interoperability with a separately maintained consumer and document round-trip loss and compatibility, including upstream license and version constraints.
- **EVID-R16** — Establish release ownership, compatibility, issue reporting, correction/retraction and rollback policy; human experts independently approve scientific interpretation and applicability.
- **EVID-R17** — Label each assessment with an as-of timestamp, independently known revocation head and freshness policy; when current status is required but cannot be verified, return `indeterminate`, while retaining explicitly historical assessments.

## Acceptance and exclusions

Every requirement maps to tasks and observable tests in [VERIFICATION_PLAN.md](VERIFICATION_PLAN.md). Scientific thresholds, validation datasets, review authority, and exact context must be selected by qualified humans before running; no placeholder is an acceptance fact. Output `satisfied` only means a particular rule's conditions were met against identified evidence. It is neither a finding of model validity nor permission to use a model. No correlated evidence is automatically aggregated. Signatures, if used, are authenticity controls, not scientific proof. Planned commands and all implementation/testing are unrun.

See [ARCHITECTURE.md](ARCHITECTURE.md), [IMPLEMENTATION_PLAN.md](IMPLEMENTATION_PLAN.md), and [EVIDENCE.md](EVIDENCE.md).
