---
date: 2026-07-30
title: "Create the Visual Architecture diagram set"
status: completed
scope: "Standard"
brainstorm: null
language: "other"
estimated-effort: "medium"
deviation-policy: "ask"
tags: [documentation, architecture, diagrams, excalidraw, svg]
phases: 2
execution-report: ".cg-docs/work-reports/2026-07-30-visual-architecture.md"
completed-phases: [1, 2]
completed-date: 2026-07-30
---

# Plan: Create the Visual Architecture diagram set

## Objective

Create three clear, consistent, and maintainable architecture diagrams that
orient new collaborators to the harmonization schemas, satellite repository
relationships, and architecture-decision coverage. Keep native Excalidraw files
as the canonical editable sources, publish GitHub-viewable SVG exports, and
derive every represented claim from current authoritative repository material.

## Context

The `visual-architecture` roadmap milestone contains four features: establish a
shared source/export convention, build the three-schema harmonization flow,
build the satellite repository dependency map, and map confirmed architecture
decisions to the `system_map.md` components they govern. The shared convention
and three-schema flow should be completed first so the first diagram becomes a
validated reference for the remaining two.

The hub is explanatory and does not own pipeline code, survey data, or GMD
methodology. `README.md`, `canonical/system-architecture.qmd`, and
`canonical/infrastructure-requirements.qmd` define the authority hierarchy;
`system_map.md` is supporting orientation material. Existing architecture
decision records are confirmed records but may not silently override
higher-authority canonical text. In particular, ADR 0001 names a vector
database while the canonical infrastructure document treats dedicated vector
storage as optional, and ADR 0002 calls atomic-only mapping confirmed while the
canonical architecture currently labels that rule Proposed. The decision map
must expose these status differences or stop for human resolution.

Physical satellite repository URLs and named owners are not fully confirmed in
the canonical architecture. The implementation may use only links and
maintenance roles verified from authoritative current sources. It must not
guess missing URLs, ownership, infrastructure capabilities, repository
dependencies, or harmonization rules. All diagram changes are draft material
outside `sync_status/` and require human review before merge.

No relevant Excalidraw or SVG-export pattern was found in the project Brain.
The completed system-map plan contributes one applicable lesson: preserve the
hub authority hierarchy and keep unresolved repository and ownership facts
explicit rather than converting them into diagram claims.

## Requirements

| ID | Requirement | Source |
|----|-------------|--------|
| R1 | Define consistent filenames, layout, palette, typography, connector semantics, status treatments, legends, accessibility expectations, canonical-source policy, and repeatable SVG export instructions before constructing diagrams. | User request; roadmap convention feature |
| R2 | Use native `.excalidraw` JSON as the canonical editable source and pair each source with a same-stem GitHub-viewable SVG export under `diagrams/`; use PNG only after SVG is shown unsuitable and a deviation is approved. | User request |
| R3 | Build the three-schema harmonization flow first, distinguishing the survey profile, canonical GMD schema, and harmonization specification while preserving authority, review, and deterministic-execution boundaries. | User request; `system_map.md`; `canonical/system-architecture.qmd` |
| R4 | Build a satellite repository dependency map that uses only verified identities and relationships, links to authoritative repositories instead of duplicating their content, and marks unknown physical or ownership details as unresolved. | User request; `README.md`; `canonical/system-architecture.qmd` |
| R5 | Build a decision-coverage map from architecture decision records to the numbered `system_map.md` components they govern, preserving decision status, source authority, and any canonical conflicts. | User request; `architecture_decisions/`; `system_map.md` |
| R6 | Make each diagram understandable to a new collaborator through concise labels, directional edges, legends, source/status cues, and links without requiring every repository document to be read first. | User request; Visual Architecture milestone objective |
| R7 | Update `diagrams/README.md` with each diagram's purpose, canonical editable source, rendered export, authoritative basis, maintenance ownership or unresolved ownership status, and export/maintenance procedure. | User request; `AGENTS.md` |
| R8 | Maintain a claim/source matrix during implementation so every node, edge, status, and repository link is traceable to current canonical material or a confirmed decision record. | User request; repository authority hierarchy |
| R9 | Validate Excalidraw JSON, complete source/export pairs, nonempty scenes, valid SVG XML, readable GitHub/browser rendering, links, and consistency with `system_map.md` and architecture decisions. | User request |
| R10 | Keep all implementation edits under `diagrams/`, treat them as draft content requiring human review, and do not directly edit canonical documents, existing ADRs, `system_map.md`, or `roadmap.json`. | `AGENTS.md`; plan file permissions |
| R11 | Link this one plan to all four features in the `visual-architecture` milestone and update feature status only through `@cg-roadmap` according to lifecycle state. | User request; `/cg-plan` roadmap contract |

