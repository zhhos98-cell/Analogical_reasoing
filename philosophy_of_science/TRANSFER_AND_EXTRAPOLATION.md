# Transfer and Extrapolation — The Closest Philosophy-of-Science Neighbor to AI Transfer Validity

**Snapshot: 21 August 2026.**

Scientific extrapolation asks a structurally familiar question:

> Results were established in source population/system `S`. Under what conditions can they support a conclusion about target `T`?

This literature is especially valuable because it refuses to collapse the problem into source–target similarity.

## 1. Three problems, not one

Jonathan Fuller (2025) distinguishes:

### Logical problem

What extrapolation argument would be valid if its premises were true?

Generic form:

```text
A. source/study result
B. source–target comparability premises
C. target conclusion
```

### Evidential problem

What evidence actually supports the comparability premises in B?

### Practical problem

Given incomplete evidence and uncertainty, when is it reasonable to accept/use the extrapolated conclusion?

This tripartite distinction maps almost directly onto an AI controller:

```text
logical     → what projection follows under mapping M?
evidential  → what source/target evidence supports M's applicability?
practical   → license / condition / veto / abstain at this uncertainty level?
```

## 2. Why this matters for benchmark design

A model may generate a perfectly coherent transfer contract using assumptions it invented itself.

That is not evidence.

A benchmark should therefore distinguish:

```text
projection correctness
comparability-premise correctness
supporting-evidence quality
final calibrated transfer decision
```

An analogy chain cannot earn full credit merely because its prose contains a mechanism that, if true, would justify the answer.

## 3. The extrapolator's circle

A persistent challenge is to establish source–target comparability without already possessing enough target knowledge to infer the target conclusion independently, which would make the source study redundant.

This is useful for AI because an LLM can easily generate circular justification:

```text
S transfers to T because T has mechanism X.
How do we know T has X?
Because T behaves like S.
```

A robust system needs an evidence path in which the comparability evidence is not merely a paraphrase of the projected conclusion.

## 4. Structural analogies as evidence for causal comparability

Fuller proposes structural analogies as a route to the evidential problem: structural similarity can sometimes support the claim that factors in source and target play corresponding causal roles.

But the required similarity depends on what is being transferred.

A qualitative causal-role projection may need weaker structural evidence than a quantitative effect-size projection.

This gives a direct AI design principle:

```text
transfer burden depends on projection granularity.
```

For example:

```text
p1: mechanism direction transfers
p2: rank ordering transfers
p3: numerical effect size transfers
```

should require progressively stronger evidence rather than inherit one source-level analogy score.

## 5. Uncertainty over extrapolation assumptions

Khosrowi (2023) emphasizes that real extrapolation relies on assumptions whose truth is often uncertain. His support-graph approach is designed to articulate and manage those uncertainties in a unified way.

The important lesson is not to import one specific graph formalism unchanged. It is that a transfer controller should expose uncertainty at the level of assumptions/support links:

```text
A1: role r exists in target — 0.78
A2: downstream mechanism remains undisrupted — 0.55
A3: relevant cofactor distribution is comparable — 0.42

projection p depends on A1,A2,A3
```

This is much more informative than `analogy confidence = 0.73`.

## 6. Problem of difference

Negro & Mudrik (2026) argue that extrapolating consciousness to animals, organoids or AI systems exposes the limits of ordinary analogy. Structural similarities may matter, but there is no simple, general similarity threshold that guarantees extrapolation. They propose **analogical abduction**: analogy participates in explanatory competition rather than settling the inference alone.

Engineering translation:

```text
source analogy proposes a target hypothesis
→ compare hypothesis with alternative explanations
→ ask whether target evidence discriminates them
```

This is another reason a historical/scientific analogue controller needs counter-hypotheses, not only better matching.

## 7. Target-side validation

The extrapolation literature makes explicit something analogy benchmarks often blur: source evidence can justify trying a target inference without settling it permanently.

A mature controller should therefore produce:

```text
projected target claim
current license strength
key assumptions
target-side discriminating evidence
what observation would reduce/revoke the license
```

This naturally supports active experimentation or evidence acquisition.

## 8. Engineering synthesis

A philosophy-of-science-inspired transfer object could be:

```yaml
source_result: ...
projection: ...
logical_transfer_rule: ...
comparability_assumptions:
  - assumption:
    support:
    uncertainty:
    falsifier:
critical_differences:
status: LICENSED | CONDITIONAL | VETOED | UNKNOWN
probability:
target_test:
```

This is essentially a **typed external-validity contract**.

## Bottom line

The extrapolation literature strongly suggests that the difficult AI problem is not `find a similar source`. It is:

> **separate the logic of transfer from the evidence that warrants its premises, propagate uncertainty over those premises, and preserve a target-side route for testing or revoking the projection.**

That is almost exactly the gap exposed by the modern analogy and historical-analogy branches.