# Temporal Validation — Preventing Hindsight from Masquerading as Historical Analogy

**Snapshot: 21 August 2026.**

Historical-analogy foresight has a special evaluation problem that ordinary analogy benchmarks do not: the model may already know how the target event ended.

A system can appear to retrieve an unusually prescient historical precedent because its parametric memory has already encoded the target's later outcome. Restricting the prompt or RAG corpus to pre-cutoff documents does **not** by itself remove this contamination.

This file therefore treats temporal control as **validation infrastructure for historical analogy**, not as a separate AI-for-history application.

---

## 1. CANA / ADR already controls explicit temporal violations

**Chen et al., _Analogical Deep Research_, 2026.**  
Canonical: https://arxiv.org/abs/2607.13602

ADR-bench gives each target event:

- a temporal cutoff with rationale;
- a pre-cutoff analyst brief;
- post-hoc causal structure and outcomes for evaluation;
- oracle analogies and hidden factors.

The task is explicitly to produce foresight **using only the pre-cutoff brief**.

Its Foresight Quality Score is claim-level. For every foresight claim the evaluator scores:

- outcome accuracy against what actually happened;
- grounding in a specific historical analogy;
- specificity;
- **derivability from pre-cutoff information + analogical reasoning**;
- temporal compliance;
- hidden-factor hits.

Temporal compliance is classified as:

- **Clean** — based on pre-cutoff target facts or historical analogical reasoning;
- **Soft violation** — invokes post-cutoff target trends without naming specific later events;
- **Hard violation** — explicitly references specific post-cutoff target facts/events/outcomes.

A hard violation receives zero temporal weight in the FQS.

### Why this is not sufficient

The evaluator can detect what the model **says** about the future. It cannot directly detect whether knowledge of the actual future already affected:

- which precedent the model selected;
- which source mechanism it emphasized;
- which hidden factor it proposed;
- which competing analogy it discarded;
- the confidence or specificity of an apparently pre-cutoff inference.

This creates a deeper distinction:

`observable post-cutoff citation`

vs

`parametric hindsight influencing an otherwise temporally clean answer`.

The second is much harder.

---

## 2. Prompt-level historical cutoffs are porous

### Asai et al. 2026 — Can LLMs Be Constrained to the Past?

**Michiro Asai et al., arXiv:2606.05804.**  
Canonical: https://arxiv.org/abs/2606.05804

The paper studies prompting a normal LLM to behave as though knowledge after a given date were unavailable. Direct cutoff prompting is especially fragile when later knowledge is only **causally related** to the question rather than explicitly requested.

The authors introduce:

- **Self-Recall** — have the model restate the cutoff constraint;
- **Question-Recall** — recall question-relevant information valid under the cutoff;
- **MHEB, Multi-cutoff Historical Event Benchmark** — ask the same question under multiple historical cutoffs.

Recall-based prompting improves cutoff behavior, especially on counterfactual questions, but performance still varies with the distance of the cutoff.

### Implication for historical analogy

Prompting can be useful for cheap experiments, but `You are an analyst in 2007` is not a reliable epistemic boundary. It should be treated as the weakest temporal-control tier.

---

## 3. HindsightBench — audit parametric hindsight directly

### Jia 2026

**Haozhe Jia, _HindsightBench: A Black-Box Behavioral Audit Protocol for Parametric Hindsight in Time-Indexed LLM Decision Tasks_, arXiv:2607.18867.**  
Canonical: https://arxiv.org/abs/2607.18867

HindsightBench assumes that models can leak realized outcomes into historical decision tasks even when the visible context is historically clean. Instead of requiring model weights or training-corpus access, it supplies a black-box behavioral audit.

The protocol combines:

1. a four-arm date manipulation matrix:
   - date revealed;
   - date-only;
   - date masked;
   - date transplanted;
2. two memory probes:
   - date recovery;
   - realized-outcome recall;
3. six metrics including:
   - trigger strength;
   - transplant effect;
   - post-cutoff placebo;
   - recoverability;
   - behaviorally effective knowledge cutoff;
   - recall–accuracy dissociation.

On 15 models from seven vendors over a 258-node vintage-correct macro panel, the paper reports that effective behavioral cutoffs can precede vendor-reported dates by as much as eight months, and that audit behavior can even change with quantization/serving configuration.

### Why this is almost tailor-made for historical analogy

A historical-analogy benchmark can run the same target under altered/hidden/transplanted dates and ask whether:

- the selected historical sources change;
- analogy rankings change;
- predicted hidden factors change;
- mechanism alignments become suspiciously closer to the realized future;
- source selection still predicts the outcome when the identifying date cue is removed.

This would turn hindsight contamination from a vague concern into an auditable property of the analogical pipeline.

---

## 4. Ranke-4B — hard time locks at the training-data level

### Göttlich, Loibner, Jiang & Voth — History LLMs

Project: https://github.com/DGoettlich/history-llms