## Implementation Steps

## Phase 1: Convention and reference flow

### 1. Establish the shared diagram and export convention

- **Requirements**: R1, R2, R6, R7, R8, R10
- **Files**: `diagrams/README.md`; supporting claim/source matrix under
  `diagrams/` if keeping it separate makes maintenance clearer
- **Details**: Define stable same-stem names for the three source/export pairs,
  with descriptive lowercase kebab-case names. Document the canonical role of
  `.excalidraw`, the rendered role of `.svg`, and the approved fallback rule for
  PNG. Establish a restrained, accessible palette with semantic colors for
  source/input, schema or authoritative rule, human gate, AI-assisted proposal,
  deterministic code, output, and open/proposed state. Define typography,
  minimum text size, line/arrow meanings, node shapes, grouping, legends,
  source/status annotations, canvas bounds, and export settings. Record how to
  open, edit, and export without embedding unsupported claims. Begin a
  claim/source matrix listing each intended diagram node and edge, its source,
  authority/status, and any unresolved issue. Record maintenance ownership by
  verified role or explicitly mark it unresolved; do not invent a person or
  repository owner.
- **Test Scenarios**: a contributor can identify the canonical source and
  reproduce an SVG export; status colors do not imply approval; a missing owner
  remains visibly unresolved; filenames support exact pair validation.
- **Tests**: targeted README heading/content checks; link target checks;
  `git diff --check`.
- **Acceptance criteria**: the convention and initial claim/source matrix are
  reviewable before diagram construction, cover all visual semantics used by
  the planned diagrams, and introduce no unverified ownership or tooling claim.

### 2. Build and validate the three-schema harmonization flow

- **Requirements**: R2, R3, R6, R8, R9, R10
- **Files**: `diagrams/three-schema-harmonization-flow.excalidraw`,
  `diagrams/three-schema-harmonization-flow.svg`, `diagrams/README.md`, and the
  claim/source matrix
- **Details**: Use the shared convention to show Schema 1 (survey profile),
  Schema 2 (canonical GMD schema), and Schema 3 (harmonization specification)
  within the broader controlled flow. Include only the minimum surrounding
  components needed to explain inputs, drafting, human review, approved exact
  specification, deterministic execution, QA, and feedback. Distinguish what
  describes the survey, what governs target definitions, and what records a
  survey-specific mapping. Reconcile the informal Schema 1/2/3 labels in
  `system_map.md` with canonical artifact terminology and avoid presenting the
  supporting map as architecture authority. Validate this first source/export
  pair as the reference implementation; adjust the shared convention before
  using it in later diagrams.
- **Test Scenarios**: a new collaborator can identify all three schemas and
  their roles; approval is not confused with drafting; production execution
  cannot bypass human review; historical precedent remains advisory; labels
  remain readable in a narrow browser viewport.
- **Tests**: `jq` parse and required Excalidraw scene-key/nonempty-element
  assertions; `xmllint --noout` for SVG; same-stem pair check; browser render at
  desktop and narrow viewports with screenshot and nonblank/clipping review;
  claim/source matrix reconciliation.
- **Acceptance criteria**: the Excalidraw source parses and remains editable,
  the SVG renders legibly on GitHub-compatible browser views, all represented
  claims have source/status entries, and the visual convention is stable enough
  to apply to the remaining diagrams.

## Phase 2: Relationship maps, index, and final validation

### 3. Build the satellite repository dependency map

- **Requirements**: R2, R4, R6, R8, R9, R10
- **Files**: `diagrams/satellite-repository-dependency-map.excalidraw`,
  `diagrams/satellite-repository-dependency-map.svg`, `diagrams/README.md`, and
  the claim/source matrix
