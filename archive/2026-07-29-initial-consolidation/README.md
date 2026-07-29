# Initial Documentation Consolidation Archive

**Archived:** 2026-07-29

**Status:** Noncanonical historical material

**Superseded by:** `README.md` and the two documents under `canonical/`

This archive preserves every proposal, narrative, presentation, rendered output,
and supporting asset that informed the first canonical version of the GMD
Harmonization Hub. Files are retained for provenance. They must not be used to
resolve current architecture or infrastructure questions.

## Archived source mapping

| Original path | Archived path | Classification |
|---|---|---|
| `AI-GMD_harmonization_proposal.qmd` | `source-drafts/root/AI-GMD_harmonization_proposal.qmd` | Concept note; duplicate of the writing copy |
| `writing/AI-GMD_harmonization_proposal.qmd` | `source-drafts/writing/AI-GMD_harmonization_proposal.qmd` | Concept note; duplicate of the root copy |
| `writing/GMD_AI_Harmonization_Presentation_Narrative.qmd` | `source-drafts/writing/GMD_AI_Harmonization_Presentation_Narrative.qmd` | Plain-language team adaptation |
| `writing/GMD_AI_Harmonization_System_Narrative.qmd` | `source-drafts/writing/GMD_AI_Harmonization_System_Narrative.qmd` | Detailed process narrative |
| `writing/GMD_Infrastructure_Request_ITS.qmd` | `source-drafts/writing/GMD_Infrastructure_Request_ITS.qmd` | Concise ITS request, draft v2 |
| `writing/GMD_Infrastructure_Requirements_ITS.qmd` | `source-drafts/writing/GMD_Infrastructure_Requirements_ITS.qmd` | Detailed ITS requirements, draft v1 |
| `writing/questions_round1.qmd` | `source-drafts/writing/questions_round1.qmd` | ITS discovery questionnaire |
| `writing/GMD_AI_Harmonization_System_Narrative_files/` | `source-drafts/writing/GMD_AI_Harmonization_System_Narrative_files/` | Generated Quarto figure cache |
| `slides/` | `presentations/slides/` | Team slide source, styles, and rendered presentations |
| `docs/` | `rendered-documents/` | Generated HTML, PDF, DOCX, and support files |
| `css/` | `presentation-assets/css/` | Presentation stylesheet dependency |
| `img/` | `presentation-assets/img/` | Diagram image assets |
| `reference.docx` | `rendering-assets/reference.docx` | Quarto DOCX rendering template |

## Duplicate finding

The two copies of `AI-GMD_harmonization_proposal.qmd` were byte-identical at
consolidation. Both had SHA-1:

```text
aa94219925b5219f8a7a06fc376e1cd1fee53588
```

Both are retained so that the original repository state can be reconstructed.

## Conflicts found in the archived drafts

The canonical rewrite resolved or explicitly exposed the following conflicts:

1. **Post-approval changes:** the slide deck allowed an AI agent to revise and
   rerun technical failures without human input, while the concept note made
   approved logic immutable. The canonical rule requires reapproval after any
   logic change.
2. **Lifecycle numbering:** drafts alternated among six stages, seven stages,
   seven components, and stages 1a/1b. The canonical architecture uses a state
   machine instead of unstable presentation numbering.
3. **Specification semantics:** one draft called the specification
   non-executable while another executed it in a sandbox. Canonically, a draft
   may be syntactically executable but remains unauthorized until approved.
4. **Raw data and AI:** sources disagreed on whether AI "reads" raw data. The
   canonical boundary keeps raw microdata in controlled executors and allows
   only approved, minimized diagnostics to cross to a model.
5. **Infrastructure certainty:** Azure products and AKS were sometimes written
   as settled architecture even though the ITS documents asked whether they
   were available and approved. They are now candidates with explicit status.
6. **Workflow state:** file storage was described as the only handoff for review,
   without concurrency or stale-approval semantics. The canonical requirement
   separates immutable artifacts from transactional workflow state.
7. **Terminology:** drafts expanded GMD as both "Global Micro Database" and
   "Global Monitoring Database." The canonical documents follow the project
   charter and retain a verification marker before external publication.
8. **Claims requiring evidence:** annual volume, time per survey, expected gains,
   data-policy claims, service guarantees, and production readiness were not
   consistently sourced. They are not treated as canonical facts.

## Preservation policy

- Do not edit archived files to match the canon.
- Correct current logic only in the canonical documents.
- If an archived source is used in a stakeholder adaptation, verify its claims
  against the canon and current institutional guidance first.
- Add future superseded material to a new dated archive rather than this one.