# Representation and Similarity — Before Mapping Begins

**Snapshot: 21 August 2026.**

Many computational treatments begin with source and target representations already fixed. Contemporary philosophy of scientific analogy repeatedly shows that this assumption hides a large part of the epistemic problem.

## 1. Climate analogues: the representation problem in applied form

**Valente, Bobadilla, El Skaf & Nappo, _Tales of twin cities: what are climate analogues good for?_ EJPS 14:34 (2024).**  
DOI: https://doi.org/10.1007/s13194-024-00597-2

Spatial climate-analogue methods select a present source location whose climate resembles the projected future climate of a target location, then use the source to reason about target impacts/adaptation.

The paper identifies five problems:

1. **non-uniqueness of the source**;
2. **non-uniqueness of the target**;
3. **problem of average**;
4. **non-causal correlations**;
5. **problem of inferred properties**.

These are remarkably close to current AI analogue failures.

## 2. Source non-uniqueness

Different metrics/variables can produce different best source analogues.

Engineering translation:

```text
retrieval result is conditional on representation + metric.
```

A system should expose source-rank sensitivity to:

- variable choice;
- abstraction level;
- metric;
- contextual constraints.

A single top-1 analogue should not be mistaken for an objective property of the world.

## 3. Target non-uniqueness

Even the target's relevant future/state representation may be uncertain.

This matters in AI because source retrieval often begins from an LLM-generated target abstraction. If several plausible target representations exist, they may retrieve different source sets.

A mature system should support:

```text
R_T1 → source set A
R_T2 → source set B
```

and track how transfer conclusions depend on that choice.

## 4. Average similarity can destroy inferential structure

A geometrical distance can aggregate many features into one score while hiding which dimension is doing the work.

This is especially dangerous when the intended inference crosses levels — for example from physical climate resemblance to socioeconomic vulnerability.

AI analogue:

```text
embedding similarity
≠
mechanism similarity
≠
projection relevance.
```

## 5. Non-causal correlation

Two systems can occupy nearby positions in feature space for reasons unrelated to the mechanism needed for a projection.

This is the exact point at which similarity-based retrieval must hand off to causal/mechanistic or evidential adjudication.

## 6. Inferred properties

Even after a good analogue is found, the property we want to transfer may not be among the properties warranted by the established resemblance.

This is perhaps the closest philosophy-of-science formulation of **projection-level transfer validity**:

```text
S is a good analogue of T for dimensions X,Y
```

does not entail:

```text
property Z observed in S may be inferred in T.
```

The target property needs its own inferential bridge.

## 7. Set-valued analogue retrieval

Valente et al. recommend presenting a **set of plausible analogues** constrained by local knowledge rather than forcing one unique best source.

This matches several AI design lessons:

- retrieve diverse candidates;
- preserve alternative representations;
- use local/domain context to constrain plausibility;
- compare which projection each source actually supports.

## 8. Biomedical similarity: metric choice is epistemic

**Boniolo, Boniolo & Valente, _Prediction via Similarity: Biomedical Big Data and the Case of Cancer Models_ (2023).**  
DOI: https://doi.org/10.1007/s13347-023-00608-9

Their analysis of k-nearest-neighbour cancer models emphasizes that predictions depend on a geometrical similarity metric. Whether the target patient is genuinely comparable to the retrieved cluster, and whether the resulting prediction is reliable, remains an empirical/epistemic issue rather than something settled by nearest-neighbour computation alone.

Engineering translation:

```text
retrieval metric is part of the scientific hypothesis.
```

It should be benchmarked and falsifiable, not treated as infrastructure outside the reasoning problem.

## 9. Conceptual revision can reverse an analogy's evidential role

**True Gibson, _Conceptual revision: how Darwin's analogy supported his theory_ (2025).**  
DOI: https://doi.org/10.1007/s10539-025-09988-y

Gibson argues that Darwin's artificial-selection analogy initially appeared to count against natural selection for many contemporaries. Only after substantive revisions to how artificial selection, variation and geological time were conceptualized could the same broad analogy support Darwin's target theory.

This is an important warning against a fixed pipeline:

```text
represent once → map → score.
```

Sometimes evidence forces:

```text
represent → map → discover contradiction
→ revise concept/representation
→ remap
→ evidential role changes.
```

## 10. Engineering implications

A representation-aware analogy system should log at least:

```yaml
target_representation:
alternative_target_representations:
source_representation:
similarity_dimensions:
metric_or_mapping_rule:
rank_sensitivity:
contextual_constraints:
projection_being_transferred:
```

and permit transfer failure to trigger representation revision.

## Bottom line

The contemporary philosophy-of-science literature makes an upstream point that is easy to lose in benchmarked AI:

> **The objects being compared, the dimensions on which they are similar, and the property to be projected are all theory- and context-sensitive choices.**

Therefore representation selection is not merely a precursor to analogical reasoning. In many scientific cases it is part of the reasoning itself.