- **Details**: Map the hub and satellite repositories using the current repo
  map and canonical capability boundaries. Label edges by verified artifact or
  information relationships rather than implying deployment, write access, or
  runtime dependencies that are not documented. Link each repository label to
  its authoritative repository only when the physical URL is verified; keep
  historical pilots visibly outside the production pipeline. Summarize each
  role in at most a short phrase and direct readers to the authoritative
  repository instead of duplicating its README. Where logical capabilities do
  not yet have confirmed physical repository assignments, show that distinction
  explicitly or halt if the requested dependency cannot be represented
  truthfully.
- **Test Scenarios**: an implementation repository is not mistaken for a
  logical capability; the hub is not shown as owning pipeline code; the
  historical pilot is not shown as production; an unverified URL or owner is
  not silently filled in.
- **Tests**: JSON/XML and pair checks; repository-link validation; edge-by-edge
  source matrix review against `README.md` and canonical capability ownership;
  desktop/narrow browser render review.
- **Acceptance criteria**: the source/export pair is valid and readable, every
  repository and relationship is verified and linked where authoritative URLs
  are known, and no edge claims an undocumented operational dependency.

### 4. Build the architecture-decision coverage map

- **Requirements**: R2, R5, R6, R8, R9, R10
- **Files**: `diagrams/architecture-decisions-component-map.excalidraw`,
  `diagrams/architecture-decisions-component-map.svg`, `diagrams/README.md`,
  and the claim/source matrix
- **Details**: Map each existing ADR to the numbered `system_map.md` components
  it directly governs, and distinguish direct governance from contextual or
  hub-only scope. Include concise decision labels and links to the full ADRs
  rather than restating their rationale. Represent ADR status and authority
  explicitly. For ADR 0001 and ADR 0002, compare the decision text with the
  current canonical architecture and infrastructure status; annotate the
  discrepancy without choosing a winner, or stop for human resolution if a
  truthful visual treatment is not possible. Keep ADR 0005 scoped to repository
  charter governance rather than implying that it governs harmonization
  methodology. Do not edit existing decision records.
- **Test Scenarios**: every ADR is considered; a component with no governing ADR
  is not given one by inference; direct and contextual mappings are visually
  distinct; canonical conflicts are visible; ADR links resolve.
- **Tests**: JSON/XML and pair checks; ADR-to-component matrix reconciliation
  against all five ADR files and `system_map.md`; conflict/status assertion in
  the legend or annotations; desktop/narrow browser render review.
- **Acceptance criteria**: the map shows defensible decision coverage and gaps,
  preserves status and authority differences, and contains no invented
  governance relationship.

### 5. Complete the diagram index and run cross-diagram validation

- **Requirements**: R1, R2, R6, R7, R8, R9, R10, R11
- **Files**: all files under `diagrams/`; roadmap registration delegated to
  `@cg-roadmap`
- **Details**: Finish the README inventory with a row for each diagram covering
  purpose, canonical editable source, rendered export, authoritative basis,
  maintenance owner or role/status, and review state. Include repeatable edit
  and export instructions, SVG fallback criteria, shared legend/conventions,
  and a concise reminder that diagrams are supporting drafts rather than
  independent authority. Run one focused validation over exactly the three
  expected source/export pairs: parse every Excalidraw JSON file, assert a
  nonempty scene and expected file type/version fields, parse every SVG as XML,
  verify pair names and README links, and inspect browser renders at desktop and
  narrow widths for clipping, blank output, and unreadable labels. Reconcile
  the completed claim/source matrix against canonical documents,
  `system_map.md`, and every ADR. Review the final diff and path allowlist.
  After the plan is saved and approved, dispatch `@cg-roadmap` to link this plan
  to each of the four `visual-architecture` feature IDs and set each feature to
  the lifecycle-appropriate status; verify only the targeted feature status and
  plan fields afterward.
- **Test Scenarios**: a missing export fails the pair check; malformed or empty
  Excalidraw JSON fails validation; malformed SVG fails XML parsing; README
  source/export links resolve; a diagram diverging from the claim matrix blocks
  completion; unrelated file changes are detected.
- **Tests**: focused `find`/`jq`/`xmllint` validation; targeted Markdown link
  checks; browser screenshots and viewport/nonblank review; source matrix
  reconciliation; `git diff --check`; `git diff --name-only` allowlist; targeted
  roadmap status/plan read after `@cg-roadmap` dispatch.
