# Evidence and source register

**Status:** draft research observations, not evidence of implementation or product novelty. **Date:** 2026-11-03. Seven primary sources were read on 2026-11-03; source descriptions below are source-reported capabilities, not local measurements or proof of interoperability.

| Primary source | Observation and proposed reuse |
|---|---|
| [AiiDA core repository](https://github.com/aiidateam/aiida-core) | Describes computational workflow management, provenance graphs and export. Reuse its provenance rather than building a workflow engine; main branch warns of breaking changes. |
| [EasyVVUQ repository](https://github.com/UCL-CCS/EasyVVUQ) | Describes simulation VVUQ, sampling and sensitivity analysis. Reuse where appropriate; do not reproduce its analysis methods. |
| [CFDverify repository](https://github.com/ORNL/cfd-verify) | Describes CFD solution-verification methods; explicitly disclaims certification and quality guarantees. Proposed CFD adapter imports its results, not a validation finding. |
| [FMI project](https://fmi-standard.org/) | Defines a container and interface for exchanging dynamic simulation models. A container can carry model artifacts, but its presence does not prove validity. |
| [MPhys repository](https://github.com/OpenMDAO/mphys) | Describes OpenMDAO conventions for modular multiphysics analysis. Preserve integration points rather than recreating coupling. |
| [preCICE project](https://precice.org/) | Describes coupling existing solvers for partitioned multiphysics and data mapping. Reuse that coupling, not a new solver orchestrator. |
| [MuPIF project](https://www.mupif.org/) | Describes distributed simulation workflows, traceability and standardized interfaces. Its overlap requires direct comparison before implementation. |

## Claims, limitations and offline references

These are overlapping, not interchangeable systems; global novelty is unproven. The descriptions do not establish whether a combination satisfies a real exchange. No maintainers have been contacted, no partners agreed, no integration run, and no performance, scientific acceptance, or license compatibility established. P0 must compare actual versions, schemas, extension and export mechanisms, licenses and user needs, then stop if existing systems suffice. P5 requires an independent consumer.

URLs and dated descriptions here are offline-readable references, but no source snapshot is included. A future self-contained bundle should include rights-permitting copies or excerpts, original URL, retrieval date, media type, content digest, version/commit when available and licensing information. If unavailable offline, mark the reference unavailable; do not imply it was checked. Source claims remain attributed; only separately recorded local observations may be called measured facts.

Scientific acceptance requires an expert-defined protocol and independent pre-run commitment as specified in [ARCHITECTURE.md](ARCHITECTURE.md). Unassigned owners, real datasets, experiment thresholds, compatible adapter APIs, independent reviewers and an exchange partner are blockers, not presumed facts.
