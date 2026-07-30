# 0001. Two database architecture

**Status.** Confirmed. Treat as settled unless explicitly reopened.
**Date confirmed.** Predates this repository; exact date not recorded.

**Decision.** The system uses two separate databases with different
authority levels. A relational database holds the canonical schema and
its rules, and is always authoritative. A vector database holds historical
harmonization precedents, and is advisory only. When the two disagree, the
schema database wins.

**Why.** Rules and precedents serve different purposes. Rules must be
consistent and enforceable. Precedents are useful context but should never
override a documented rule, or the system would silently drift over time.
