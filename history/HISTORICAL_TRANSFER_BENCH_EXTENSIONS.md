# Historical Transfer Bench — Calibration & Control Extensions

**Status: design extension, not released data.**  
**Snapshot: 21 August 2026.**

The base benchmark specification focuses on projection-level selective transfer. Subsequent field sweeps identify four controls that should be made explicit rather than left as optional analysis:

1. **case vs reference-class conflict**;
2. **competing precedents / evidence diagnosticity**;
3. **coverage/salience robustness**;
4. **forecasting-trained longitudinal calibration**.

These extensions are designed to prevent a historical-analogy system from scoring well merely because it retrieves a plausible precedent and produces fluent limitations.

---

# Track X1 — Rich precedent vs outside-view reference class

## Goal

Test whether a model can combine mechanism-rich case reasoning with distributional historical calibration.

Each item includes:

- target `T`;
- one or more rich precedent candidates `S1...Sk`;
- a wider reference-class pool `C` with realized outcomes;
- at least two plausible class definitions, one of which may be misleading;
- target-side evidence about a potentially exceptional mechanism `X`.

### Condition A — case and class agree

The rich precedent and outside-view distribution support the same directional claim.

### Condition B — vivid precedent conflicts with base rate; no exceptional mechanism evidenced

Expected action: **do not overrule the reference class solely because the precedent is narratively compelling**.

### Condition C — precedent conflicts with base rate; target-specific mechanism is strongly evidenced

Expected action: permit a calibrated deviation and state the evidence carrying the burden of proof.

### Condition D — reference class invalid / heterogeneous

Expected action: reject or widen/redefine the class rather than mechanically trust the base rate.

## Outputs

```text
reference-class definition:
base-rate / outcome distribution:
rich precedent(s):
case-derived projection:
case–class divergence:
claimed exceptional mechanism:
target evidence for exceptionalism:
final probability:
reason for deviation / non-deviation:
```

## Metrics

- reference-class selection accuracy;
- proper scoring rule for final forecast;
- justified-deviation accuracy;
- famous-precedent capture rate;
- calibration when case/class conflict;
- performance relative to time-safe kNN / RCF baseline.

### Prior art / rationale

Lovallo, Clarke & Camerer (2012) already demonstrate that a **reference class of analogies** can outperform a few familiar analogies and explicitly combine case-based decision making with the outside view. Therefore this track does not claim the hybrid idea as novel; it tests whether a foundation model can add semantic/mechanism value beyond strong analogue-class baselines.

---

# Track X2 — Competing precedents and diagnostic evidence

## Goal

Separate `evidence that fits an analogy` from `evidence that discriminates among analogies`.

Each target includes:

- favored precedent `S_A` → mechanism `M_A`;
- competing precedent `S_B` → mechanism `M_B`;
- optional third/no-precedent alternative;
- evidence items `e1...en`;
- several facts compatible with both mechanisms;
- one or more genuinely discriminating observations.

The system must estimate which evidence is **diagnostic**, not count supportive facts.

## Desired output

```text
candidate mechanism A: ...
candidate mechanism B: ...
no-precedent / novel-mechanism option: ...

for each evidence item:
  supports A?
  supports B?
  diagnosticity / likelihood ratio estimate:

current ranking:
confidence:
what next observation would most discriminate A/B:
```

## Metrics

- competing-precedent ranking;
- recognition of non-diagnostic overlap;
- response to disconfirming evidence;
- likelihood/confidence calibration;
- unresolved-state accuracy;
- forecast Brier/log score where outcomes exist.

### Critical warning

Analysis-of-Competing-Hypotheses research does **not** establish that procedural complexity automatically improves judgment. Experimental and review evidence is mixed/negative, while 2026 LLM Bayesian-process-tracing work shows models can be internally coherent yet systematically overestimate evidential support. This track therefore scores empirical calibration, not checklist completion.

---

# Track X3 — Coverage and salience robustness

## Goal

Test whether the model retrieves a precedent because it is structurally useful or because it is famous / heavily represented in training data.

### Perturbation arms

#### Entity masking

Replace country, leader and canonical event names with neutral identifiers while preserving relations.

#### Geographic transplantation

Keep structure fixed while changing geographic labels.

#### Canonical vs obscure matched sources

Pair a famous source with an obscure but mechanism-matched source.

