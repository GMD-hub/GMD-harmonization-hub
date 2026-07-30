# 0005. Compound GPID charter scoping

**Status.** Confirmed.
**Date confirmed.** 2026-07-29

**Decision.** Each repository linked to Compound GPID gets its own
`compound-gpid.md` project charter scoped to what that specific repository
does, with at most one or two sentences of context about the broader AI
harmonization initiative it belongs to. No single charter describes the
whole initiative across every repo.

**Why.** A charter is only visible to Copilot when a session opens in that
particular repository. A charter that describes the whole initiative gives
Copilot no boundary on what the repository it is currently sitting in
actually owns. For this hub specifically, an unscoped charter listing
things like infrastructure specifications or stakeholder presentations as
deliverables would contradict `AGENTS.md`, which states this repository
holds no pipeline code and no duplicated content. Scoping each charter to
its own repository, with only a light nod to the wider initiative, keeps
Copilot's sense of what it is allowed to produce aligned with what
`AGENTS.md` actually permits.
