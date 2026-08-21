# Comparative Process Tracing — A Mechanism-Level Transfer Controller

**Snapshot: 21 August 2026.**

Comparative process tracing (CPT) is one of the closest philosophy-of-science analogues to the engineering problem of projection-level transfer validity.

The central problem is the **extrapolator's circle**:

```text
we want to know whether source result S transfers to target T
but to know that source and target are similar in the causally relevant respects
seems to require already knowing the target mechanism
```

Daniel Steel's mechanisms-based extrapolation strategy and Francesco Guala's reconstruction of it show that this circle can sometimes be weakened by **selective comparison of mechanism stages**, not by establishing overall similarity.

---

## 1. Core idea

Suppose a source mechanism is represented as:

```text
C → X → Y → Z → E
```

A naive transfer test asks whether the whole source and target mechanisms are sufficiently similar.

CPT asks a narrower question:

> **Where are source and target most likely to differ in a way that would alter the projection?**

Researchers then inspect those strategically chosen stages. One need not know or match the complete target mechanism.

The SEP literature on mechanisms summarizes Steel's strategy as focusing on key similarities and likely difference points. If an intermediate stage is established in the target, uncertainty about source–target differences can sometimes be localized downstream of that point.

### AI translation

Do not require the model to generate a complete target DAG before deciding whether to transfer.

Instead learn:

```text
projection p
→ candidate causal pathway
→ high-risk difference nodes / bottlenecks
→ acquire/check target evidence at those nodes
→ update transfer license for p
```

This is potentially much more tractable than whole-event causal equivalence.

---

## 2. Fingerprints rather than global similarity

Steel's chain-graph formulation introduces **fingerprints / distinctive markers** as a way to avoid spurious analogy.

The basic idea is that a distinctive downstream pattern may be diagnostic of the mechanism/process that generated it.

Rather than:

```text
S and T look similar overall
```

ask:

```text
Does T exhibit the distinctive marker expected if the source-side mechanism really operates there?
```

This is extremely close to a target-side validation query.

### Engineering form

For source mechanism `M_s` and projected claim `p`:

```yaml
hypothesized_shared_mechanism: M
predicted_fingerprint: F
observed_target_evidence: E
fingerprint_match: yes/no/uncertain
transfer_update: increase/decrease/hold
```

The key is that the analogue itself predicts **what evidence should be searched for in the target**.

---

## 3. Difference localization

One of CPT's most useful intuitions is that source–target differences need not invalidate every projection.

If a difference occurs at mechanism stage `Y`, projections depending only on upstream `C→X` may survive while projections depending on `Y→Z→E` fail.

That yields exactly the partial-transfer logic needed by the AI benchmark:

```text
source S
projection p1 depends on path C→X            → may remain LICENSED
projection p2 depends on path C→X→Y→Z        → CONDITIONAL / VETOED if Y differs
```

This is stronger than whole-source accept/reject.

---

## 4. Relation to current AI failures

Resolved forecasting failures such as the BTF pattern-break cases have the same shape:

```text
historical/recent pattern was genuine
critical target-side boundary evidence existed
model failed to let the boundary modify the projection
```

CPT suggests a better controller architecture:

1. infer the process that generated the source pattern;
2. identify likely breakpoints when moving to target;
3. query evidence specifically at those breakpoints;
4. bind each projected claim to the mechanism stages it depends on;
5. update only affected projections.

This converts `difference awareness` into **causal credit assignment**.

---

## 5. Comparison with full causal-graph generation

A full event graph asks the model to solve too much at once:

```text
recover all relevant causal nodes and edges
+ decide which source nodes correspond to target nodes
+ decide which differences matter
+ derive future projections
```

CPT offers a weaker epistemic target:

```text
find enough discriminating mechanism information to license or block this projection
```

This is more compatible with open-world uncertainty.

A system can explicitly say:

```text
Full target mechanism unknown.
Projection p depends on stages X and Y.
Evidence supports X.
Y is unresolved and is a plausible source–target divergence point.
Status: UNKNOWN / acquire evidence about Y.
```

---

## 6. Active evidence acquisition

CPT naturally yields an **active reasoning policy**.

Instead of searching for more generic information, select the evidence query with highest expected transfer-disambiguation value:

```text
q* = argmax_q E[ reduction in uncertainty about transfer(p) | answer(q) ]
```

Candidate questions target:

- mechanism bottlenecks;
- scheduled regime transitions;
- terminal states;
- actor/institution changes;
- causal direction;
- mediator/moderator activation;
- fingerprints that discriminate competing pathways.

This links philosophy of extrapolation directly to active search / research-agent design.

---

## 7. What CPT does not solve

CPT assumes we have enough background knowledge to identify:

- a plausible source mechanism;
- likely source–target difference points;
- which mechanism stages control the projected outcome;
- informative fingerprints.

Foundation models can generate these candidates, but that does not make them reliable.

A modern controller therefore needs uncertainty over the **process-tracing model itself**:

```text
R1: mechanism representation 0.50
R2: alternative representation 0.30
R3: alternative representation 0.20
```

and should choose evidence that discriminates not only transfer status but competing representations.

---

## 8. Benchmark translation

Add a `mechanism_breakpoint` track to Historical Transfer Bench / general analogical-transfer evaluation.

Each item contains:

```yaml
source_pathway:
projection:
projection_dependency_nodes:
candidate_difference_nodes:
critical_difference_node:
target_evidence:
diagnostic_fingerprint:
```

Metrics:

- breakpoint localization accuracy;
- projection-specific boundary response;
- evidence-query efficiency;
- fingerprint selection precision;
- false whole-source rejection rate;
- transfer calibration after evidence acquisition.

---

## 9. Why this matters for the PoS→AI bridge

CPT changes the engineering question from:

> **Are source and target sufficiently similar?**

into:

> **Which parts of the source process does this projected claim rely on, where could target divergence break that process, and what evidence would tell us?**

That is a much better formulation of open-world analogical transfer.

---

## Core references

- Daniel Steel, *Across the Boundaries: Extrapolation in Biology and Social Science* (2008).
- Daniel Steel, “A New Approach to Argument by Analogy: Extrapolation and Chain Graphs,” *Philosophy of Science* 77(5), 2010. DOI: https://doi.org/10.1086/656543
- Francesco Guala, “Extrapolation, Analogy, and Comparative Process Tracing,” *Philosophy of Science* 77(5), 2010. DOI: https://doi.org/10.1086/656541
- Wendy S. Parker, “Comparative Process Tracing and Climate Change Fingerprints,” *Philosophy of Science* 77(5), 2010.
