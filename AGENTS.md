# AGENTS.md — Operating Rules for AI Agents (Draft)

Read this file completely before reading anything else in this repository.

## What this repository is

This is the GMD Harmonization Hub. It is the central reference point for the
GMD AI assisted household survey harmonization project. It explains how the
canonical schema repository, the survey extraction repository, the
harmonization specification repository, and the historical knowledge base
fit together as one system, and it records the reasoning behind the major
design decisions that shape that system.

This repository contains no pipeline code of its own. Its role is to
explain, connect, and preserve reasoning, not to run anything.

## Before doing anything

1. Read this file completely.
2. Read `README.md` to understand the repo map and how each satellite
   repository relates to the others.
3. Read `architecture_decisions/` before proposing any change to an existing
   decision entry.
4. Never assume ITS infrastructure capabilities, GitHub Action permissions,
   or cross repo access that have not been explicitly confirmed by the user.
   If unsure, add the question to `open_questions.md` instead of guessing.

## Where agents are allowed to write

| Location | What goes here | Who writes |
|---|---|---|
| `sync_status/` | Machine generated facts only: last commit date, latest tag, link | Agent, direct commit |
| A pull request branch | Proposed updates to a repo summary after a satellite repo changes meaningfully | Agent drafts, human approves |
| `architecture_decisions/` | Log of confirmed design decisions, one dated entry each | Human authored. Agent may draft a new entry for review, never edit an existing one |
| `glossary.md` | Definitions of project vocabulary | Human authored. Agent may propose additions for review |
| `open_questions.md` | Unresolved items | Human authored. Agent may propose additions for review |
| `for_collaborators/` | Role specific guidance for focal points, ITS, and team members | Human authored. Agent may draft for review |
| `diagrams/` | Visual diagrams of the pipeline and repo relationships | Agent may draft, human reviews before merging |

Agents write freely only to `sync_status/`. Everything else goes through a
pull request or a direct draft that the user reviews before it is merged.

## What always requires human approval

- Any new or modified file outside `sync_status/`
- Any change to an existing entry in `architecture_decisions/`
- Any addition to `glossary.md` or `open_questions.md`
- Any change to this file

## What agents must never do

- Silently update a narrative summary of a satellite repo without opening a
  pull request for review
- Invent or assume facts about ITS infrastructure, Azure services, or GitHub
  Action permissions that have not been confirmed
- Store pipeline code, notebooks, or scripts here. That belongs in the
  satellite repos
- Duplicate content that already lives in a satellite repo README. Summarize
  briefly in two or three sentences and link out instead
- Draft or restate harmonization rules. This repository documents the
  system. It is not the source of methodological content, which belongs to
  the regional focal points and lives in the canonical schema repository

## Source of truth

For the harmonization rules themselves, defer to the canonical schema
repository and its own `AGENTS.md`. This hub explains and connects the
pieces of the system. It does not override the authority of any satellite
repository on its own subject matter.

## Relationship to Compound GPID

This team uses Compound GPID, a Copilot plugin that manages its own working
memory in `.cg-docs/` and a project charter in `compound-gpid.md`. Those
serve a different purpose than this file and the `architecture_decisions/`
folder. `.cg-docs/` holds artifacts from individual brainstorm, plan, and
review sessions. `architecture_decisions/` holds only confirmed, stable
decisions about the system as a whole. Do not let the two folders merge or
duplicate each other. If Compound GPID proposes changes to this file during
`cg-link`, review them manually before accepting.
