# 0002. Atomic mapping only

**Status.** Confirmed. Treat as settled unless explicitly reopened.
**Date confirmed.** Predates this repository; exact date not recorded.

**Decision.** The AI maps raw survey variables only to atomic, leaf node
GMD variables. Derived or aggregate variables are always computed
deterministically in code from atomic variables, never mapped to directly.

**Why.** Letting the AI map to high level aggregates would hide the actual
construction logic inside a black box decision. Keeping derivation in
deterministic code keeps every harmonized value traceable back to its
atomic inputs.
