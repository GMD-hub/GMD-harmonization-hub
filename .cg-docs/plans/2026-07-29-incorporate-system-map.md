---
date: 2026-07-29
title: "Incorporate the system components map into the hub"
status: completed
scope: "Standard"
brainstorm: null
language: "other"
estimated-effort: "medium"
deviation-policy: "ask"
tags: [documentation, system-map, glossary, open-questions, navigation]
phases: 2
execution-report: ".cg-docs/work-reports/2026-07-29-incorporate-system-map.md"
completed-phases: [1, 2]
completed-date: 2026-07-29
---

# Plan: Incorporate the system components map into the hub

## Objective

Incorporate the supplied GMD system components map into the hub's supporting
architecture documentation while keeping the repository's authority boundaries
explicit. Separate reusable terminology and unresolved decisions into their
established destinations, and update navigation and project deliverables to
make the new map discoverable.

## Context

The hub is a documentation and proposal repository; it contains no pipeline
code or survey data. `system_map.md` is a new supporting document supplied for
this work. `README.md` identifies only the canonical Quarto documents as
substantive sources of truth, so the map must be presented as explanatory
supporting material rather than as a competing architecture authority.

The source map describes inputs, profiling, reconciliation, schemas, country
parameters, historical precedents, drafting, review, deterministic execution,
quality assurance, outputs, and their relationships. Existing glossary entries
already cover several of these concepts, and `open_questions.md` already tracks
related infrastructure, country-parameter, legacy-script, and education-rule
uncertainties. The implementation should extend those files only where the map
adds a genuinely missing term or question.

## Requirements

| ID | Requirement | Source |
|---|---|---|
| R1 | Preserve the system components inventory, data flow, composition, and change-frequency information in `system_map.md` as supporting documentation. | User-provided `system_map.md` |
| R2 | Route reusable project terminology to `glossary_and_questions/glossary.md` without duplicating existing definitions or asserting canonical methodology. | `AGENTS.md`; user request |
| R3 | Route unresolved choices and uncertainties to `glossary_and_questions/open_questions.md`, keeping them explicitly open and avoiding invented infrastructure or ownership facts. | `AGENTS.md`; user-provided map |
| R4 | Update `README.md` so readers can find and understand the status of `system_map.md`. | User request; README maintenance policy |
| R5 | Update `compound-gpid.md` so the project deliverables/current focus account for the system map where appropriate. | User request |
| R6 | Avoid modifying architecture decisions, canonical Quarto documents, roadmap data, pipeline code, or survey data. | `AGENTS.md`; project charter |
| R7 | Validate links, whitespace, required files, and the final documentation diff. | Approved completion contract |

## Implementation Steps

## Phase 1: Content integration

### 1. Reconcile the supplied map with hub authority

- **Requirements**: R1, R2, R3, R6
- **Files**: `system_map.md`, `canonical/system-architecture.qmd`, `architecture_decisions/`, `AGENTS.md`
- **Details**: Compare the map's component boundaries and flow with the
  canonical architecture and existing decisions. Preserve the map's useful
  explanatory inventory, but mark or soften any statement that is proposed,
  advisory, or still unresolved. Do not restate statistical harmonization
  rules owned by the canonical schema repository.
- **Test Scenarios**: the map agrees with existing authority; a potentially
  conflicting ownership or infrastructure statement is left open or surfaced;
  no architecture decision entry is edited.
- **Tests**: targeted text search for authority terms and review of the changed
  documentation diff.
- **Acceptance criteria**: `system_map.md` is a coherent supporting map and
  contains no unverified implementation commitment presented as fact.

### 2. Complete the system map document

- **Requirements**: R1, R6
- **Files**: `system_map.md`
- **Details**: Keep the component sections, Mermaid relationship diagram, and
  quick-reference table. Add concise status or authority framing where needed
  so readers understand that the map explains the system and does not override
  canonical documents. Link to the glossary and architecture decisions using
  repository-relative Markdown links where useful.
- **Test Scenarios**: all numbered components remain represented; Mermaid
  syntax remains intact; supporting links point to existing files.
