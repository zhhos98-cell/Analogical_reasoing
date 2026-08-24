# Transferability Estimation — Turning CANA's Transfer-Error Assumption into a Learned Decision

**Snapshot: 21 August 2026.**

CANA's Assumption 3 introduces a mechanism-transfer error bound `α_s^tr`: even when source and target share a genuine structural position `s`, the source-derived trajectory can still be wrong for the target.

A mature adjacent field already asks the operational version of this question:

> **Before performing transfer, can we estimate how well a source/model will work on the target and avoid negative transfer?**

The field is usually called **transferability estimation**. It does not solve open historical analogy, but it provides strong prior art for treating source applicability as a learned/predicted quantity rather than a similarity heuristic.

---

## 1. PAS — estimate target accuracy before adaptation

### Diniz, de Faria Júnior & Ester, ICLR 2026

**_PAS: Estimating the Target Accuracy Before Domain Adaptation_.**  
ICLR 2026.

PAS estimates the usefulness of a candidate **source domain + pretrained feature extractor** for an unlabeled target task before expensive adaptation is performed.

The important design point is asymmetry:

```text
source → target transferability
```

is not assumed to equal

```text
target → source transferability.
```

A source can be a poor starting point for a harder target even if the domains appear close under a symmetric distance metric.

### Historical-analogy translation

Historical analogy should also be directional:

```text
1907 → 2008
```

need not have the same transfer value as

```text
2008 → 1907-like target.
```

The target may contain later institutions, technologies or buffering mechanisms that change applicability.

A precedent score should therefore predict **downstream transfer performance**, not merely source–target similarity.

---

## 2. Wang & Thiede 2026 — context-aware transferability estimation

### _Context-aware Transferability Estimation for Industrial Transfer Learning_

**Yijin Wang & Sebastian Thiede.** Journal of Intelligent Manufacturing (2026).  
Canonical: https://doi.org/10.1007/s10845-026-02911-6

This is especially relevant because it explicitly argues that **statistical distributional similarity is insufficient** for deciding whether manufacturing knowledge transfers.

The framework combines:

### Context-aware transferability score

- multi-scale **structural alignment**;
- **monotonicity consistency**;
- key process-parameter analysis.

### Data-based transferability score

- Maximum Mean Discrepancy;
- Wasserstein distance;
- Jensen–Shannon divergence.

The combined score is validated against **actual downstream transfer-learning performance** using RMSE/MAPE, with no-transfer and no-adaptation baselines.

### Why this maps unusually well to historical analogy

The structure is almost exactly what a historical transfer controller needs:

```text
surface/statistical similarity
+
process/mechanism compatibility
→ predicted transferability
→ verify against realized target performance
```

For open historical events, the corresponding inputs could be:

- structural-role alignment;
- direction/monotonicity consistency of mechanism effects;
- key enabling/blocking conditions;
- source/target scale mismatch;
- temporal/institutional context;
- broader reference-class distance.

The hard difference is representation: manufacturing process variables and product properties are defined in advance; historical mechanism variables are endogenous and contestable.

---

## 3. TranSAC and the broader transferability-metric field

### Zhan, Zeng & Wang 2026 — _TranSAC_

Pattern Recognition (2026).  
Canonical: https://doi.org/10.1016/j.patcog.2026.113137

TranSAC estimates transferability without target labels by combining:

- **task speciality**;
- **domain commonality**.

It provides theoretical performance bounds and evaluates both model ranking and source-domain ranking.

This reinforces a useful separation:

```text
general source compatibility
≠
specific usefulness for the target task/projection.
```

Historical analogy needs the same distinction. A historical source can be broadly mechanism-similar while being useless for the **particular projected claim** the analyst is considering.

---

## 4. Source-selection scores are not necessarily trustworthy

### Singh, Hess & Vanschoren — ICLR 2026

