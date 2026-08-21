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
- [`COMPARATIVE_PROCESS_TRACING.md`](COMPARATIVE_PROCESS_TRACING.md) — mechanism-breakpoint/fingerprint strategies: inspect the causally diagnostic difference points rather than demand whole-source similarity.
- [`MODEL_TRANSFER.md`](MODEL_TRANSFER.md) — distinguishes what is transferred (model form, operator, mechanism, strategy, outcome) and why successful model reuse is not automatically projective confirmation.
- [`SURROGATIVE_REASONING.md`](SURROGATIVE_REASONING.md) — separates source/model demonstration from target interpretation/rebinding and from empirical target accuracy.
- [`REPRESENTATION_AND_SIMILARITY.md`](REPRESENTATION_AND_SIMILARITY.md) — source/target non-uniqueness, metric dependence, inferred properties and conceptual revision.
- [`CONTEXT_AND_REPRESENTATION_REVISION.md`](CONTEXT_AND_REPRESENTATION_REVISION.md) — source/target/reasoning context as revisable state; connects AGM-style belief update, over-analogization and DNN feature change.
- [`AI_REPRESENTATION_CHANGE.md`](AI_REPRESENTATION_CHANGE.md) — scientific concept revision ↔ DNN feature revision; makes `REREPRESENT` an explicit analogical-control action.
- [`DISCOVERY_VS_CONFIRMATION.md`](DISCOVERY_VS_CONFIRMATION.md) — separates analogy as hypothesis/model-strategy generation and pursuit from analogy as confirmation, prediction or action warrant.
- [`LOCALISM_AND_CONTEXT.md`](LOCALISM_AND_CONTEXT.md) — a portable transfer-control grammar with domain-local evidential rules rather than one universal analogy score.
- [`ROBUSTNESS_AND_MULTI_ANALOGUE.md`](ROBUSTNESS_AND_MULTI_ANALOGUE.md) — why agreement among several analogues is not automatically several independent confirmations; includes 2026 inferential rules for what robustness can establish.
- [`ANALOGUE_EXPERIMENTS.md`](ANALOGUE_EXPERIMENTS.md) — plausibility, model-external support and external validation as distinct transfer states.
- [`FROM_NORMS_TO_REWARDS.md`](FROM_NORMS_TO_REWARDS.md) — separates PoS distinctions already mirrored by modern training methods from still-hypothetical reward/control signals.
- [`PROGRAM_AND_AI_BRIDGE.md`](PROGRAM_AND_AI_BRIDGE.md) — current research network around scientific analogy and its explicit AI interfaces.
- [`../data/philosophy_of_science_analogy.csv`](../data/philosophy_of_science_analogy.csv) — structured literature map.

## Current high-level result

Contemporary philosophy of science does **not** treat analogical inference as a scalar function of source–target resemblance.

The literature repeatedly separates at least these stages:

```text
1. Representation:
   what exactly are source and target, under which description?

2. Source demonstration:
   what actually follows inside the source/model representation?

3. Mapping / interpretation:
   how is that source result rebound/interpreted in target terms?

4. Logical transfer:
   if certain comparability premises hold, what target conclusion follows?

5. Evidential support:
   what source/target evidence actually warrants those comparability premises?

6. Epistemic role:
   is the analogy only worth pursuing, or does it support belief/forecast/action?

7. Practical commitment:
   given uncertainty and stakes, when should we act, test, extrapolate or abstain?
```

A major engineering implication is that an AI analogue controller should not output only:

```text
analogy_score(S,T) = 0.84
```

but something closer to:

```text
representation R
source result r
mapping / target interpretation
projection p
bridge/comparability assumptions A
supporting evidence E+
blocking evidence E-
epistemic role: GENERATE / PURSUE / PLAUSIBLE / PROJECT / CONFIRM / ACT
transfer status: LICENSED / CONDITIONAL / VETOED / UNKNOWN
uncertainty
falsifier / target-side test
validation state
```

## Eight stronger conclusions from the sweep

