# 0003. Harmonization Specification as the central artifact

**Status.** Confirmed. Treat as settled unless explicitly reopened.
**Date confirmed.** Predates this repository; exact date not recorded.

**Decision.** The Harmonization Specification is the pivot artifact of the
whole system. The AI drafts it, a human expert approves or edits it, and a
separate deterministic engine executes it. Nothing runs in production
without human sign off. Every human override is stored back into the
historical database along with its justification.

**Why.** This keeps AI, human judgment, and execution as three clearly
separated steps, each auditable on its own, rather than one opaque process.
