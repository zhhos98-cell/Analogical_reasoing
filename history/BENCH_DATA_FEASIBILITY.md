# Benchmark Data Feasibility — Historical Transfer Does Not Need to Start from 40 Hand-Written Stories

**Snapshot: 21 August 2026.**

A projection-level historical-transfer benchmark sounds annotation-heavy if imagined as a set of bespoke historical essays. The current forecasting/event ecosystem makes a more scalable design possible.

There are now several complementary data layers:

1. **large resolved forecasting corpora** for outcome/calibration supervision;
2. **timestamped news/event streams** for pre-cutoff evidence and source retrieval;
3. **temporal knowledge graphs** for large-scale structured precedent baselines;
4. **deep live-crisis case corpora** for high-resolution qualitative validation;
5. **simulated dynamic worlds** for controlled transfer/disanalogy unit tests;
6. a smaller **expert-annotated transfer layer** for mechanism/projection labels.

The benchmark can therefore separate scale from expensive historical judgment.

---

# 1. OpenForesight — 55k resolved forecasting questions

**OpenForesight / OpenForecaster.**  
Dataset: https://huggingface.co/datasets/nikhilchandak/OpenForesight

Current public dataset size: **55,301 questions** across train/validation/test and later 2025–26 splits.

Useful fields include:

- question/background;
- explicit resolution criteria;
- answer;
- source article and publication dates;
- question start date;
- resolution date;
- retrieval-augmented prompt variants.

The 2026 Q1 Al Jazeera split adds 330 genuinely recent forecasting questions with extra checks that the answer could not already be inferred before the target period.

### Use for historical-transfer work

OpenForesight supplies **resolved target outcomes and decision dates**, not historical precedent annotations.

A scalable pipeline could:

```text
forecast question T at time t
→ retrieve candidate historical events S1...Sk from older corpora
→ generate mechanism mappings / projections
→ log projection probabilities
→ compare against resolved answer
```

Then only a stratified subset requires expert source/transfer annotation.

---

# 2. BTF-2 — a frozen pre-cutoff benchmark with rich research context

**BTF-2 / FutureSearch.**  
Dataset: https://huggingface.co/datasets/BTF-2/BTF-2

Public release:

- **1,417 binary questions**;
- written October 2025, resolved by December 2025;
- topics concentrated in geopolitics, regulation/policy, macroeconomics/markets, international security, law/investigations and related current affairs;
- detailed research summaries prepared before resolution;
- SOTA forecast probabilities/rationales and actual resolutions;
- companion scrape index with **15.5 million question→page edges** across more than 8 million unique URLs captured during the October 2025 window.

### Why this may be especially useful

BTF-2 already supplies the core ingredients for a serious retrospective transfer experiment:

```text
frozen target date
frozen research environment
resolved binary outcome
high-quality benchmark forecast
```

Historical-analogy evaluation can add one new layer:

```text
which pre-target historical precedents did the model retrieve?
what projection did each precedent support?
did the analogue improve Brier score beyond the existing research/base-rate forecast?
```

### Caveat

Models with late-2025/2026 pretraining may have parametric access to resolutions. Use models whose knowledge cutoff predates the benchmark or run explicit hindsight audits/time-locked baselines.

---

# 3. ForecastBench — continuously generated contamination-resistant outcomes

**ForecastBench.**  
Dataset hub: https://www.forecastbench.org/datasets/  
Open repository: https://github.com/forecastingresearch/forecastbench-datasets

ForecastBench is particularly attractive because it is **dynamic** rather than a one-off pastcast dataset.

Every two weeks it creates new forecasting rounds; resolution data and leaderboards update continuously. Question sources include:

- ACLED;
- FRED / DBnomics / market/economic series;
- Wikipedia-derived structured questions;
- prediction platforms such as Metaculus, Manifold and Polymarket.

### Historical-transfer use

This can become a live prospective test:

