# Visual Architecture Diagrams

These diagrams are supporting orientation artifacts for the hub. They do not
override canonical sources in `canonical/system-architecture.qmd` and
`canonical/infrastructure-requirements.qmd`, and they do not create new
methodological or infrastructure decisions.

All diagram files in this folder are draft material and require human review
before merge.

## Canonical Source and Export Convention

- Canonical editable source: `.excalidraw` JSON.
- Rendered adaptation: same-stem `.svg` export for GitHub/browser viewing.
- PNG fallback: allowed only if SVG is shown unsuitable and an explicit
	deviation is approved.

## Stable Filenames

| Stem | Purpose | Status |
|---|---|---|
| `three-schema-harmonization-flow` | Distinguish Schema 1 (survey profile), Schema 2 (canonical GMD schema), and Schema 3 (harmonization specification) inside the review-controlled flow. | Draft (build complete; review pending) |
| `satellite-repository-dependency-map` | Show verified repository relationships and unresolved physical ownership/URL gaps without inventing infrastructure claims. | Draft (build complete; review pending) |
| `architecture-decisions-component-map` | Map ADR coverage to numbered `system_map.md` components and surface authority/status differences. | Draft (build complete; review pending) |

Expected source/export pairs:

- `three-schema-harmonization-flow.excalidraw` +
	`three-schema-harmonization-flow.svg`
- `satellite-repository-dependency-map.excalidraw` +
	`satellite-repository-dependency-map.svg`
- `architecture-decisions-component-map.excalidraw` +
	`architecture-decisions-component-map.svg`

## Visual Language

### Palette

| Semantic role | Color | Usage |
|---|---|---|
| Source/input artifact | `#FFF4CC` | Questionnaire and raw-data inputs |
| Survey/profile schema artifact | `#E8F4FF` | Schema 1 and metadata/reconciliation nodes |
| Canonical rule artifact | `#E8F7EF` | Schema 2 and binding rules |
| AI-assisted proposal | `#F4ECFF` | Drafting/proposal layers |
| Human gate | `#FFF1E3` | Approval/rejection control points |
| Deterministic execution | `#ECEFF1` | Engine and rule-based automated checks |
| Output/audit | `#E8F5E9` | Final products and lineage artifacts |
| Open/unresolved status | `#FFE8E8` | Unknown owner/URL/status notes |

### Typography

- Primary family: `IBM Plex Sans`, then `Segoe UI`, then `sans-serif`.
- Minimum text size: 14 px body labels, 16 px section or node titles.
- Use concise labels (target: 12 words or fewer per node line).
- Include explicit status tags (`Approved`, `Proposed`, `Open`) when status
	could be misread.

### Shapes and Connectors

- Rounded rectangles: system artifacts or components.
- Double-border rounded rectangle: canonical/binding artifact.
- Solid arrow: verified data or decision flow.
- Dashed arrow: advisory feedback loop.
- Dotted border: unresolved assignment or open claim.

Every diagram must include a small legend that documents color and connector
semantics.

## Accessibility and Readability

- Target WCAG-like contrast expectations for label text against fills.
- Avoid color-only meaning; pair color with label or status tag.
- Keep major reading flow left-to-right and top-to-bottom.
- Verify readability at desktop width and narrow width before phase/final
	completion gates.

## Authoritative Basis and Claim Traceability

- Every node/edge/status claim must be traceable in
	`claim-source-matrix.md`.
- Allowed source classes for claims:
	- Canonical architecture/infrastructure documents.
	- `README.md` navigation and authority statements.
	- `system_map.md` as supporting orientation material.
	- Existing ADR files for confirmed decisions.
- If a claim cannot be traced, mark it open/unresolved or remove it.

## Editing and Export Procedure

1. Edit the `.excalidraw` source first.
2. Confirm node/edge labels match traced claims in `claim-source-matrix.md`.
3. Export as SVG with a white background and same stem filename.
4. Keep one source and one SVG per stem; do not generate extra variants.
5. Validate source and export:
	 - JSON parse for `.excalidraw`.
	 - XML parse for `.svg`.
	 - Same-stem pair check.
6. Check render at desktop and narrow viewport for clipping/blank output.
7. Update this README and the claim matrix for any semantic changes.

## Maintenance Ownership Status

- Named per-diagram maintainers are not yet confirmed in canonical sources.
- Until ownership is assigned, updates proceed through normal pull-request
	review in this repository.

## Diagram Index

| Diagram | Purpose | Canonical editable source | Rendered export | Authoritative basis | Maintenance ownership/status | Review state |
|---|---|---|---|---|---|---|
| Three-schema harmonization flow | Show Schema 1, Schema 2, Schema 3 and control gates from draft to deterministic execution. | [three-schema-harmonization-flow.excalidraw](three-schema-harmonization-flow.excalidraw) | [three-schema-harmonization-flow.svg](three-schema-harmonization-flow.svg) | [canonical/system-architecture.qmd](../canonical/system-architecture.qmd), [system_map.md](../system_map.md), [README.md](../README.md) | Owner unresolved; PR review required | Draft |
| Satellite repository dependency map | Show verified repository relationships and unresolved physical assignment gaps. | [satellite-repository-dependency-map.excalidraw](satellite-repository-dependency-map.excalidraw) | [satellite-repository-dependency-map.svg](satellite-repository-dependency-map.svg) | [README.md](../README.md), [canonical/system-architecture.qmd](../canonical/system-architecture.qmd), [system_map.md](../system_map.md) | Owner unresolved; PR review required | Draft |
| Architecture-decision component map | Show ADR-to-component coverage and authority/status differences. | [architecture-decisions-component-map.excalidraw](architecture-decisions-component-map.excalidraw) | [architecture-decisions-component-map.svg](architecture-decisions-component-map.svg) | [architecture_decisions](../architecture_decisions/), [system_map.md](../system_map.md), [canonical/system-architecture.qmd](../canonical/system-architecture.qmd), [canonical/infrastructure-requirements.qmd](../canonical/infrastructure-requirements.qmd) | Owner unresolved; PR review required | Draft |
