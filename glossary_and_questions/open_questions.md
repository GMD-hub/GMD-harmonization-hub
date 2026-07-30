# Open questions

- Is Azure OpenAI Service approved in the WBG tenant? This is the single
  most critical unresolved question for the whole pipeline.
- What are the ITS infrastructure constraints and which Azure services are
  actually available to this project?
- Can GitHub Actions in this environment make outbound network calls, and
  can they use cross repo tokens? This determines whether the hub's
  planned sync automation is possible at all.
- Should Country Parameter Layer fallback policies (use the global
  default, skip the check, or block and escalate) be set centrally by the
  GPID team, or per country by country harmonizers? This choice shapes the
  whole layer's architecture.
- Does `basic` in `GMD_vars.csv` mean output file membership rather than
  mandatory status? Needs team confirmation.
- Do country specific education system conversion rules already exist
  anywhere on the team?
- What is the formal threshold between Situation B and Situation C for
  education variables?
- Are legacy harmonization scripts centralized in one repository, or
  scattered across country folders and personal drives?
- What is the full list of legacy surveys to include in the PoC historical
  database seed?
- Should Raw Data Cleaning remain fully deterministic, or should it include
  bounded agent assistance to detect file levels and structure in especially
  messy surveys?
- What does the AI Factory key actually connect to? An Anthropic
  compatible endpoint, Azure OpenAI Service, or a different OpenAI
  compatible gateway shape the design of any component that calls an LLM,
  most immediately the Phase 3 sync automation. Check onboarding
  documentation or ask whoever administers AI Factory access.

When a question here is resolved, move it into `architecture_decisions/`
as a new dated entry rather than just deleting it.
- Does `cg-link` treat an existing root level `AGENTS.md` as a managed file
  it will try to generate, or does it leave it alone as user owned content?
  Confirm this the first time `cg-link` runs in this repo, and resolve any
  conflict it reports manually rather than accepting a proposed overwrite.