- **Tests**: `test -f system_map.md`; targeted link/file checks; `git diff --check`.
- **Acceptance criteria**: the new file is readable on its own, navigable from
  the hub, and clearly subordinate to the canonical architecture documents.

### 3. Extract missing terminology and open questions

- **Requirements**: R2, R3, R6
- **Files**: `glossary_and_questions/glossary.md`, `glossary_and_questions/open_questions.md`
- **Details**: Add only terms introduced by the map that are not already
  defined, such as raw data profile, profile reconciliation, harmonization
  engine, human review dashboard, or audit trail, using concise explanatory
  definitions. Add only genuinely unresolved map-derived questions, including
  the raw-data-cleaning automation boundary if it is not already present.
  Reuse existing questions rather than creating duplicates, and preserve the
  rule that resolved questions move to a dated architecture decision.
- **Test Scenarios**: an existing term is not duplicated; an unresolved choice
  remains explicitly open; no question is phrased as an approved design.
- **Tests**: targeted searches for duplicate headings/terms and review of the
  resulting glossary and question entries.
- **Acceptance criteria**: readers can find definitions and unresolved items
  in the established destinations, with no accidental methodology decisions.

## Phase 2: Navigation and verification

### 4. Update repository navigation and project metadata

- **Requirements**: R4, R5
- **Files**: `README.md`, `compound-gpid.md`
- **Details**: Add `system_map.md` to the repository layout or supporting
  documentation navigation, explain its noncanonical status, and include it
  among the hub's relevant deliverables/current-focus references without
  duplicating its body. Preserve the distinction between canonical documents,
  supporting documentation, and Compound GPID workflow metadata.
- **Test Scenarios**: a new reader can reach the map from README; the charter
  names the map's explanatory role; no canonical-source hierarchy is changed.
- **Tests**: targeted Markdown link checks and review of changed sections.
- **Acceptance criteria**: both files point to or describe the new map in a
  concise, consistent way.

### 5. Validate the integrated documentation set

- **Requirements**: R1, R2, R3, R4, R5, R6, R7
- **Files**: `system_map.md`, `glossary_and_questions/glossary.md`, `glossary_and_questions/open_questions.md`, `README.md`, `compound-gpid.md`
- **Details**: Check that every new link resolves, required repository files
  remain present, no unrelated files changed, and the diff contains no
  whitespace errors. Review the final document set for duplicated definitions,
  unresolved questions presented as decisions, and accidental pipeline code or
  data content.
- **Test Scenarios**: happy path with all files present; broken-link or missing
  file detection; a diff containing only the planned documentation changes.
- **Tests**: `git diff --check`; `test -f system_map.md`; targeted shell checks
  for referenced paths; `git diff --stat`; final `git status --short`.
- **Acceptance criteria**: all checks pass and the resulting diff is limited to
  the approved documentation scope.

## Testing Strategy

Use documentation-focused validation rather than runtime tests:

- compare the map against the canonical architecture and `AGENTS.md` authority
  boundaries;
- search for duplicate glossary definitions and repeated open questions;
- verify all repository-relative links added by the change resolve;
- run `git diff --check` and inspect the final diff/status for scope control.

## Documentation Checklist

- [ ] `system_map.md` is clearly identified as supporting, noncanonical documentation.
- [ ] Component descriptions, relationships, and composition table are retained.
- [ ] Missing terminology is added to the shared glossary once.
- [ ] Unresolved map-derived questions are added to the shared question log once.
- [ ] `README.md` navigation and repository layout include the map.
- [ ] `compound-gpid.md` reflects the map's role in the hub deliverables/current focus.
- [ ] No architecture decision, canonical Quarto source, code, data, or roadmap entry was changed.

## Risks & Mitigations

