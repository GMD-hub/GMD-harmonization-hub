---
project-name: "GMD Harmonization Hub"
team: "GMD-hub, World Bank"
created: "2026-07-29"
last-reviewed: "2026-07-29"
---

# GMD Harmonization Hub

## Objective

The system is designed to accelerate interpretation and standardization of
household survey microdata into the Global Micro Database while preserving
human authority, methodological rigor, and deterministic execution. AI
systems assist by proposing mappings and diagnosing logic but never make
final methodological decisions; human experts retain full authority. This
repository is the explanatory layer for that broader initiative. It does
not perform harmonization itself.

## Key Deliverables

- A repo map explaining what each pipeline repository does and how they
  relate
- A dated log of confirmed architecture decisions with their rationale
- A shared glossary of project terminology
- A tracked list of open questions, moved into the decisions log once
  resolved
- Role specific guidance for collaborators such as regional focal points
  and ITS
- Diagrams of the pipeline and repo relationships

## Constraints

- This repository holds no harmonization pipeline code (mapping logic, harmonize_{variable} functions, or anything that touches survey data). Small maintenance tooling for the hub itself, such as a status sync workflow, is in scope.
- Content that already exists in a satellite repo's README is summarized
  briefly here and linked to, never duplicated
- Changes to an existing entry in the architecture decisions log require
  human review
- This repository does not execute anything and has no connection to
  production data flows

## Current Focus

The GMD Harmonization Hub is the central reference point for the AI
assisted household survey harmonization pipeline. It records how the
canonical schema, the survey extraction pipeline, the historical precedent
knowledge base, and the human review process fit together as a single
system, and it explains the reasoning behind the major design decisions
that shape that system. Its purpose is to let any team member,
collaborator, or institutional partner understand the architecture of the
pipeline and the responsibilities each repository and each person holds,
without needing to reconstruct that understanding from scattered
conversations, code, or memory. The hub contains no pipeline code of its
own. Its role is to explain, connect, and preserve the reasoning behind
the system, so the project stays legible as it grows and as team
membership changes.