- **Acceptance criteria**: all three canonical source/export pairs and README
  records are complete and consistent, all required checks pass with recorded
  evidence, only allowed diagram files changed during implementation, the work
  remains a draft for human review, and all four milestone features reference
  this plan with lifecycle-consistent status.

## Testing Strategy

Validation is incremental. First validate the convention and the three-schema
source/export pair; this is the cheapest check that can disprove the proposed
visual system before it propagates. Validate each later pair immediately after
creation using `jq` for Excalidraw JSON, `xmllint` for SVG XML, exact filename
pair checks, link checks, and browser rendering at desktop and narrow widths.

The final validation runs over an explicit allowlist of three expected stems,
not every arbitrary file in `diagrams/`. It verifies nonempty Excalidraw scenes,
valid SVGs, complete pairs, README references, and no unexpected implementation
paths. Visual checks must establish that each SVG is nonblank, framed within its
viewport, unclipped, and readable at GitHub-like desktop and narrow widths.
Content validation is separate from syntax validation: every node, edge,
status, and external link is checked against the claim/source matrix and then
against the canonical QMDs, `system_map.md`, or an existing ADR.

No new validation dependency should be added unless the built-in `jq`,
`xmllint`, browser tooling, and chosen Excalidraw export workflow prove
insufficient. Any new tool or package is a deviation requiring approval and
documentation of its reproducibility implications.

## Documentation Checklist

- [ ] State that `.excalidraw` is canonical and SVG is a rendered adaptation.
- [ ] Document stable filenames and same-stem source/export pairing.
- [ ] Document palette, typography, shapes, edge semantics, status cues, and legends.
- [ ] Document accessible contrast, minimum text size, and narrow-view readability.
- [ ] Record each diagram's purpose and intended audience.
- [ ] Link each canonical editable source and rendered export.
- [ ] List authoritative basis and claim/source matrix location.
- [ ] Record verified maintenance ownership by role or mark ownership unresolved.
- [ ] Document the exact edit/export/review procedure and SVG fallback rule.
- [ ] Mark all diagrams as supporting drafts requiring human review.
- [ ] Link satellite repositories only through verified authoritative URLs.
- [ ] Record how ADR/canonical status discrepancies are displayed.

## Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| Supporting `system_map.md` terminology is mistaken for canonical architecture | The diagrams could elevate an adaptation into a new source of truth | Reconcile every claim with canonical QMDs and label supporting terminology/status explicitly. |
| ADR 0001 or 0002 conflicts with current higher-authority canonical status | The decision map could silently choose an authority or misstate approval | Show the discrepancy and authority levels explicitly; stop for human resolution if it cannot be represented neutrally. |
| Satellite URLs, owners, or physical boundaries remain unconfirmed | The dependency map could invent relationships or produce unreliable links | Use only verified links and role ownership; leave unknowns explicit or block the affected diagram. |
| Excalidraw export changes text, links, fonts, or canvas framing | GitHub renders may be clipped, blank, or materially different from the source | Validate SVG XML and browser rendering at two viewports after every export; keep reproducible export settings in README. |
| Dense content becomes unreadable to new collaborators | Diagrams fail their orientation purpose despite being technically correct | Limit labels, use layered grouping and legends, apply minimum text sizes, and test narrow rendering. |
| Semantic colors imply authority or approval incorrectly | Readers may confuse proposed, open, advisory, and binding material | Define semantic colors/status badges before drawing and include a legend in every diagram. |
| Diagram and source drift after canonical documents change | Rendered architecture becomes stale | Record source basis, maintenance role/status, and a review checklist in README; require source-first updates and re-export. |
| A generated export obscures a user-authored or unrelated change | Review becomes unsafe | Work on the accepted branch, inspect the path allowlist and diff, and never revert unrelated changes. |

## Out of Scope

- Changing canonical architecture, infrastructure requirements, methodology, or
  harmonization rules.
- Resolving conflicts between canonical documents and confirmed ADRs.
- Editing existing files in `architecture_decisions/` or `system_map.md`.
- Assigning physical repositories, named owners, or infrastructure products
  where current authority leaves them open.
- Creating pipeline code, automated status-sync tooling, or survey artifacts.
- Publishing or merging the diagrams without human review.
- Producing PNG exports unless SVG is demonstrably unsuitable and the deviation
  is explicitly approved.

## Completion Contract

### Outcome