#### Coverage-stratified source pool

Annotate sources by documentation/media/corpus salience proxy.

#### Structured-blind baseline

A baseline receives only relation/features, not proper nouns.

## Metrics

- source-rank stability under masking/transplantation;
- mechanism-quality-adjusted salience bias;
- precision by source-coverage tier;
- canonical-source over-selection rate;
- downstream transfer accuracy after entity masking.

### Rationale

Conflict-forecasting evidence in 2026 shows large geographic media-coverage asymmetries can induce categorical LLM priors that override available temporal evidence. This is adjacent evidence, not proof that historical analogy has the identical failure. It is strong enough to justify a dedicated robustness test.

---

# Track X4 — Historical replay and forecast-trained calibration

## Goal

Move selective transfer from a static classification task to a **longitudinal forecasting policy**.

Use a chronological replay environment:

```text
t0:
  target evidence available up to t0
  system retrieves precedents and labels projections
  system commits probabilities

t1:
  new evidence appears
  some projections resolve
  system may update source applicability / representation / confidence

t2...tn:
  repeat
```

### Controller conditions

Compare at least:

1. generic LLM + prompt;
2. generic LLM + historical analogue retrieval;
3. time-safe kNN/reference-class baseline;
4. mechanism-rich historical analogue controller;
5. mechanism-rich controller + forecasting-trained calibration model/head.

### Metrics

- Brier score / log score;
- Brier skill relative to no-analogy and reference-class baselines;
- calibration error;
- projection macro-F1;
- update latency after new evidence;
- repeated-invalid-transfer rate;
- improvement in source/projection applicability memory;
- source-ranking drift after resolved failures;
- hindsight leakage / decision-time compliance.

### Rationale

OpenForecaster shows forecasting accuracy/calibration can be improved through dedicated post-training rather than being left to generic LLM reasoning. FutureSim shows real-world chronological replay can measure long-horizon search, memory, uncertainty and adaptation while questions resolve. Historical Transfer Bench should borrow this evaluation discipline.

---

# Track X5 — Incremental-value decomposition

This track asks a deliberately unfriendly question:

> **What does the LLM/analogy machinery add beyond retrieval itself?**

For every main result, include ablations:

```text
A. random / base-rate baseline
B. structured non-semantic model
C. time-safe kNN analogue retrieval
D. reference-class forecast
E. LLM using retrieved sources without mechanism scaffold
F. mechanism analogue system
G. mechanism analogue + projection control
H. mechanism analogue + projection control + calibrated forecasting controller
```

Report incremental gain from each transition.

This follows the caution from leakage-aware macro-analog forecasting where a simple kNN historical-neighborhood baseline recovers a comparable median signal to a richer LLM actor–critic pipeline.

---

# Track X6 — Rationale quality is not analogy presence

Large forecasting-tournament evidence indicates that an `Analogies` marker by itself has very small association with forecast quality, whereas broader reasoning discipline and rationale–forecast alignment are much more informative.

Therefore rationale scoring should reward:

- correspondence to the numerical forecast;
- explicit differences/limitations;
- base-rate use;
- competing evidence;
- update conditions;
- calibrated uncertainty.

Do **not** award quality points merely because the response cites historical precedents.

---

# Recommended composite evaluation

A system should not receive a single historical-analogy score. Report a profile:

```text
SOURCE SEARCH
  recall / precision / salience robustness

STRUCTURE
  mechanism alignment / representation plurality

TRANSFER
  projection license F1 / critical-disanalogy binding

EVIDENCE
  competing-precedent diagnosticity / dependence awareness

OUTSIDE VIEW
  reference-class selection / justified deviation

TIME
  hindsight sensitivity / chronological compliance

FORECAST
  Brier / log score / calibration / skill vs baselines

LEARNING
  applicability-memory improvement / repeat-failure rate

COMMUNICATION
  rationale–probability alignment / persuasion calibration
```

The research claim should be strongest only when gains survive **all** reasonable simpler baselines.

---

## Bottom line

The benchmark target is no longer simply `can the model use history?`.

It is:

> **Can a model derive a historically rich precedent hypothesis, survive an outside-view and competing-hypothesis challenge, remain invariant to irrelevant salience cues, attach calibrated probabilities to individual projected lessons, and improve those judgments as the world resolves?**
