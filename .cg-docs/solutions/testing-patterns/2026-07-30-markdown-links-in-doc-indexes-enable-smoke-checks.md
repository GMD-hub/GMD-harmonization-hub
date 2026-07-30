---
date: 2026-07-30
title: "Markdown links in documentation indexes create a real smoke-check surface"
category: "testing-patterns"
language: "both"
tags: [documentation, markdown-links, smoke-checks, navigation, indexes, review]
root-cause: "A documentation index listed important source and basis artifacts as plain text, so review could not validate actual navigation targets even though file-existence and diff checks passed."
severity: "P3"
---

# Markdown links in documentation indexes create a real smoke-check surface

## Problem

A documentation review flagged that a new index of diagram artifacts used plain
text filenames and basis references instead of real markdown links. The
repository already had a lightweight smoke-check convention for docs-only
changes, but that convention could only validate concrete navigation anchors.
Because the index exposed text rather than links, the new documentation surface
was only partially testable.

## Root Cause

The documentation change focused on content completeness and visual clarity, but
treated the index as descriptive text instead of a navigable interface. In a
docs-only repository without a formal test harness, that distinction matters:
smoke checks can validate real links, not intended destinations inferred from
plain text.

## Solution

Convert source, export, and authoritative-basis references in documentation
indexes to explicit markdown links whenever those references are part of the
intended navigation surface.

For the diagram index pattern, this means linking:

```md
| Diagram | Canonical editable source | Rendered export | Authoritative basis |
|---|---|---|---|
| Three-schema harmonization flow | [three-schema-harmonization-flow.excalidraw](three-schema-harmonization-flow.excalidraw) | [three-schema-harmonization-flow.svg](three-schema-harmonization-flow.svg) | [canonical/system-architecture.qmd](../canonical/system-architecture.qmd), [system_map.md](../system_map.md), [README.md](../README.md) |
```

Then extend the lightweight smoke check to verify one or more concrete links
introduced by the index:

```sh
test -f diagrams/README.md
test -f diagrams/three-schema-harmonization-flow.excalidraw
test -f diagrams/three-schema-harmonization-flow.svg
grep -n '\[three-schema-harmonization-flow.excalidraw\](three-schema-harmonization-flow.excalidraw)' diagrams/README.md
grep -n '\[canonical/system-architecture.qmd\](../canonical/system-architecture.qmd)' diagrams/README.md
```

## Prevention

- Treat documentation indexes as navigation surfaces, not only prose tables.
- If a reader is expected to navigate from the index, prefer markdown links to
  plain text filenames.
- Pair docs-review fixes with smoke checks that verify the exact anchors added
  by the change.
- In documentation-only repositories, distinguish between "the file exists" and
  "the documentation exposes a verifiable path to the file."

## Related

- [.cg-docs/solutions/testing-patterns/2026-07-29-documentation-smoke-checks-without-test-harness.md](../testing-patterns/2026-07-29-documentation-smoke-checks-without-test-harness.md)
- [.cg-docs/reviews/2026-07-29-incorporate-system-map-verify-review.md](../../reviews/2026-07-29-incorporate-system-map-verify-review.md)
- [diagrams/README.md](../../../diagrams/README.md)