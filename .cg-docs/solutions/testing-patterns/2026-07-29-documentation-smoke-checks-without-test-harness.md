---
date: 2026-07-29
title: "Documentation smoke checks when navigation changes have no test harness"
category: "testing-patterns"
language: "both"
tags: [documentation, smoke-checks, navigation, markdown-links, quarto, review]
root-cause: "Navigation-heavy documentation changes relied on file-existence and diff checks only, while the repository had no tests/Run-Tests.ps1 harness to validate markdown-link paths or render-oriented smoke behavior."
severity: "P3"
---

# Documentation smoke checks when navigation changes have no test harness

## Problem

A documentation-only change added new navigation edges to `system_map.md`,
`README.md`, and the glossary/open-questions split. Review found that the
change had no explicit smoke-check convention for links or navigation behavior.
The repository also had no `tests/` directory, so the standard targeted and
full-suite `Run-Tests.ps1` workflow was unavailable.

## Root Cause

The review and work workflows assumed that normal file-existence checks,
`git diff --check`, and diagnostics were enough for a docs-only change.
That left a gap for documentation navigation changes: relative links and
orientation paths can still be wrong even when markdown files exist and lint
cleanly. Because this repo has no test harness, that validation gap was not
covered elsewhere.

## Solution

Capture and document a lightweight smoke-check procedure in the repository
README so future navigation or link-oriented documentation changes have an
explicit validation step even without a formal test suite.

Use a small command set that verifies the expected files exist and that the
primary navigation anchor is present:

```sh
test -f README.md
test -f system_map.md
test -f glossary_and_questions/glossary.md
test -f glossary_and_questions/open_questions.md
grep -n '\[system_map.md\](system_map.md)' README.md
```

For canonical Quarto document edits, extend the smoke check by running the
existing render commands already documented in the repository:

```sh
quarto render canonical/system-architecture.qmd --to html \
    --output-dir ../build -M embed-resources:true
quarto render canonical/infrastructure-requirements.qmd --to html \
    --output-dir ../build -M embed-resources:true
```

## Prevention

- When a docs change adds or rewires navigation, treat it like a testable
  change even if no code changed.
- If the repository has no `tests/` harness, add a documented smoke-check
  recipe near the maintenance or rendering instructions rather than relying on
  implicit reviewer judgment.
- Keep smoke checks anchored to the concrete links introduced by the change.
- Do not let glossary entries settle open design questions; pair docs
  validation with wording checks when review identifies authority drift.

## Related

- `README.md` documentation smoke checks section.
- `.cg-docs/solutions/testing-patterns/2026-07-30-markdown-links-in-doc-indexes-enable-smoke-checks.md`
- `.cg-docs/reviews/2026-07-29-incorporate-system-map-review.md`
- `.cg-docs/plans/2026-07-29-incorporate-system-map.md`
