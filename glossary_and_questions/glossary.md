# Glossary

**Canonical Variable Schema (CVS).** The authoritative, machine readable
rulebook for how each GMD variable must be harmonized. Lives in
`GMD-canonical-schema`. Contains no country specific content.

**Survey Profile.** A structured, machine readable summary of what is in a
raw household survey questionnaire, produced by `survey-scribe` before any
harmonization decision is made.

**Raw Data Cleaning.** The preprocessing stage that standardizes multi-file,
multi-level raw survey data into merge-ready structure with clear keys. It
changes data structure, not harmonization methodology.

**Raw Data Metadata (Raw Data Profile).** A factual profile generated from
cleaned raw data, including variable names and labels, missingness and
non-response patterns, and summary statistics. It describes what the data
contains, independent of questionnaire intent.

**Profile Reconciliation.** An agent-assisted cross-check between the Survey
Profile and the Raw Data Metadata that produces one verified profile for
downstream harmonization drafting.

**Reconciled Survey Profile.** The consolidated profile produced by Profile
Reconciliation and used as drafting input instead of either source alone.

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

**Harmonization Drafting Agent.** The orchestrating AI component that proposes
per-survey harmonization specifications using the reconciled profile, CVS,
country parameters, and historical precedents. It has no approval authority.

**Human Review Dashboard.** The review interface where experts approve, edit,
or reject drafted harmonization specifications before execution.

**Harmonization Engine.** The deterministic execution component that applies an
approved harmonization specification to cleaned raw data exactly as authored.

**Quality Assurance and Validation.** Automated checks over harmonized output,
including structural consistency, valid ranges, and cross-wave comparisons,
with escalation to drafting or human review depending on issue type.

**Audit trail.** The versioned record of specification approvals or overrides,
execution artifacts, and quality-assurance results attached to each produced
harmonized output.

**GPID Team.** The World Bank team leading this project.

**ITS.** The World Bank's IT services division, the infrastructure partner
for this project.

**do2screen.** A Stata ado program used to parse legacy harmonization
scripts as the first step of the legacy script ingestion pipeline.
