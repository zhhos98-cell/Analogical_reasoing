# Localism and Context — One Control Schema, Domain-Specific Evidence Rules

**Snapshot: 21 August 2026.**

A recurring temptation in AI is to search for a universal scalar rule for analogy quality. Contemporary philosophy of science gives strong reasons to resist that ambition.

## 1. Archaeoastronomy as a worked historical-science case

**Nappo, Magli & Valente, _Evidence and analogy in Archaeoastronomy_, Synthese 200:439 (2022).**  
DOI: https://doi.org/10.1007/s11229-022-03863-z

The paper asks when analogies between a better-understood civilization/source and a poorly understood historical target can support claims about the target's intentions, meanings or astronomical practices.

It distinguishes direct analogies with historical/geographical lineage from indirect analogies where no such relation exists. Importantly, indirect does not simply mean weak: different kinds of background knowledge can make an indirect analogy evidentially useful.

## 2. Analogy needs a bridgehead and contextual evidence

The paper describes analogical research as identifying a **bridgehead** linking observed target features with a familiar source, then transferring and revising source meanings where appropriate.

But a striking resemblance alone is insufficient. Converging contextual evidence can strengthen, weaken or reshape the inference.

This provides a useful AI separation:

```text
bridgehead / mapping
≠
contextual warrant for the projected interpretation.
```

## 3. Localism

The authors explicitly favor a **localist epistemology** of analogy.

On this view, an analogical inference is not justified merely because it instantiates one universal formal schema. Its epistemic status depends on:

- the background knowledge available in the field;
- which similarities matter to the conclusion;
- field-specific norms for responsible inference;
- the relation between known and predicted similarities;
- converging evidence.

This suggests an architecture principle:

```text
portable control protocol
+
domain-local evidential policy
```

rather than:

```text
one universal analogy score.
```

## 4. Direct and indirect sources may require different warrants

A direct historical analogue can receive support from genealogy/continuity. An indirect analogue needs a different bridge, such as shared environmental pressure, recurring functional demands or a broader uniformity in behavior.

Engineering translation:

```text
source relation type
→ changes what evidence can license transfer.
```

The system should record whether a mapping is supported by:

- common lineage;
- shared mechanism;
- convergent constraint;
- structural isomorphism;
- functional role;
- statistical recurrence;
- other domain-specific grounds.

These are not interchangeable.

## 5. Multiple imperfect analogues

The discussion draws on Currie's strategy of reconstructing a unique target by combining several imperfect sources, each informative about a different feature.

This is highly relevant to multi-precedent AI:

```text
S1 supports p1
S2 supports p2
S3 challenges p3
```

rather than forcing one source to be a global analogue of the target.

The key control problem becomes **composition of partial analogues** and management of their dependence/failures.

## 6. Self-correction rather than guaranteed validity

The localist position is not permissivism. The point is that fallible analogical practices can contain norms for their own correction: relevant similarities, contextual backing, robustness and additional evidence can constrain error.

This matches a continual controller better than a one-shot classifier:

```text
propose analogue
→ expose warrant
→ gather context
→ revise transfer
→ test target prediction
→ update applicability boundary.
```

## 7. Implication for the repo's benchmarks

The same `LICENSED / CONDITIONAL / VETOED / UNKNOWN` schema can be portable across domains, but the evidence required for each label should differ.

Examples:

### Historical event analogy

Evidence may include institutional lineage, chronology, actors, policy diffusion, contemporaneous sources.

### Biomedical extrapolation

Evidence may include biological structure, mechanism stages, cofactor distribution, intervention pathway.

### Climate analogue

Evidence may include physical-climate variables, local socioeconomic structure, adaptation capacity.

### Analogue experiment in physics

Evidence may include theoretical universality, shared equations/causal structure, robustness under perturbation.

The **state space is general; the warrant rules are local**.

## Bottom line

Localism suggests a useful compromise between two bad engineering extremes:

```text
one opaque universal analogy score
```

and

```text
a completely different system for every domain.
```

The more plausible target is:

> **a shared transfer-control grammar whose evidential predicates, thresholds and falsifiers are learned or specified locally for each scientific domain.**