**_How NOT to benchmark your SITE metric: Beyond Static Leaderboards and Towards Realistic Evaluation_.**  
Canonical: https://proceedings.iclr.cc/paper_files/paper/2026/hash/f0ebc318e2df08360b2df559e81602e5-Abstract-Conference.html

This paper audits benchmarks for Source-free/Source/Model Transferability Estimation and finds a serious problem: common evaluation setups have unrealistic candidate spaces and static performance hierarchies. Under these conditions, simple dataset-agnostic heuristics can appear competitive with or better than sophisticated transferability metrics.

### Historical-analogy warning

A historical transfer benchmark can make the same mistake if:

- the same canonical precedents are useful across many targets;
- source rankings are nearly static;
- target domains are too homogeneous;
- famous sources dominate both training and evaluation;
- the same mechanism vocabulary repeats across the whole dataset;
- no new sources enter over time.

A controller could learn `always prefer source family X` and look like it understands transfer validity.

Therefore benchmark construction needs:

- changing candidate-source sets;
- targets where source rankings reverse;
- source `S` useful for projection `p1` but harmful for `p2`;
- chronological replay where applicability changes;
- domain/geographic/time heterogeneity;
- no-valid-source cases;
- obscure/famous source balance.

---

## 5. Operationalizing CANA's `α_s^tr`

A historical transferability head could predict:

```text
α_hat(S, T, s, p)
```

where:

- `S` = source precedent;
- `T` = target event;
- `s` = structurally aligned role/pathway;
- `p` = candidate projected claim.

Inputs:

```text
structural alignment features
residual source-target gaps
pathway direction consistency
target-side enabling/blocking conditions
scale mismatch
temporal/institutional distance
source dependence / salience
reference-class disagreement
current evidence quality
```

Output:

```text
predicted transfer error / probability of projection validity
```

Decision policy:

```text
low predicted error   → LICENSED
moderate/context-bound → CONDITIONAL
high predicted error  → VETOED
high epistemic uncertainty → UNKNOWN / acquire evidence
```

The label should ultimately be trained/validated from **resolved targets**, not only LLM judges.

---

## 6. A key distinction from ordinary transferability estimation

Standard transferability metrics usually output one score for:

```text
source model/domain → target task
```

Historical analogy needs finer granularity:

```text
source event
→ target event
→ one aligned mechanism/pathway
→ one projected historical lesson
```

A source can therefore be simultaneously:

```text
highly transferable for p1
conditional for p2
non-transferable for p3
```

This is the central reason we keep the projection-level object.

---

## 7. Training data strategy

A resolved-event corpus can generate supervision for transferability estimation.

For each historical target at cutoff `t0`:

1. construct source candidates available before `t0`;
2. generate source→target mappings and projections using only pre-cutoff information;
3. record predicted transferability for every `(S,T,s,p)`;
4. reveal later target outcomes;
5. score realized projection error;
6. learn which residual gaps predict negative transfer;
7. update applicability boundaries.

This turns historical record into a **source-target transfer dataset**, not just a retrieval corpus.

---

## 8. Benchmark consequence

Historical Transfer Bench should report a metric analogous to a transferability-ranking correlation:

```text
Does predicted source/projection transferability correlate with realized transfer quality?
```

Possible measures:

- rank correlation between predicted transferability and realized projection performance;
- AUROC for harmful-transfer detection;
- calibration of projection-validity probabilities;
- regret from source/projection selection;
- negative-transfer rate relative to no-analogy baseline;
- source-ranking stability under changing candidate sets;
- dynamic rank reversal accuracy.

---

## Bottom line

Transferability estimation falsifies another overly broad novelty claim: **predicting whether source knowledge will help a target before transfer is already an active, technically mature problem.**

The historical-analogy frontier is the harder version:

> **estimate transferability at the level of a learned historical relation/pathway and an individual projected lesson, when the source/target representation itself is open, uncertain and revisable.**

This supplies a direct engineering interpretation of CANA's `α_s^tr`: do not assume the bound is small; learn to predict it, verify it on resolved events, and use it to control precedent-derived claims.