### 1. Similarity is not confirmation

Recent Bayesian work makes similarity evidential only through a bridge/inferential structure and background knowledge. Different formal structures can even make more believed similarity reduce target confirmation.

### 2. Mapping is not relevance

A source and target can genuinely share feature/relation `f` without that fact licensing projection of `g`. Recent meta-rule approaches make the missing relation explicit: background knowledge must connect sameness/difference on the mapped dimension to the projected dimension.

### 3. Whole-source similarity is often the wrong transfer question

Comparative process tracing and chain-graph/fingerprint approaches ask which mechanism stages are likely to differ and which distinctive markers would discriminate genuine from spurious extrapolation. This suggests projection-specific breakpoint search and active evidence acquisition rather than whole-event causal equivalence.

### 4. Source reasoning is not target interpretation

Scientific representation/surrogative reasoning separates what follows inside a model from how that result is interpreted as a claim about the target. A model can perform source-side reasoning and mapping coherently while the target interpretation or external-validity bridge is wrong.

### 5. Representation is not fixed before analogy

Recent context-update work treats source, target and reasoning contexts as belief sets revised during the reasoning process; Votsis directly compares scientific concept change with DNN feature change. A useful controller therefore needs typed rerepresentation rather than merely longer inference over a frozen abstraction.

### 6. Analogy can justify pursuit without justifying belief

Scientific analogies can transfer a modelling strategy, suggest an experiment or open a new hypothesis space without confirming the target claim. AI systems should separate `GENERATE/PURSUE` from `BELIEVE/PROJECT/ACT` rather than upgrading creative analogy into forecast confidence.

### 7. Multi-source agreement is not automatically independent evidence

The robustness literature warns that agreement among several models/sources may simply reproduce shared assumptions, representational omissions or one common data lineage. A multi-analogue system therefore needs assumption/dependence analysis, not precedent voting. Recent work further clarifies that robustness can identify dispensable auxiliaries without automatically providing empirical target confirmation.

### 8. There may be no universal analogue score

Localist work argues that justification depends on contextually available facts and field-specific norms. The engineering target may therefore be:

```text
shared control states
+
domain-local warrant predicates / thresholds / falsifiers
```

rather than one global similarity-to-transfer function.

## Why the field is active now

Francesco Nappo and Giovanni Valente's **_Analogical Reasoning in Science_** appeared in Cambridge Elements in the Philosophy of Science in June 2026. Its stated premise is that the exact epistemological role of analogy in science remains an outstanding contemporary problem despite its importance in scientific discovery and inference.

Canonical: https://doi.org/10.1017/9781009526494

The Element's reference map itself spans cognitive structure mapping, scientific modelling/representation, extrapolation and comparative process tracing, robustness, model transfer, conceptual innovation, analogue experiments and AI. The 2023–25 PRIN project **Analogical Reasoning in Contemporary Physical Theories** and its 2024 `Analogies in Physics and Beyond` conference linked philosophy of physics with biology, economics, robotics and AI. Ioannis Votsis's `Modelling Analogical Reasoning: One-Size-Fits-All?` makes the AI motivation explicit: automating scientific reasoning requires models that distinguish good analogical transfer from bad.

## Working bridge to AI

The current AI and philosophy-of-science maps meet at a fairly sharp interface:

```text
AI strength:
open representation + large-scale source search + flexible mapping

PoS strength:
transfer-object typing + projection relevance + comparability premises
+ evidential support + extrapolation breakpoints + uncertainty
+ external validity + robustness/dependence + falsification discipline
+ separation of discovery from confirmation
```

The strongest engineering hypothesis from this branch is now narrower and falsifiable:

> **Do explicit relevance, comparability-evidence, breakpoint/boundary-sensitivity, interpretation-state, robustness and validation-state signals improve far transfer and calibration beyond outcome-only analogical training?**

Modern RA-RFT/RLVR work shows that analogy-aware retrieval and analogical transfer can already be trained; the remaining question is whether the philosophy-derived decomposition adds measurable control rather than merely better explanations.