```text
round r:
  historical-analogy system commits precedents + transfer contracts + probabilities

later:
  outcomes resolve
  transfer error is scored
  applicability memory updates

round r+1:
  test whether learned boundaries help
```

This is much cleaner evidence than post-hoc case studies because the historical analogy is logged before the outcome exists.

---

# 4. WorldReasoner — outcome, evidence and mechanism can be scored separately

**Chi, Chamoun, Ding & Vlachos, 2026.**  
Canonical: https://arxiv.org/abs/2606.11816

WorldReasoner contains:

- **345 resolved forecasting tasks**;
- **14,141 timestamped articles**;
- post-resolution hindsight graphs spanning **8,087 extracted events**.

The framework separately evaluates:

```text
outcome quality
evidence quality
causal-reasoning / graph quality
```

### Historical-transfer use

This is almost the ideal evaluation skeleton for a subset of our benchmark:

```text
was the forecast correct?
were the historical/source claims grounded in valid pre-cutoff evidence?
was the projected causal pathway compatible with later evidence?
```

A fourth axis can be added:

```text
was the source→target transfer itself licensed?
```

---

# 5. Fog-of-War data — one small but very deep live historical-analogy testbed

**Li, Li & Zhou 2026.**  
Dataset: https://huggingface.co/datasets/AIcell/war-test-dataset

Public artifacts include:

- **11 temporal nodes** in an unfolding 2026 conflict;
- **42 verifiable questions + 5 exploratory questions**;
- roughly **1,685 timestamped articles** from Reuters, AP, BBC, Al Jazeera, Bloomberg, Guardian and others;
- post-cutoff model evaluation.

This is not a scale dataset. It is useful as a **microscope**.

The paper already contains a supplied-precedent disanalogy episode (`Overcoming Historical Bias`), making it a natural place to manually annotate:

- source precedent;
- target-side changed conditions;
- blocked projection;
- probability before/after disanalogy.

---

# 6. ICEWS / GDELT — millions of structured historical events

ICEWS and GDELT are already standard temporal-event forecasting corpora.

Examples:

- ICEWS14: ~90k event facts;
- ICEWS18: ~469k;
- ICEWS05–15: ~461k;
- commonly used GDELT benchmark slices can exceed **2 million** event facts.

### What they are good for

They supply a cheap structured source universe for:

- large-scale precedent retrieval;
- event-type/actor/relation similarity baselines;
- candidate-source hardness mining;
- temporal pattern / recurrence tests;
- source-rank reversal and no-source controls.

`AnRe` (ACL 2025) already demonstrates analogical replay over temporal knowledge graphs, making this an important lower-bound baseline.

### What they are bad for

A coded event tuple is much thinner than a historical mechanism. ICEWS/GDELT should not be treated as the final historical representation.

Use them as:

```text
retrieval/baseline substrate
```

rather than:

```text
historical causal truth.
```

---

# 7. ForecastBench-Sim — controlled causal transfer before real-history external validation

**Lee, Merrill & Karger, 2026.**  
Canonical: https://arxiv.org/abs/2606.18686

ForecastBench-Sim generates forecasting tasks from Freeciv world rollouts. Because the world is simulated, it can produce:

- paired intervention worlds;
- immediately resolved forecasts;
- rare/disruptive events on demand;
- arbitrary forecast horizons;
- counterfactual/conditional questions.

### Why a non-historical simulation belongs here

Our key operation is difficult to validate in history because the counterfactual ground truth is often unknowable:

```text
source S and target T share structure
BUT condition X differs
→ projection p should / should not transfer
```

In simulation we can **manufacture exact matched worlds** where only X changes and observe whether the projected outcome really changes.

This gives a two-stage research design:

### Stage A — controlled transfer unit test

Use simulated worlds to establish that the controller can learn:

```text
shared mechanism
+ one discriminative condition
→ projection-level license/veto
```

with real causal ground truth.

### Stage B — historical external validity

Apply the same control architecture to frozen real-world event corpora where representations and mechanisms are uncertain.

This sharply separates:

