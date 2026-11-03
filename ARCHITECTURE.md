# Architecture and proposed decisions

**Status:** draft. **Date:** 2026-11-03. No software or data bundle exists yet.

## Flow and trust boundaries

Local source artifacts → isolated adapters → immutable bundle → schema/integrity checks → rule evaluator → JSON report and human inspection. Import never executes an FMU, plugin or solver. Authorized runs occur separately under least privilege, with bounded resources, no network by default and read-only inputs. Treat adapter output as untrusted. Reject traversal, escaping symlinks, decompression bombs, external entity resolution and unsafe deserialization; do not fetch links automatically. Platform isolation requires P4 verification.

## Proposed logical schemas

The following are conceptual field contracts, not an implemented JSON Schema. All records carry `schema_version`, `record_type`, `record_id`, and canonical content digest (algorithm and canonicalization version specified by P1). An identifier for semantic meaning is not a byte digest. A record must not hash itself: calculate over a canonical payload excluding its `record_id`, digest and signatures, and specify attachment byte hashing separately.

| Record | Required content |
|---|---|
| Model | `semantic_id: {namespace, name, version}`, artifact digest(s), source, and revision relationship; equal semantic IDs with different bytes are conflicts until reviewed, not duplicates. |
| Context | identified intended decision, domain, physical configuration, assumptions, operating conditions and target quantities; typed range endpoints and units are explicit. |
| Quantity | semantic identifier, role, value or interval, unit, dimension, coordinate frame and uncertainty; each potentially missing field is `{state: known, value: ...}`, `{state: unknown, reason: ...}`, or `{state: not_applicable, reason: ...}`. Null and omission do not imply either state. |
| Evidence | kind `calibration`, `verification`, `validation`, or `other`; model/context IDs, source artifact digest, dataset/sample IDs, lineage edges and roles, method, time, outcome and limitations; independent validation is a claim supported by lineage and expert review, never a parser inference. |
| Observation | distinguish `source_claim` (attribution and original reference) from `measured_fact` (instrument/method, observer, time, uncertainty, raw data ID). Imported assertions remain claims unless a local measurement actually occurs. |
| Run | immutable references to model, input, dataset, adapter, evaluator, solver, dependency lock, environment/platform, raw output, start/end, status and errors. Unknown dependencies are recorded, never silently presumed equal. |
| Rule/report | rule ID/version, context, typed predicates, referenced evidence and protocol commitment; report includes per-rule outcome, reason, input IDs, stale/conflict flags, evaluator version, assessment mode, as-of time, snapshot/head identity and freshness policy. |
| History | append-only correction/revocation/supersession event, target and replacement IDs, reason, actor, time; retain previous bytes and label the known head and its as-of time, not an unverified current head. |

Lineage is a directed graph of artifact and sample identities with explicit `derived_from`, `calibrated_with`, `validated_against`, and `reuses` edges. Detect identical identities and known overlaps; unknown sample identity means independence is indeterminate. A run's declared dependencies include platform and relevant tool, solver, library and configuration versions/digests, data, protocol and rule IDs. A changed or unverifiable dependency marks affected conclusions stale; reevaluation requires compatible new evidence or a documented expert determination, never silent carry-forward. Historical reports remain reproducible as historical records.

## Evaluator and frozen protocol

Rules are deterministic and side-effect free. `satisfied`: every required predicate has known, compatible inputs current for the declared assessment scope and evaluates true. `unsupported`: a known, compatible, scope-current input contradicts a required predicate or establishes a declared exclusion. `indeterminate`: a required input, independence, status, unit mapping, trusted commitment or dependency is unknown, missing, stale, conflicted, revoked or unverifiable. For multiple required predicates, indeterminate takes precedence over unsupported if any required input is indeterminate; otherwise any false gives unsupported; all true gives satisfied. Rules report individual outcomes and do not generate an overall scientific verdict. An N/A field is admissible only if the rule explicitly permits it with a reason; otherwise indeterminate. Valid conversion requires documented compatible dimensions, quantity meaning, reference conditions and frame transformation, preserving originals and mapping. Same units alone are insufficient: total and static pressure are different quantities. A known semantic mismatch blocks conversion; unknown mapping is indeterminate.

### Offline assessment freshness

Each assessment specifies `historical` or `current_required`, an as-of timestamp, snapshot digest, known revocation head and a versioned freshness policy naming trusted authority, verification method, reference time and maximum acceptable age. An offline bundle proves only the included history up to its declared snapshot/head; it cannot establish that no later remote revocation exists. `historical` evaluates the selected snapshot and permanently labels the report as-of that snapshot, never as current. `current_required` needs independently verified authority/head freshness meeting the policy and no independently known newer head; without that verification, affected rules are `indeterminate`. If a newer trusted head is known but its events are unavailable, status is indeterminate until reconciled; if the revocation is available, apply it. An authority's guarantees and clock assumptions limit any current-status claim; a self-declared timestamp or bundled head alone is not proof of freshness.

A future pre-run protocol must contain named scientific decision owners and reviewers; exact model and context; quantities, units, reference data and sample identities; calibration/validation separation and independence checks; measurement and uncertainty methods; numerical metrics, thresholds and boundary semantics; exclusions, missing-data treatment, analysis plan and stop/decision rules. Include protocol/rule/schema versions, tooling and dataset commitments, approvals and time. Canonical bytes and threshold configuration are hashed together, and the digest is independently retained by a trusted reviewer or append-only external record **before** data access/run. The run and report reference that commitment. Recomputing a hash stored alongside modified thresholds alone is insufficient. Without a verifiable pre-run anchor, precommitment is indeterminate. Signatures can authenticate an approver if keys and revocations are independently managed, but do not establish scientific merit or trustworthy time by themselves.

## Decisions proposed, not accepted

| Decision | Alternative and cost | Revisit trigger |
|---|---|---|
| Portable local, content-addressed bundle; optional offline reference copies with license/rights metadata. | Central service gives collaboration but adds availability and governance dependencies. | Independent exchange requires shared access or scale beyond bundles. |
| Explicit typed rules and three outcomes, no scientific aggregate. | Free-form scripts or a single score obscure assumptions and are unsafe to execute or compare. | Maintainers demonstrate a constrained, reviewable rule expression cannot express a real use case. |
| Adapt existing outputs; preserve native references. | Rebuild workflow, UQ, or coupling engines duplicates established systems. | P0/P5 show existing supported interfaces cannot carry necessary provenance. |
| Immutable events plus explicit migration. | In-place edits are simpler but erase the audit trail. | Measured storage/retention burden requires a reviewed archival scheme. |

FMI, MPhys, preCICE and MuPIF remain exchange/coupling ecosystems to interoperate with, not code to reproduce. AiiDA, EasyVVUQ and CFDverify remain provenance/VVUQ tools to reuse. P0 chooses a real interoperability target and P5 proves the exchange; none is asserted compatible here.
