# 0004. Legacy script ingestion pipeline

**Status.** Confirmed. Treat as settled unless explicitly reopened.
**Date confirmed.** Predates this repository; exact date not recorded.

**Decision.** Legacy Stata do files are ingested through a fixed sequence:
a do2screen parser extracts structural logic, an LLM interprets that logic
into a plain language explanation, a human reviewer validates the
interpretation, and only then does it enter the historical database.

**Why.** Legacy scripts vary enormously in quality. Requiring human
validation before anything enters the historical database prevents low
quality extractions from quietly contaminating future AI drafts.
