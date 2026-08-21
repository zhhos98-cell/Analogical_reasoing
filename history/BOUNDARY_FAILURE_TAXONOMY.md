# Boundary Failure Taxonomy — Where Does Historical/Pattern Transfer Actually Break?

**Snapshot: 21 August 2026.**

Resolved forecasting failures show that `bad historical transfer` is not one error type. The same wrong final probability can arise at different pipeline stages.

A useful diagnostic decomposition is:

```text
BOUNDARY SEARCH
→ BOUNDARY REPRESENTATION
→ BOUNDARY-TO-PROJECTION LINK
→ PROBABILITY UPDATE
→ FINAL COMMITMENT
```

The controller should attribute failure to the earliest broken stage rather than treating every error as `bad analogy`.

---

## F1 — Boundary evidence not retrieved

The system anchors on a historical/base-rate pattern and never retrieves the target-side fact that changes its applicability.

### Example: Brazil green bill / COP30

In a BTF-2 forecast, one Claude Opus 4.6 run anchored on the bill's history of being scheduled but not voted and forecast roughly 30% passage. Across 17 searches it did not query `COP30`, `climate`, or `Belém` even though COP30 was the major target-specific driver of passage. Another run explored different context; ensembling improved performance.

Source: FutureSearch, **“Run agents twice for fun and profit,”** 1 May 2026.  
https://futuresearch.ai/blog/run-agents-twice/

Failure location:

```text
source pattern found
critical target driver NOT retrieved
→ target representation incomplete
```

Correct repair:

```text
RESEARCH / RETRIEVE AGAIN
```

not merely `lower analogy confidence`.

---

## F2 — Boundary evidence retrieved but not represented as a transfer condition

The research contains the relevant fact, but the system does not encode it as changing the generating process.

This can happen when evidence remains an isolated sentence rather than becoming a state/phase/mechanism variable.

Correct repair:

```text
REREPRESENT target
```

or

```text
ADD boundary condition X to transfer contract
```

---

## F3 — Boundary represented but veto/conditional update not executed

This is the clearest historical-transfer failure.

### EU Iran sanctions

The model's own research recognized that the September sanctions package was comprehensive, deadline-driven and could reduce immediate need for another action. It still gave **95% Yes**, treating the prior cadence as dominant.

Pipeline diagnosis:

```text
pattern retrieved ✓
boundary retrieved ✓
boundary represented ✓
projection dependency understood at least partly ✓
probability/veto update ✗
```

Correct repair:

```text
APPLY VETO / strong downweight
```

This is the strongest real-world seed for `difference known → transfer control fails`.

---

## F4 — Scheduled phase transition acknowledged but continuation extrapolated through it

### Argentine peso

The model knew an election was six days away but projected a five-day panic/depreciation trajectory through the election boundary with **85% Yes**.

This is a phase-sensitive subtype:

```text
pre-juncture dynamic
→ known critical juncture
→ model treats process as stationary
```

Correct repair:

```text
CONDITIONAL forecast
branch on post-juncture regimes
increase uncertainty
```

---

## F5 — Reference class not revised after structural change

### NYC turnout

The post-2001 turnout ceiling was historically real, but the competition/mobilization structure generating that ceiling changed in 2025.

Failure:

```text
historical class C retained
although target no longer satisfies the class-defining mechanism
```

Correct repair:

```text
REDEFINE REFERENCE CLASS
```

rather than simply `ignore history`.

---

## F6 — Correct evidence/derivation, incorrect probability integration

A model can find the right target evidence and even perform the right calculation while final confidence contradicts it.

### NYC turnout — underconfidence analysis

FutureSearch reports that Opus found approximately 1.1m primary ballots and a historical primary→general ratio around 1.22, yielding roughly 1.34m — already above the 1.3m threshold. The model wrote the calculation, called it unstable, and still issued **25% Yes**. Actual turnout exceeded 2m.

Source: FutureSearch, **“Some rare examples of AIs being underconfident,”** 6 May 2026.  
https://futuresearch.ai/blog/ais-underconfident/

This is not a retrieval failure or necessarily an analogy failure. It is:

```text
valid evidence / calculation
→ final probabilistic integration inconsistent
```

Correct repair:

```text
CALIBRATE / enforce rationale–probability consistency
```

---

## F7 — Projection scope mismatch

A system may analyze an extreme version of the target event and then apply that evidence to a broader question.

FutureSearch's `catastrophizing` cases have this shape: evidence against a full-scale or extreme scenario is used to lower the probability of a much weaker threshold event.

This is structurally analogous to claim-strength mismatch:

```text
source/evidence addresses claim C_strong
model uses it for C_weak
```

Correct repair:

```text
ALIGN EVIDENCE WITH CLAIM SCOPE
```

---

# 8. Typed repair policy

A mature controller should select a repair action based on the diagnosed stage.

| Failure | Repair |
|---|---|
| F1 boundary not retrieved | `SEARCH_BOUNDARY_EVIDENCE` |
| F2 boundary not represented | `REREPRESENT` |
| F3 veto not executed | `UPDATE_TRANSFER_LICENSE` |
| F4 phase transition ignored | `BRANCH_ON_PHASE / CONDITIONALIZE` |
| F5 bad reference class | `REBUILD_REFERENCE_CLASS` |
| F6 probability integration error | `RECALIBRATE / CONSISTENCY_CHECK` |
| F7 claim-scope mismatch | `RETARGET_EVIDENCE / CLAIM` |

This is a direct bridge to the broader repo's typed failure-credit-assignment problem.

---

# 9. Training data format

Resolved failure traces can be stored as:

```yaml
case_id:
source_pattern:
projection:
final_probability:
outcome:

stage_states:
  boundary_retrieved: true|false
  boundary_represented: true|false
  projection_dependency_linked: true|false
  probability_updated: true|false
  final_commitment_consistent: true|false

failure_type: F1..F7
repair_action:
```

The target is not only `correct final answer`; it is **correct repair action after diagnosis**.

---

# 10. Why this matters for analogue-memory learning

If an Iran-sanctions failure is incorrectly stored as:

```text
historical recurrence is unreliable
```

the memory will overgeneralize.

Correct memory is:

```text
recurrence pattern remains useful
BUT terminal/deadline completion is a boundary condition
AND projections past that state must be downweighted
```

Likewise, if the Brazil case is stored as `past legislative failures were misleading`, it misses the actual error: **the agent did not retrieve the new driver**.

Typed failure attribution is therefore necessary before persistent applicability memory can work.

---

## Bottom line

Historical-transfer errors should be diagnosed at the earliest broken stage:

> **Did the system fail to find the boundary, fail to represent it, fail to connect it to the projected claim, fail to update probability, or fail only at final commitment?**

Those failures require different repairs and should not all train the model to reject the source analogy.
