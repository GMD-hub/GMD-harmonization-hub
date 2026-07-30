# Glossary

**Canonical Variable Schema (CVS).** The authoritative, machine readable
rulebook for how each GMD variable must be harmonized. Lives in
`GMD-canonical-schema`. Contains no country specific content.

**Survey Profile.** A structured, machine readable summary of what is in a
raw household survey questionnaire, produced by `survey-scribe` before any
harmonization decision is made.

**Harmonization Specification.** The per survey, per variable record that
declares how a raw variable maps to a GMD variable. Drafted by AI, approved
by a human expert, then executed by a deterministic engine. This is the
central artifact of the whole pipeline.

**Atomic variable.** A leaf node GMD variable. The AI maps only to these.

**Derived variable.** A GMD variable computed deterministically from atomic
variables in code, never mapped to directly by the AI.

**derived_preferred.** A mapping role for a variable that can behave as
either atomic or derived depending on what the source survey provides.

**Situation A, B, C.** The three mapping outcomes for a variable in a given
survey. A: direct mapping. B: inferred from a proxy with a documented
conversion. C: set to missing with a documented fallback reason.

**Country Parameter Layer.** A sparse overlay of country specific
parameters that sit outside the CVS, referenced by lookup tables rather
than embedded in the universal rules.

**Historical decisions database.** A vector database of past harmonization
decisions, used as advisory precedent only. The schema database always
wins when the two disagree.

**GPID Team.** The World Bank team leading this project.

**ITS.** The World Bank's IT services division, the infrastructure partner
for this project.

**do2screen.** A Stata ado program used to parse legacy harmonization
scripts as the first step of the legacy script ingestion pipeline.