Three consistently styled, editable `.excalidraw` sources and three
GitHub-viewable SVG exports exist under `diagrams/`, with `diagrams/README.md`
documenting purpose, source/export links, authority, ownership, conventions, and
repeatable export instructions. Every represented claim is traceable to current
canonical material or a confirmed ADR, and all changes remain draft branch
content pending human review.

### Verification Surface

| ID | Phase | Evidence Required | Command/Artifact | Required |
|----|-------|-------------------|------------------|----------|
| V1 | 1 | Shared convention and claim/source matrix exist before diagram construction | `diagrams/README.md` and implementation diff | yes |
| V2 | 1 | Three-schema source is valid Excalidraw JSON and has a valid, matching SVG export | `jq`, `xmllint`, filename-pair check, browser render | yes |
| V3 | 2 | All three expected `.excalidraw`/`.svg` pairs exist, parse, and contain nonempty scenes | Focused `find`/`jq`/`xmllint` validation command | yes |
| V4 | 2 | SVGs render readably at desktop and narrow viewports without clipping or blank output | Browser-render screenshots plus viewport/nonblank checks and recorded review | yes |
| V5 | final | Diagram labels, edges, statuses, ADR mappings, and links reconcile with authoritative sources | Claim/source matrix review against canonical QMDs, `system_map.md`, and ADR files | yes |
| V6 | final | README records purpose, canonical editable source, rendered export, maintenance owner/role, and export procedure for each diagram | Targeted README checks and link validation | yes |
| V7 | final | The branch is reviewable and no protected/existing ADR or canonical source was modified | `git diff --check`, path allowlist, and final diff review | yes |

### Constraints

| ID | Phase | Constraint | Check |
|----|-------|------------|-------|
| C1 | 1 | Native `.excalidraw` files are the canonical editable diagram sources; SVG is the default render | Pair/convention checks |
| C2 | 1 | Shared naming, palette, typography, connector, status, legend, and export rules precede the first diagram | README/convention section review |
| C3 | 2 | No infrastructure capability, repository relationship, URL, owner, or harmonization rule is inferred | Source matrix and unresolved-claim scan |
| C4 | 2 | Canonical authority/status distinctions remain visible, including conflicts between ADR 0001/0002 and higher-authority canonical text | ADR-map legend and source reconciliation review |
| C5 | final | Satellite content is linked and briefly summarized, not duplicated | Link/content review |
| C6 | final | Changes outside `sync_status/` remain drafts requiring human approval | Branch/PR review state; no direct merge |
| C7 | final | Existing canonical QMDs, ADR entries, `system_map.md`, and `roadmap.json` are not edited by implementation | `git diff --name-only` allowlist; roadmap writes delegated to `@cg-roadmap` |

### Boundaries

- Allowed: new diagram sources/exports under `diagrams/`, updates to
  `diagrams/README.md`, validation evidence, and a roadmap-link dispatch after
  plan approval.
- Allowed: concise source/status annotations and links to authoritative
  repository or document locations once verified.
- Out of scope: changing canonical architecture, resolving ADR/canonical
  conflicts, assigning unconfirmed owners, approving infrastructure, editing
  ADRs, or adding pipeline code.
- Out of scope: PNG exports unless SVG is demonstrably unsuitable and the
  deviation is approved.

### Iteration Policy

1. Lock the shared convention and claim/source matrix first.
2. Build and validate the three-schema flow as the reference; correct the
   convention before propagating it.
3. Reuse the approved convention for the repository and ADR diagrams.
4. Under `deviation-policy: ask`, pause before changing format, using PNG,
   introducing tooling or dependencies, or representing an unsupported claim.
5. Run focused validation after each source/export pair, then the complete
   cross-diagram check.
6. Submit the finished diagram set as draft content for human review; do not
   treat review as architectural approval.

### Blocked-Stop Conditions

- A diagram claim cannot be traced to a canonical document or confirmed ADR.
- A required satellite repository URL or maintenance owner/role cannot be
  verified.
- “Schema 1/2/3” wording cannot be reconciled with canonical artifact
  terminology without overstating authority.
- The ADR-to-component mapping would conceal or arbitrarily resolve a conflict
  between authority levels.
- SVG cannot render legibly and switching to PNG has not been approved.
- Required executable validation cannot run, or a required evidence item
  remains failed.
- Work would require modifying a canonical source, existing ADR,
  `system_map.md`, or `roadmap.json` directly.