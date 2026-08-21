# Coverage and Salience Priors — When the Model Retrieves the Famous Past Instead of the Relevant Past

**Snapshot: 21 August 2026.**

Historical analogy has a source-selection problem that is not captured by ordinary retrieval metrics: models are trained on radically unequal amounts of text about different countries, wars, crises, institutions and canonical episodes. That can create a **parametric prior over which histories feel predictive** before target evidence is considered.

This note treats media/corpus coverage as a potential confound in historical precedent generation and ranking.

---

## 1. Conflict forecasting exposes a qualitative prior failure

### Nemkova 2026 — _The Limits of LLM Forecasting: Parametric Knowledge Gaps Across Conflict Zones_

Canonical: https://arxiv.org/abs/2607.00018

Across 22 active conflict zones (2020–2026), the paper reports roughly a **224× gap** in English-language media attention per ACLED conflict event. It evaluates GPT-4o and Llama-3.3-70B on 660 held-out escalation cases and compares them with simple structured baselines.

The striking result is not a smooth accuracy decline with lower coverage. The models adopt qualitatively different categorical priors:

- Llama predicts escalation on every under-covered test case, numerically matching an Always-YES baseline;
- GPT-4o predicts no escalation on every over-covered case in its tier, missing all five actual escalation events;
- logistic regression using eleven observation-window features and **no country identity** reaches overall F1 ≈ 0.402 and beats both LLMs;
- adding structured ACLED evidence does not reliably repair the LLM failure and can make it worse.

The authors interpret this as temporal signal being overridden by country-level parametric priors rather than a simple lack of available evidence.

---

## 2. Why this matters for historical analogue retrieval

A historical-analogy model can fail upstream before mapping begins.

Suppose the target is an unfamiliar political crisis. A model may retrieve:

```text
Munich
Vietnam
Cuban Missile Crisis
1914
1929
1970s inflation
Japan 1990
```

not because these are the best structural sources, but because they occupy unusually dense and culturally canonical regions of the training distribution.

The failure signature is:

```text
training salience
→ source accessibility
→ apparent analogical plausibility
→ explanation fluency
```

rather than:

```text
target structure
→ source utility
```

This is especially dangerous because canonical precedents are also rhetorically legible to users.

---

## 3. The bias is not merely geographic

Historical salience can arise from:

- English-language media/documentation density;
- canonical school/history narratives;
- geopolitical importance to training-data-producing countries;
- famous leaders or named crises;
- digitization/access asymmetry;
- historiographic repetition;
- Wikipedia / textbook density;
- availability of clean machine-readable event data;
- recent commemorations or contemporary political reuse.

Thus a precedent can be over-retrieved even if its semantic relevance is only moderate.

---

## 4. Tests for salience-driven precedent selection

Historical Transfer Bench should include explicit **source-accessibility perturbations**.

### A. Entity masking

Replace country/leader/event names with neutral identifiers while preserving relations and quantities.

Measure:

- change in source ranking;
- change in mapping;
- change in projection confidence.

A large drop suggests reliance on entity-level parametric priors.

### B. Geographic transplantation

Keep the target event structure fixed but substitute geographic labels.

If the chosen precedent changes dramatically without a mechanism change, source retrieval is not structure-stable.

### C. Canonical-vs-obscure matched sources

Construct pairs with similar mechanism quality but radically different corpus salience.

Test whether the famous source systematically outranks the obscure source.

### D. Coverage-stratified source pools

Annotate candidate historical sources by approximate documentation/media/corpus coverage and report retrieval precision/recall by tier.

### E. Structured-blind baseline

Compare LLM source ranking with a model that only sees a curated relation/feature representation and not proper nouns.

If the simpler representation yields better target outcomes, semantic richness may be injecting salience rather than useful history.

---

## 5. Relation to Past Meets Present

Past Meets Present already observes that free generation can fall into stereotyped/same-entity/same-country analogies and uses reflection/verification to improve candidate quality. Coverage-prior testing pushes that observation further:

> **Does the model choose the source because its relational structure is useful, or because the source is unusually available in parametric memory?**

This should be treated as an empirical source-selection question, not inferred from fluency.

---

## 6. Relation to the reference-class bridge

Reference classes can partially counter vivid/canonical source capture by forcing comparison with a broader case population.

But reference classes can inherit the same archive bias if the database itself overrepresents well-documented events. Therefore the outside view needs its own coverage audit:

```text
observed historical base rate
≠ true historical base rate
```

when inclusion in the historical case base is selective.

The controller should report both:

- source relevance;
- source/case-base coverage limitations.

---

## 7. Training implication

A future source retriever could explicitly optimize **downstream transfer utility under salience controls**, not raw likelihood or semantic relevance.

Useful negatives include:

- famous source with high lexical availability but wrong mechanism;
- obscure source with low lexical overlap but correct mechanism;
- same-country source that is less useful than a cross-domain case;
- several canonical sources from the same historiographic family.

A contrastive/reinforcement objective can reward selection that survives entity masking and yields better out-of-sample projection accuracy.

---

## Bottom line

The conflict-forecasting evidence does not prove that every historical-analogy model is coverage-biased. It does establish a strong adjacent failure mode: **parametric familiarity can override temporally relevant evidence even when the evidence is supplied.**

Historical analogue retrieval should therefore be evaluated for **salience invariance**, not only source plausibility:

> **Would this precedent still be selected if its famous names and corpus-frequency advantages were removed?**
