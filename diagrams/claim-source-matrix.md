# Diagram Claim-Source Matrix

This matrix tracks the source and authority status for each diagram node, edge,
and status cue. It is a maintenance artifact for the visual-architecture plan.

## Legend

- Authority level:
  - `canonical`: one of the canonical QMD sources.
  - `supporting`: repository supporting documentation.
  - `decision-record`: existing ADR entry.
- Status cue:
  - `Approved`, `Proposed`, `Open`, or `Advisory`.

## Three-Schema Harmonization Flow

| ID | Diagram element | Type | Claim summary | Source | Authority | Status cue | Notes |
|---|---|---|---|---|---|---|---|
| TS-01 | Questionnaire PDF | Node | Survey documentation is a drafting input. | `system_map.md` section 1 and section 4 | supporting | Advisory | Canonical architecture names documentation as a source class. |
| TS-02 | Raw survey microdata | Node | Raw microdata is profiled/processed and not directly model-default payload. | `canonical/system-architecture.qmd` trust boundaries table; `system_map.md` section 1 | canonical + supporting | Approved | Diagram uses source/input semantics only. |
| TS-03 | Raw data cleaning | Node | Cleaning standardizes structure and produces cleaned data artifacts. | `system_map.md` section 2 | supporting | Advisory | Explicitly not a methodology approval step. |
| TS-04 | Raw data metadata | Node | Metadata profile is generated from cleaned data. | `system_map.md` section 3 | supporting | Advisory | Aligned to canonical data profile concept. |
| TS-05 | Survey profile (Schema 1) | Node | Structured survey-description artifact derived from documentation extraction. | `system_map.md` section 4; `canonical/system-architecture.qmd` intake/structuring | supporting + canonical | Proposed | Label reconciles with canonical wording. |
| TS-06 | Profile reconciliation | Node | Survey profile and raw-data metadata are reconciled before downstream drafting. | `system_map.md` section 5 | supporting | Advisory | Supports orientation; not an invariant itself. |
| TS-07 | Canonical GMD schema (Schema 2) | Node | Canonical schema is binding authority for variable definitions and derivations. | `canonical/system-architecture.qmd` invariants and source authority table | canonical | Approved | Drawn as double-border canonical rule artifact. |
| TS-08 | Historical precedents | Node | Approved precedents are advisory and do not override schema authority. | `canonical/system-architecture.qmd` source authority; `system_map.md` section 8 | canonical + supporting | Advisory | Dashed contribution edge only. |
| TS-09 | Harmonization specification (Schema 3) | Node | Draft and approved harmonization specs are distinct states and versions. | `canonical/system-architecture.qmd` artifact contracts and states; `system_map.md` section 9 | canonical + supporting | Approved | Includes status tags for draft vs approved. |
| TS-10 | Harmonization drafting agent | Node | AI drafting proposes mappings and diagnostics only. | `canonical/system-architecture.qmd` purpose and invariants; `system_map.md` section 10 | canonical + supporting | Approved | Explicitly not approval authority. |
| TS-11 | Human review gate | Node | Human review approves/rejects methodology and controls production authorization. | `canonical/system-architecture.qmd` human authority and lifecycle | canonical | Approved | Central control gate in diagram. |
| TS-12 | Deterministic harmonization engine | Node | Production execution applies exact approved spec without AI inference. | `canonical/system-architecture.qmd` deterministic execution; `system_map.md` section 12 | canonical + supporting | Approved | Marked deterministic/run-only. |
| TS-13 | QA and validation | Node | QA blocks publication on failure and routes disposition. | `canonical/system-architecture.qmd` QA section; `system_map.md` section 13 | canonical + supporting | Approved | Shows loopbacks for failure. |
| TS-14 | Outputs and audit trail | Node | Publication produces outputs plus lineage and may feed curated precedents. | `canonical/system-architecture.qmd` publication/admission; `system_map.md` section 14 | canonical + supporting | Approved | Final artifact node. |
| TS-E1 | Input to profile edge | Edge | Questionnaire feeds profile extraction. | `system_map.md` mermaid flow | supporting | Advisory | |
| TS-E2 | Cleaning to metadata edge | Edge | Cleaned data feeds metadata profile. | `system_map.md` sections 2-3 | supporting | Advisory | |
| TS-E3 | Reconciliation edge | Edge | Profile and metadata feed reconciliation stage. | `system_map.md` section 5 | supporting | Advisory | |
| TS-E4 | Drafting input edges | Edge | Reconciled profile + schema + precedents feed drafting. | `system_map.md` section 10; canonical source classes | supporting + canonical | Advisory | |
| TS-E5 | Review approve edge | Edge | Approved exact version flows to deterministic execution. | `canonical/system-architecture.qmd` lifecycle | canonical | Approved | Solid edge |
| TS-E6 | Review reject edge | Edge | Rejected/edited drafts return to drafting stage. | `canonical/system-architecture.qmd` lifecycle | canonical | Approved | Solid reverse edge |
| TS-E7 | QA failure loop | Edge | QA failure loops to human disposition/revision path. | `canonical/system-architecture.qmd` QA section | canonical | Approved | Dashed edge |

## Satellite Repository Dependency Map

