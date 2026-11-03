# Model Evidence

Design specifications for an executable model-validity and evidence layer for engineering simulations.

**Status: reviewed design draft.** This repository contains specifications and implementation plans. No evidence evaluator, adapter or certification service is implemented.

## Vision

Make a model's identity, context of use, verification, calibration, independent validation and applicability constraints inspectable alongside its predictions.

The proposed first version is an offline-capable evidence bundle and rule evaluator with two complementary adapters in one discipline. It is intended to interoperate with established provenance and simulation tools rather than replace them.

## Documentation

| Document | Contents |
| --- | --- |
| [Specification](SPEC.md) | Requirements, context of use and exclusions |
| [Architecture](ARCHITECTURE.md) | Evidence records, identities, rules, freshness and trust boundaries |
| [Implementation plan](IMPLEMENTATION_PLAN.md) | Tasks, dependencies, phase gates and definitions of done |
| [Verification plan](VERIFICATION_PLAN.md) | Integrity, calibration leakage, staleness and interoperability tests |
| [Evidence](EVIDENCE.md) | Existing ecosystems, primary references and adoption blockers |

## Starting point

Begin with phase P0: identify an actual exchange between independent maintainers and verify that existing tools do not already satisfy it. A rule marked satisfied is not scientific validation or certification. Historical offline bundles cannot establish the absence of later revocations; current-status requirements must handle missing freshness evidence explicitly.

## Contributing

Proposals for evidence schemas, adapters, applicability rules and adversarial fixtures are welcome. Reference requirement/task IDs, preserve unknown states, and distinguish attributed claims from observations. Governance and external adoption are part of the design, not established partnerships.

## Licensing

An open-source release is intended; a license has not yet been selected. Public visibility alone does not grant an open-source license. Imported evidence and source artifacts retain their own rights and access restrictions.
