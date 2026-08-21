# Philosophy of Science — Analogy, Extrapolation and Transfer

**Snapshot: 21 August 2026.**

This branch maps contemporary philosophy of science as a technical neighbor of modern AI analogical reasoning. It is not a history-of-ideas branch and is not organized by canonical thinkers.

The central question is:

> **What does contemporary philosophy of science say must be true before evidence, mechanisms or outcomes observed in a source can legitimately support a claim about a target?**

That question is very close to the current AI frontier around open-world source→target transfer validity.

## Start here

- [`CURRENT_MAP.md`](CURRENT_MAP.md) — eight-part decomposition of the current epistemology of analogy/transfer.
- [`FORMAL_CONFIRMATION.md`](FORMAL_CONFIRMATION.md) — Bayesian confirmation, formal analogical inference and why similarity is not itself confirmation.
- [`BACKGROUND_META_RULES.md`](BACKGROUND_META_RULES.md) — a candidate relevance layer between mapping and projection: what background rule makes a shared feature informative about the projected one?
- [`TRANSFER_AND_EXTRAPOLATION.md`](TRANSFER_AND_EXTRAPOLATION.md) — external validity, the logical/evidential/practical problems of extrapolation, uncertainty and target-side evidence.
- [`REPRESENTATION_AND_SIMILARITY.md`](REPRESENTATION_AND_SIMILARITY.md) — source/target non-uniqueness, metric dependence, inferred properties and conceptual revision.
- [`CONTEXT_AND_REPRESENTATION_REVISION.md`](CONTEXT_AND_REPRESENTATION_REVISION.md) — source/target/reasoning context as revisable state; connects AGM-style belief update, over-analogization and DNN feature change.
- [`LOCALISM_AND_CONTEXT.md`](LOCALISM_AND_CONTEXT.md) — a portable transfer-control grammar with domain-local evidential rules rather than one universal analogy score.
- [`ROBUSTNESS_AND_MULTI_ANALOGUE.md`](ROBUSTNESS_AND_MULTI_ANALOGUE.md) — why agreement among several analogues is not automatically several independent confirmations; includes 2026 inferential rules for what robustness can establish.
- [`ANALOGUE_EXPERIMENTS.md`](ANALOGUE_EXPERIMENTS.md) — plausibility, model-external support and external validation as distinct transfer states.
- [`FROM_NORMS_TO_REWARDS.md`](FROM_NORMS_TO_REWARDS.md) — separates PoS distinctions already mirrored by modern training methods from still-hypothetical reward/control signals.
- [`PROGRAM_AND_AI_BRIDGE.md`](PROGRAM_AND_AI_BRIDGE.md) — current research network around scientific analogy and its explicit AI interfaces.
- [`../data/philosophy_of_science_analogy.csv`](../data/philosophy_of_science_analogy.csv) — structured literature map.

## Current high-level result

Contemporary philosophy of science does **not** treat analogical inference as a scalar function of source–target resemblance.

The literature repeatedly separates at least four questions:

```text
1. Representation:
   what exactly are source and target, under which description?

2. Logical transfer:
   if certain comparability premises hold, what conclusion follows?

3. Evidential support:
   what target/source evidence actually warrants those comparability premises?

4. Practical commitment:
   given uncertainty, when should we act, forecast, extrapolate or abstain?
```

A major engineering implication is that an AI analogue controller should not output only:

```text
analogy_score(S,T) = 0.84
```

but something closer to:

```text
representation R
projection p
bridge/comparability assumptions A
supporting evidence E+
blocking evidence E-
transfer status: LICENSED / CONDITIONAL / VETOED / UNKNOWN
uncertainty
falsifier / target-side test
validation state
```

## Five stronger conclusions from the first sweep

### 1. Similarity is not confirmation

Recent Bayesian work makes similarity evidential only through a bridge/inferential structure and background knowledge. Different formal structures can even make more believed similarity reduce target confirmation.

### 2. Mapping is not relevance

A source and target can genuinely share feature/relation `f` without that fact licensing projection of `g`. Recent meta-rule approaches make the missing relation explicit: background knowledge must connect sameness/difference on the mapped dimension to the projected dimension.

### 3. Representation is not fixed before analogy

Recent context-update work treats source, target and reasoning contexts as belief sets revised during the reasoning process; Votsis directly compares scientific concept change with DNN feature change. A useful controller therefore needs typed rerepresentation rather than merely longer inference over a frozen abstraction.

### 4. Multi-source agreement is not automatically independent evidence

The robustness literature warns that agreement among several models/sources may simply reproduce shared assumptions, representational omissions or one common data lineage. A multi-analogue system therefore needs assumption/dependence analysis, not precedent voting. Recent work further clarifies that robustness can identify dispensable auxiliaries without automatically providing empirical target confirmation.

### 5. There may be no universal analogue score

Localist work in historical science argues that justification depends on contextually available facts and field-specific norms. The engineering target may therefore be:

```text
shared control states
+
domain-local warrant predicates / thresholds / falsifiers
```

rather than one global similarity-to-transfer function.

## Why the field is active now

Francesco Nappo and Giovanni Valente's **_Analogical Reasoning in Science_** appeared in Cambridge Elements in the Philosophy of Science in June 2026. Its stated premise is that the exact epistemological role of analogy in science remains an outstanding contemporary problem despite its importance in scientific discovery and inference.

Canonical: https://doi.org/10.1017/9781009526494

The 2023–25 PRIN project **Analogical Reasoning in Contemporary Physical Theories** and its 2024 `Analogies in Physics and Beyond` conference linked philosophy of physics with biology, economics, robotics and AI. Ioannis Votsis's `Modelling Analogical Reasoning: One-Size-Fits-All?` makes the AI motivation explicit: automating scientific reasoning requires models that distinguish good analogical transfer from bad.

## Working bridge to AI

The current AI and philosophy-of-science maps appear to meet at the following interface:

```text
AI strength:
open representation + large-scale source search + flexible mapping

PoS strength:
comparability premises + evidential relevance + uncertainty
+ external validity + robustness/dependence + falsification discipline
```

The strongest engineering hypothesis from this branch is now narrower and falsifiable:

> **Do explicit relevance, comparability-evidence, boundary-sensitivity, robustness and validation-state signals improve far transfer and calibration beyond outcome-only analogical training?**

Modern RA-RFT/RLVR work shows that analogy-aware retrieval and analogical transfer can already be trained; the remaining question is whether the philosophy-derived decomposition adds measurable control rather than merely better explanations.