Ranke-4B is a family of 4B Qwen3-architecture models trained from scratch on 80B tokens each with hard knowledge cutoffs at:

`1913 / 1929 / 1933 / 1939 / 1946`.

The wider corpus contains about 600B tokens of historical books and newspapers. The project explicitly validates that checkpoints learn pre-cutoff but not post-cutoff facts and attempts to post-train conversational behavior without importing later normative content.

### Relevance to analogy rather than historical roleplay

The most valuable use for this branch is experimental:

- take a target event just before one of the cutoffs;
- provide or retrieve only earlier historical source events;
- compare analogy generation/mapping between a time-locked model and a contemporary model;
- observe which supposedly “obvious” historical precedents disappear when hindsight is genuinely unavailable;
- test whether later successful analogies were historically retrievable or only retrospectively salient.

This is stronger than prompt-time temporal masking because the future facts literally never entered the checkpoint's training data.

### Limits

Time locking does not itself create a good analogical reasoner. Ranke-4B is 4B-scale and optimized for historical textual culture, not necessarily frontier reasoning. Its value is as a **clean epistemic baseline / source generator**, possibly paired with a more capable but audited reasoning system.

---

## 5. MACROCAST — what a gold-standard real-time evaluation looks like

### Carriero, Pettenuzzo & Shekhar 2026

**_MACROCAST: A Vintage-Consistent Time Series Foundation Model for Real-Time Macroeconomic Forecasting_, arXiv:2606.28670.**  
Canonical: https://arxiv.org/abs/2606.28670

MACROCAST is not a historical-analogy model. It is important because it demonstrates a much stricter evaluation standard than most historical foresight work.

It prevents two forms of leakage:

- **temporal contamination** — future realized values never enter training;
- **revision bias** — the model never sees later revised economic releases that a real-time forecaster could not have observed.

Pretraining uses synthetic time series; fine-tuning uses vintage-specific ALFRED data. Evaluation is a genuine real-time out-of-sample exercise.

### Lesson for historical analogy

Historical analogy needs the equivalent of a **vintage-consistent event corpus**:

`what source descriptions existed at time t?`

`what target information was visible at t?`

`which later reinterpretations/revised statistics had not yet appeared?`

A historically valid analogue benchmark should version not only target outcomes but also source representations and data revisions.

---

# 6. Three temporal-control tiers

| Tier | Method | Protects against | Remaining risk | Cost |
|---|---|---|---|---|
| **T1 Prompt cutoff** | cutoff instruction / recall prompting / MHEB | blatant future references | parametric hindsight still shapes reasoning | low |
| **T2 Black-box audit** | HindsightBench-style date manipulations + memory probes | detects behavioral influence of memorized outcomes | cannot fully remove contamination | medium |
| **T3 Hard temporal isolation** | time-locked model / vintage-only training | future facts absent from model/data | smaller models; corpus-era bias; reasoning limits | high |

A serious historical-analogy experiment should state explicitly which tier it uses.

---

# 7. Historical-analogy-specific hindsight tests

Generic hindsight metrics should be extended to the analogy pipeline.

## H1 — source-selection hindsight

Does the model choose a precedent whose relevance became obvious only after the target outcome?

Measure:

`P(source S selected | actual target date)`

vs

`P(source S selected | date masked/transplanted)`.

## H2 — mapping hindsight

With the same source retained, does the model emphasize structural roles that line up suspiciously with the realized target future?

## H3 — disanalogy hindsight

Does the model selectively ignore source–target differences that, before the outcome, should have weakened the analogy?

## H4 — hidden-factor hindsight

Can the model name the historically hidden factor even when date/outcome cues are removed and the factor was genuinely obscure before cutoff?

## H5 — confidence hindsight

Does knowing the target date increase confidence/specificity even when the visible evidence is unchanged?

## H6 — analogue-set hindsight

Does cross-analogy confirmation become stronger only because the model retrieves a retrospectively curated set of precedents?

These tests are especially important for CANA-style systems because a temporally clean final report can still have a hindsight-contaminated **search trajectory**.

---

# 8. A stronger historical analogy benchmark design

The cleanest future benchmark would combine several forms of temporal control:

1. **historical target cutoffs** with a contemporaneous analyst brief;
2. **vintage source representations**, excluding retrospective reinterpretation when possible;
3. **date-masked and date-transplanted counterfactual arms**;
4. **parametric memory probes** for known target outcomes;
5. **time-locked checkpoints** for a subset of periods as a hard baseline;
6. **claim-level temporal compliance** like ADR/FQS;
7. **source-selection and mapping-level hindsight metrics**, not final-text inspection alone;
8. evaluation against later outcomes only in a separate judge layer.

The key principle is:

> **The model that constructs the analogy should not be allowed to know more about the target future than the historical analyst it is supposed to emulate.**

This is the necessary bridge between historical analogy as a persuasive reasoning style and historical analogy as a genuinely testable foresight technology.
