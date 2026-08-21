# Context and Representation Revision — Analogy as Dynamic Belief Update

**Snapshot: 21 August 2026.**

Static analogy pipelines usually assume that source, target and background context are fixed before mapping. Recent work at the cognitive-systems / philosophy–AI boundary argues for a stronger model: analogical reasoning itself changes the contexts in which source and target are represented.

## 1. Zhu & Hong 2026 — context-update perspective

**Wensheng Zhu & Zhengyi Hong, _Analogical reasoning from a context-update perspective_, Cognitive Systems Research 97 (2026), 101479.**  
DOI: https://doi.org/10.1016/j.cogsys.2026.101479

The paper distinguishes three contexts represented as belief sets:

```text
C_S = source-domain context
C_T = target-domain context
C_R = reasoning/meta-level context
```

Analogy is reconstructed as a multi-stage update process using AGM-style operations:

```text
expansion
contraction
revision
```

rather than a one-shot similarity computation.

## 2. Dynamic similarity is an outcome of context update

On this view, the features that make two domains appear similar can change as source/target/reasoning belief sets are revised.

This is important for AI because it reverses a common assumption:

```text
similarity → reasoning
```

can become:

```text
reasoning/context revision ↔ similarity.
```

A system may discover a useful analogy only after dropping one target assumption, adding a source relation or revising the purpose of comparison.

## 3. Over-analogization as information loss

The paper uses context revision to explain erroneous analogy, including over-analogization. A revision process may discard propositions that would have preserved an inference-critical difference.

Engineering translation:

```text
failure is not always bad mapping;
it may be destructive context compression.
```

This suggests logging which propositions/relations are contracted or suppressed during abstraction/mapping.

A useful audit question is:

> Did the system produce a cleaner shared representation by deleting the very target difference that should have vetoed the projection?

## 4. Votsis 2025 — concept change and DNN feature change

**Ioannis Votsis, _Concept and Feature Change in Scientific and Deep Neural Net Representations_, CogSci 2025 Proceedings, pp. 1654–1660.**

Votsis compares changes in classical scientific concepts/representations with changes in DNN representations/features. The central claim is methodological: practices for evaluating useful conceptual/feature change may permit cross-pollination between philosophy of scientific representation and neural-network representation learning.

This makes representation revision a direct philosophy–AI question rather than an analogy-specific historical analogy.

## 5. A controller should distinguish three revisions

When transfer fails, at least three different things may need revision:

### Source revision

```text
our abstraction of S omitted a causal/functional condition.
```

### Target revision

```text
we represented T under the wrong ontology or abstraction level.
```

### Reasoning-context revision

```text
the purpose/relevance rule used to compare S and T was wrong.
```

These failures require different updates.

## 6. Typed failure attribution

A useful analogue controller can therefore return:

```yaml
failure_type:
  - SOURCE_REPRESENTATION
  - TARGET_REPRESENTATION
  - RELEVANCE_RULE
  - MAPPING
  - TRANSFER_APPLICABILITY
  - EXECUTION
revision_action:
  add_relation:
  remove_assumption:
  split_concept:
  merge_features:
  change_abstraction_level:
  retrieve_new_source:
```

This is stronger than storing `source S produced a bad answer`.

## 7. Revision should be empirically scored

Representation flexibility can easily become unconstrained post-hoc rationalization. A revision is useful only if it improves independent performance:

```text
held-out projection accuracy
forecast calibration
source retrieval stability
counterfactual/intervention prediction
cross-case reuse
```

A system should pay a complexity/ad-hoc cost for repeated bespoke rerepresentation that only repairs one failed item.

## 8. A minimal experiment

Construct matched analogy tasks where the initial representation hides a critical relation.

Compare:

```text
A. fixed representation + more reasoning tokens
B. permitted source rerepresentation
C. permitted target rerepresentation
D. permitted relevance-rule revision
```

Then evaluate whether the system chooses the correct revision type and whether that revision transfers to related cases.

## Bottom line

The live philosophy/cognitive-AI literature supports a stronger picture of analogy:

> **representation and context are state variables inside analogical reasoning, not merely inputs supplied before it begins.**

The next engineering problem is controlled rerepresentation: allow a system to revise source, target or relevance context after failure, while making those revisions typed, auditable and accountable to held-out evidence.