# Current AI Scientific-Discovery Cases — Pressure-Testing the PoS Map

**Snapshot: 21 August 2026.**

Contemporary philosophy-of-science constraints should be tested against systems where analogy already produces measurable scientific value. Two 2026 cases are especially informative because they isolate different stages of the pipeline.

---

## 1. Larraz & Corma 2026 — the bridge is available but not autonomously activated

**Rafael Larraz & Avelino Corma, _Human analogical guidance amplifies LLM performance through cross-domain knowledge activation_, Nature Communications 17:4822 (2026).**  
DOI: https://doi.org/10.1038/s41467-026-70873-7

### Experimental design

The study reconstructs the pre-1936 knowledge environment for Fluid Catalytic Cracking (FCC), whose later solution is known. Across 250 trials with Qwen-2.5-7B, the RAG context is held fixed while analogical guidance and internal representation steering are manipulated.

### Result

Minimal guidance yields only about **10%** FCC-class success in the reported baseline condition. Structured analogical guidance redirects the model from conservative in-domain petroleum solutions toward cross-domain principles such as particle suspension/Stokes-law reasoning and yields **100%** success in the scaffolded condition reported in the paper.

Crucially, the cross-domain documents are already present in the fixed RAG context. Guidance changes which latent knowledge the model uses rather than adding new evidence.

Activation steering at a mid-depth semantic layer can abolish successful synthesis despite unchanged evidence/guidance, showing that intact internal representation is required.

### PoS diagnosis

This case separates:

```text
knowledge availability
from
relevance/bridge activation.
```

The system possesses relevant source knowledge but does not autonomously treat it as inferentially relevant to the target.

That is almost exactly the `mapping/relevance` distinction in the philosophy branch.

### Remaining gap

Human guidance effectively supplies the bridge:

```text
particle-handling problem in another domain
is relevant to
catalyst-circulation problem here.
```

The next system must discover and calibrate that bridge autonomously and determine whether it survives target-specific engineering constraints.

---

## 2. Shen, Druckmann & Zou 2026 — analogy as a scientific search operator

**Andrew Shen, Shaul Druckmann & James Zou, _Unlocking LLM Creativity in Science through Analogical Reasoning_ (2026).**  
Canonical: https://arxiv.org/abs/2605.11258

### Task

The paper focuses on **open-ended scientific solution generation**. Given a research problem, the system:

```text
extracts objects/relations
→ generates cross-domain analogies
→ represents each analogy by object mappings + shared relations
→ searches the analogous domain for candidate solutions
→ transfers those solution ideas back to the scientific target.
```

The representation explicitly allows **partial relational mapping**: not every problem relation must be preserved.

### Result

Analogical reasoning increases solution-diversity metrics by roughly **90–173%** over reported baselines and produces novel solutions more than 50% of the time in the reported evaluation, compared with some baselines as low as 1.6%.

The authors implement AR-generated approaches on four biomedical problems and report quantitative gains, including a nearly 13-fold improvement on one perturbation-effect distributional metric, improved cell-cell communication inference, brain-region interaction correlation around `ρ = 0.729`, and state-of-the-art performance on two oligonucleotide datasets.

### Evaluation structure

Analogy quality includes dimensions such as:

- structural depth;
- domain distance;
- applicability;
- novelty.

LLM-judged analogy-quality metrics are checked against expert pairwise preferences for selected dimensions. Most importantly, several generated scientific ideas are implemented and measured, so the work contains genuine downstream validation rather than only analogy ratings.

### PoS diagnosis

This is strong evidence that analogy can enlarge the **scientific search space**.

But the philosophy branch suggests separating two claims:

```text
A. analogy is a productive hypothesis/solution generator;
B. source-derived proposal is epistemically licensed for the target.
```

The paper demonstrates A very strongly and provides downstream empirical evidence for selected B cases. It does not imply that every high-quality structural analogy carries a calibrated transfer license.

---

# 3. The two cases expose opposite bottlenecks

## FCC case

```text
useful bridge exists
+ relevant source knowledge available
+ model usually fails to activate it autonomously.
```

Dominant problem:

```text
RELEVANCE / SOURCE ACTIVATION.
```

## Biomedical AR case

```text
model actively generates many cross-domain bridges
+ solution diversity rises strongly.
```

Dominant next problem:

```text
SELECTION / TRANSFER VALIDITY / VALIDATION COST.
```

As retrieval/generation improves, the bottleneck moves from `find a creative bridge` to `decide which creative bridge deserves experimental resources`.

---

# 4. A philosophy-informed discovery funnel

A future autonomous-science system could separate stages:

```text
1. DIVERGENT SEARCH
   generate far analogues aggressively

2. STRUCTURAL MAPPING
   identify object/relational correspondence

3. RELEVANCE / BRIDGE TEST
   why should mapped relation f bear on target variable g?

4. COMPARABILITY EVIDENCE
   what target/source evidence supports the bridge?

5. COUNTER-ANALOGUE / ROBUSTNESS
   what related source fails? which auxiliary is doing the work?

6. TRANSFER STATE
   LICENSED / CONDITIONAL / VETOED / UNKNOWN

7. EXPERIMENT DESIGN
   which target-side test most efficiently discriminates validity?

8. VALIDATION MEMORY
   update source-family / bridge / boundary reliability after experiment.
```

This reconciles scientific creativity with epistemic control instead of forcing one model stage to optimize both diversity and conservatism.

---

# 5. The key experimental hypothesis

The current AI results already show:

```text
analogy increases access to distant solution spaces.
```

The philosophy-derived contribution should therefore be tested on a different dependent variable:

```text
Does an epistemic controller improve
VALIDATED DISCOVERIES PER UNIT EXPERIMENTAL COST
without collapsing source diversity?
```

Possible measures:

- fraction of generated analogies reaching empirical validation;
- experimental budget per validated solution;
- false-positive bridge rate;
- calibration of applicability before experiment;
- counter-analogue retrieval before costly validation;
- diversity retained after filtering.

## Bottom line

AI-for-science already gives analogy a real job: **expand the space of plausible scientific moves**.

Contemporary philosophy of science becomes engineering-relevant at the next bottleneck:

> **How should a system move from an imaginative cross-domain bridge to a warranted, prioritized and falsifiable scientific transfer?**