| Risk | Mitigation |
|---|---|
| Supporting map is mistaken for a canonical architecture source. | Add explicit status framing and link back to the canonical documents and README authority hierarchy. |
| Existing glossary terms or questions are duplicated. | Search current headings and entries before adding new content; merge into existing entries where appropriate. |
| Proposed infrastructure or ownership details are presented as settled. | Preserve `Open` or `Proposed` status and defer unknowns to `open_questions.md`. |
| The map accidentally restates methodology owned by the canonical schema repository. | Keep methodology references at the system-boundary level and link to the satellite source of truth. |
| README and charter become inconsistent about document roles. | Update both from the same concise description and verify their authority language together. |
| Untracked user-supplied `system_map.md` is omitted from the final change. | Include a required-file check and inspect `git status --short` before completion. |

## Out of Scope

- Editing existing architecture decision entries.
- Changing `canonical/system-architecture.qmd` or
  `canonical/infrastructure-requirements.qmd`.
- Creating pipeline, dashboard, engine, QA, or infrastructure code.
- Resolving any open question or approving an infrastructure choice.
- Assigning satellite repository ownership or inventing URLs, permissions, or
  production capabilities.
- Modifying `roadmap.json` directly.

## Completion Contract

### Outcome

The supplied system components map is incorporated into the hub as a reviewed
supporting document. Its reusable terminology is added to the glossary,
unresolved decisions are recorded as open questions, and `README.md` plus
`compound-gpid.md` identify and navigate to the new system map.

### Verification Surface

| ID | Evidence Required | Command/Artifact | Required | Phase |
|---|---|---|---|---|
| V1 | The system map contains the component inventory, relationships, composition table, and clear authority boundaries. | `system_map.md` review | yes | 1 |
| V2 | Terms introduced by the map are defined once in the shared glossary. | `glossary_and_questions/glossary.md` review and duplicate-term search | yes | 1 |
| V3 | Unresolved choices are recorded without being presented as decisions. | `glossary_and_questions/open_questions.md` review | yes | 1 |
| V4 | Repository navigation and project deliverables reference the new map. | `README.md` and `compound-gpid.md` review | yes | 2 |
| V5 | Markdown links, whitespace, and required files pass repository checks. | `git diff --check` plus targeted link/file checks | yes | 2 |

### Constraints

| ID | Constraint | Check | Phase |
|---|---|---|---|
| C1 | Do not add pipeline code, data, or implementation-specific operational details to the hub. | Review changed files against `AGENTS.md`. | 1 |
| C2 | Do not duplicate canonical statistical methodology or satellite-repository README content. | Compare additions with canonical architecture and repository boundaries. | 1 |
| C3 | Preserve unresolved matters as open questions and do not invent infrastructure capabilities or ownership facts. | Review all proposed statements for status and source. | 1 |
| C4 | Treat `system_map.md` as a new supporting file and update navigation metadata accordingly. | Verify file is referenced from `README.md` and `compound-gpid.md`. | 2 |
| C5 | Changes outside `sync_status/` require human review. | Present the resulting diff for review. | final |

### Boundaries

- Allowed: add and organize the system map; extract concise definitions into
  the glossary; add map-derived unresolved questions; update README navigation
  and project deliverables.
- Out of scope: modifying existing architecture decisions, changing canonical
  Quarto documents, resolving open questions, assigning repository owners,
  changing roadmap data, or adding implementation code/data.

### Iteration Policy

1. Classify each map statement as system-map content, glossary terminology, or
   an unresolved question.
2. Preserve approved or already-established architecture language where it
   exists; flag conflicts instead of silently reconciling them.
3. Keep glossary entries concise and avoid duplicating existing definitions.
4. Record only genuinely unresolved decisions in `open_questions.md`, preserving
   their open status.
5. Validate links, whitespace, required files, and the final diff after
   implementation.
6. If a conflict with a canonical document or existing architecture decision
   is found, stop that slice and surface it for human resolution.

### Blocked-Stop Conditions

- The map contradicts `canonical/system-architecture.qmd` or an existing
  architecture decision in a way that cannot be resolved by documenting status.
- A proposed glossary entry would assert methodology owned by the canonical
  schema repository.
- The intended destination or wording of a map-derived item cannot be
  determined without inventing project facts.
- The new document cannot be added without violating repository ownership or
  review rules.