| ID | Diagram element | Type | Claim summary | Source | Authority | Status cue | Notes |
|---|---|---|---|---|---|---|---|
| SR-01 | GMD-harmonization-hub | Node | Hub documents architecture/governance and does not hold pipeline runtime code or survey data. | `README.md` repository boundaries; `AGENTS.md` scope | canonical for repo policy + governance file | Approved | Node text explicitly states documentation-only role. |
| SR-02 | GMD-canonical-schema | Node | Canonical schema repository is binding for variable definitions and derivation rules. | `README.md` repo map; `canonical/system-architecture.qmd` schema authority | canonical + supporting | Approved | Shown as canonical-rule color family. |
| SR-03 | harmonization-specs | Node | Holds survey-specific harmonization mappings/specifications for review and execution. | `README.md` repo map; `system_map.md` sections 9 and 11-12 | supporting + canonical alignment | Advisory | Summarized; no duplicated repository README content. |
| SR-04 | survey-scribe | Node | Extracts structured survey profile from questionnaire/docs. | `README.md` repo map; `system_map.md` section 4 | supporting | Advisory | Depicted as documentation-extraction capability. |
| SR-05 | GMD-KnowledgeBase-Pilot | Node | Historical pilot informed design but is not production pipeline. | `README.md` repo map | canonical for hub navigation | Advisory | Dashed relation styling denotes historical context only. |
| SR-06 | Open assignments block | Node | Physical repository URLs and named ownership assignments remain unresolved in canonical sources. | `README.md` repo map caveat; `canonical/system-architecture.qmd` verify note | canonical + supporting | Open | Explicitly prevents inferred URLs/owners. |
| SR-E1 | Hub to canonical-schema | Edge | Hub documents and references canonical schema authority; no runtime ownership transfer. | `README.md`; `canonical/system-architecture.qmd` ownership table | canonical + supporting | Approved | Dashed relation used for documentation/reference connection. |
| SR-E2 | Hub to harmonization-specs | Edge | Hub describes harmonization spec role and governance boundaries. | `README.md`; `system_map.md` sections 9-12 | supporting | Advisory | |
| SR-E3 | Hub to survey-scribe | Edge | Hub references extraction capability in system narrative. | `README.md`; `system_map.md` section 4 | supporting | Advisory | |
| SR-E4 | canonical-schema to harmonization-specs | Edge | Canonical rules constrain survey-specific mapping logic. | `canonical/system-architecture.qmd` schema authority + artifact contracts | canonical | Approved | Solid edge denotes verified dependency. |
| SR-E5 | survey-scribe to harmonization-specs | Edge | Extracted profile information feeds specification drafting context. | `system_map.md` sections 4-5 and 10 | supporting | Advisory | |
| SR-E6 | historical pilot to harmonization-specs | Edge | Pilot is contextual precedent for design, not live dependency. | `README.md` pilot note | canonical for navigation | Advisory | Dashed historical relation only. |

## Architecture-Decision Component Map

| ID | Diagram element | Type | Claim summary | Source | Authority | Status cue | Notes |
|---|---|---|---|---|---|---|---|
| AD-01 | ADR 0001 -> component 8 | Mapping | ADR 0001 governs the split between canonical rule store and advisory precedent store in component 8 area. | `architecture_decisions/0001_two_database_architecture.md`; `system_map.md` section 8 | decision-record + supporting | Approved | Conflict note retained: dedicated vector service remains an option in canonical infrastructure document. |
| AD-02 | ADR 0002 -> components 10/12 context | Mapping | ADR 0002 constrains drafting and deterministic derivation boundaries via atomic mapping principle. | `architecture_decisions/0002_atomic_mapping_only.md`; `system_map.md` sections 10 and 12 | decision-record + supporting | Approved | Canonical architecture labels related archived rule as proposed; displayed without resolving authority conflict. |
| AD-03 | ADR 0003 -> component 9 | Mapping | Harmonization specification is central artifact with human approval before deterministic execution. | `architecture_decisions/0003_harmonization_spec_as_central_artifact.md`; `system_map.md` section 9; canonical lifecycle | decision-record + canonical alignment | Approved | Direct governance relation. |
| AD-04 | ADR 0004 -> component 8 ingestion path | Mapping | Legacy script ingestion must pass parser -> LLM interpretation -> human validation before precedent entry. | `architecture_decisions/0004_legacy_script_ingestion_pipeline.md`; `system_map.md` section 8 | decision-record + supporting | Approved | Direct governance relation to historical base ingestion. |
| AD-05 | ADR 0005 -> hub governance context | Mapping | ADR 0005 governs repository charter scoping and does not govern harmonization methodology components directly. | `architecture_decisions/0005_compound_gpid_charter_scoping.md`; `AGENTS.md` | decision-record + governance scope | Approved for hub governance; contextual for system components | Dashed contextual mapping by design. |
| AD-06 | Conflict annotation (ADR 0001) | Status note | ADR confirms two-database pattern; canonical infrastructure still treats dedicated vector service choice as under review/proposed. | `architecture_decisions/0001_two_database_architecture.md`; `canonical/infrastructure-requirements.qmd` hybrid retrieval section | decision-record + canonical | Open | Diagram explicitly carries note rather than selecting a winner. |
| AD-07 | Conflict annotation (ADR 0002) | Status note | ADR confirms atomic mapping policy while canonical architecture labels archived atomic-only rule as proposed methodology design. | `architecture_decisions/0002_atomic_mapping_only.md`; `canonical/system-architecture.qmd` mapping granularity section | decision-record + canonical | Open | Conflict shown as status distinction only. |