```text
algorithm cannot learn selective transfer
```

from:

```text
historical evidence/representation is insufficient to identify transfer.
```

---

# 8. Proposed four-tier dataset architecture

## Tier 1 — structured scale

**ICEWS / GDELT / temporal KGs**

Purpose:

- millions of candidate events;
- fast retrieval baselines;
- hard-negative mining;
- repeated relation patterns;
- source-selection stress tests.

Human annotation: minimal.

---

## Tier 2 — resolved real-world forecast scale

**OpenForesight / BTF-2 / ForecastBench**

Purpose:

- proper scoring;
- temporal cutoffs;
- real outcomes;
- reference-class calibration;
- longitudinal transfer-error learning.

Human annotation: none for most items; expert annotation only for selected candidate precedents.

---

## Tier 3 — mechanism/evidence evaluation

**WorldReasoner + curated historical cases + CANA-style event annotations**

Purpose:

- mechanism/pathway quality;
- source grounding;
- projection-level transfer labels;
- competing representations;
- expert adjudication.

Human annotation: high, but only hundreds rather than tens of thousands of items.

---

## Tier 4 — prospective/live and controlled causal tests

**ForecastBench live rounds / FutureSim / Fog of War / ForecastBench-Sim**

Purpose:

- genuine no-hindsight evaluation;
- boundary-memory learning;
- live source selection;
- intervention/counterfactual unit tests;
- resolution-driven updating.

Human annotation: targeted audits.

---

# 9. A practical curation strategy

A realistic first release does not need 10,000 expert-labeled historical analogies.

### Phase A — automatic mining

From 5k–50k resolved forecasting targets:

1. retrieve top historical source candidates via multiple methods;
2. include structured kNN / semantic / mechanism-LLM / random hard negatives;
3. generate candidate projections;
4. score actual target outcomes automatically where possible.

### Phase B — select disagreement cases

Prioritize items where:

- semantic retriever and mechanism retriever disagree;
- vivid source conflicts with reference-class base rate;
- two historical precedents imply opposite outcomes;
- the same source appears useful for one projection and harmful for another;
- model confidence is high but outcome is wrong;
- entity masking changes source ranking.

These are the highest-information cases for expert annotation.

### Phase C — historian/domain-expert adjudication

Experts annotate only:

```text
source usefulness
structural correspondence
critical disanalogy
projection license
competing representation
source dependence/provenance
```

The target outcome itself is already resolved by the forecasting dataset.

This converts expert labor from `write the entire benchmark` to `adjudicate the hard transfer boundary`.

---

# 10. A plausible first dataset size

A credible pilot could be:

```text
Tier 1: 100k+ machine-structured event candidates
Tier 2: 1,000–5,000 resolved forecast targets
Tier 3: 150–300 expert-adjudicated transfer cases
Tier 4: 20–50 deep/live/counterfactual trajectories
```

Each expert case can contain multiple source candidates and multiple projections, yielding many more **transfer decisions** than target-event count suggests.

For example:

```text
200 targets
× 4 source candidates
× 3 projections
= 2,400 projection-level transfer judgments
```

plus automatic outcome/calibration labels.

---

# 11. What still requires expensive scholarship

No dataset eliminates the need for serious historical/domain judgment on:

- what counts as the relevant mechanism;
- whether two precedents are genealogically dependent;
- whether a target-side difference is historically consequential;
- whether a causal pathway is one reasonable interpretation or retrospective overfitting;
- whether the model's source description is itself anachronistic or source-distorted.

The gain is that this labor can be concentrated where machine systems **disagree or fail**, rather than applied uniformly to every event.

---

## Bottom line

The data problem is tractable.

The current ecosystem already supplies large, resolved, timestamped forecasting and event corpora. A historical-transfer benchmark can therefore be built as a **layer over existing outcome infrastructure**, with expert work focused on the small but decisive object that no existing dataset supplies:

> **which relation/projection from which historical source is actually licensed for this target, under which historically consequential differences?**
