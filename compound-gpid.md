---
project-name: "AI-Assisted Harmonization of Household Surveys for the Global Micro Database (GMD)"
team: "GMD-hub -- World Bank"
created: "2026-07-29"
last-reviewed: "2026-07-29"
---

# AI-Assisted Harmonization of Household Surveys for the Global Micro Database (GMD)

## Objective

The system is designed to accelerate interpretation and standardization of household survey microdata into the Global Micro Database while preserving human authority, methodological rigor, and deterministic execution. AI systems assist by proposing mappings and diagnosing logic but never make final methodological decisions; human experts retain full authority.

## Key Deliverables

- System architecture and design principles
- Process narrative and operational manual
- Infrastructure requirements specification
- Infrastructure deployment request
- Presentations and stakeholder communication
- Q&A and issues log

## Constraints

- All harmonization decisions must be explicitly approved by human experts before execution; AI-generated proposals are never autonomously applied.
- All approved decisions must be executed by fixed, versioned code.
- Raw survey microdata is not stored in this architecture and design workspace.
- All choices must be traceable and documented; methodological decisions must not be implicit in model weights.

## Current Focus

The GMD Harmonization Hub is the central reference point for the AI assisted household survey harmonization pipeline. It records how the canonical schema, the survey extraction pipeline, the historical precedent knowledge base, and the human review process fit together as a single system, and it explains the reasoning behind the major design decisions that shape that system. Its purpose is to let any team member, collaborator, or institutional partner understand the architecture of the pipeline and the responsibilities each repository and each person holds, without needing to reconstruct that understanding from scattered conversations, code, or memory. The hub contains no pipeline code of its own. Its role is to explain, connect, and preserve the reasoning behind the system, so the project stays legible as it grows and as team membership changes.