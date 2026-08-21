# Case Analogies + Reference Classes — The Hybrid Is Older Than LLMs

**Snapshot: 21 August 2026.**

This note tests whether the apparent bridge between rich historical precedents and outside-view/reference-class calibration is genuinely new. The answer is **no at the abstract forecasting level, yes at the open-event foundation-model level**.

The mature pre-LLM lesson is simple:

> **a few vivid analogies are often less robust than a broader reference class of analogies, but a pure reference class can lose the mechanism-rich structure that makes a particular precedent informative.**

The modern frontier is therefore not to invent a case/class hybrid from scratch. It is to move that hybrid into open-text, mechanism-level historical reasoning while retaining probabilistic calibration and source-level auditability.

---

## 1. Lovallo, Clarke & Camerer 2012 — robust analogizing already combines cases and the outside view

**Dan Lovallo, Carmina Clarke & Colin F. Camerer, “Robust analogizing and the outside view: two empirical tests of case-based decision making,” Strategic Management Journal 33 (2012), 496–512.**  
Canonical: https://doi.org/10.1002/smj.962

This is the strongest direct prior art found for our proposed case/class bridge.

The paper asks how decision-makers should use analogies under uncertainty. In one empirical study of private-equity decisions, an **outside view formed from a reference class of analogies** performs better than relying on a few analogies familiar to the decision-maker. In a second study, the authors introduce **similarity-based forecasting (SBF)**, explicitly combining reference-class forecasting with case-based decision making; it outperforms regression models in their film-revenue forecasting test.

The important architecture is:

```text
current target
→ identify comparable past cases
→ weight/select them by similarity
→ aggregate realized outcomes across the class
→ forecast target
```

This is not a rich causal-event analogy system, but it establishes three points that matter for historical-analogy AI:

1. the `single vivid precedent` problem is empirically real;
2. analogical source selection and reference-class calibration can be unified rather than treated as rival methods;
3. analogy quality should ultimately be judged by downstream predictive/decision performance, not only perceived resemblance.

### What remains missing relative to CANA-style history

SBF operates over comparatively regular forecasting objects. It does not need to represent a historical event as contested mechanisms, actors, institutions, temporal sequences and countervailing differences. Nor does it return projection-level licenses such as `this lesson transfers but that one does not`.

So the novelty claim for an LLM-era system must be narrower:

> **open semantic representation + mechanism-aware precedent reasoning + distributional outside-view calibration.**

---

## 2. Modern RCF is already becoming machine-selected and hybrid

### Cantarelli et al. 2026 — RCF research agenda

**Chantal C. Cantarelli, Kate Davis, Jeffrey K. Pinto & Neil Turner, “Reference class forecasting: promises, problems, and a research agenda moving forward,” Production Planning & Control 37(7), 691–709.**  
Canonical: https://doi.org/10.1080/09537287.2025.2578708

The 2026 review describes a shift from classical non-parametric reference classes toward **hybrid RCF**, including Bayesian/probabilistic models, kernel methods, k-NN-style analogue selection, and Gradient Boosted Regression Trees. The central unresolved problem remains reference-class validity and applicability: which historical cases are sufficiently comparable, and how does one avoid manipulating the answer through class construction?

That is the same upstream selection problem faced by historical analogy, but the downstream output is much better disciplined: predictive distributions, quantiles and backtests rather than a single narrative lesson.

---

## 3. Salih & El-adaway 2025/26 — ML + RCF in a real project dataset

**Fareed Salih & Islam H. El-adaway, “Integrating Machine Learning and Reference Class Forecasting for Construction Risk Contingency Prediction,” Computing in Civil Engineering 2025.**  
Canonical: https://doi.org/10.1061/9780784486436.011

Using data from **294 design-build building projects**, the authors compare machine-learning predictions with reference-class-derived distributions for cost/duration risk contingency. The workflow explicitly combines predictive ML with historical outside-view distributions rather than using one as a replacement for the other.

This is useful because it shows a modern hybrid can be empirically evaluated over a nontrivial historical case base.

### Limitation for our branch

The class variables and target quantities are strongly structured. The method does not have to discover an event representation from raw political, economic or technological narratives.

---

## 4. DoD AI–RCF 2026 — automatic class construction is now an explicit defense objective

**Monte L. Ellis Jr., “Enhancing Decision Accuracy in DoD Acquisition: Integrating Artificial Intelligence with Reference Class Forecasting,” Naval Postgraduate School, NPS-AM-26-221, June 2026.**  
Canonical: https://dair.nps.edu/bitstream/123456789/5501/1/NPS-AM-26-221.pdf

This capstone is especially relevant to the defense/precedent branch because it explicitly proposes using **ML/NLP to automate reference-class construction from heterogeneous acquisition records** and to output probabilistic P50/P80-style forecasting bands for cost, schedule and technology-readiness decisions.

Its stated motivation is almost exactly the analogy/source-selection problem in a constrained operational domain:

- manual analogue selection does not scale;
- heterogeneous defense programs make `valid comparison class` difficult;
- AI can group historical programs into statistically coherent classes and extract patterns;
- the outside-view distribution should anchor decision-makers against optimism and planning-fallacy bias.

The report also explicitly notes an edge case that matters for historical analogy: when **no valid reference class exists**, hybridization with subject-matter judgment or Bayesian methods may be necessary.

### Evidence status

This is not evidence that a fully deployed DoD historical-analogy controller exists. The study is qualitative/conceptual with comparative cases and simulated/holdout analysis. It is useful as evidence of an **engineering direction and institutional use case**, not as a solved system.

---

## 5. Guan & Chen 2026 — historical analog retrieval + LLM rule compression under strict time hygiene

**Mao Guan & Qian Chen, “Leakage-Aware Benchmarking of LLM Forecasting: Real-Time Nowcasts as the Decision-Time Input for Macro Factor Ranking,” ICML 2026 Workshop on AI Forecasting (non-archival).**  
Canonical: https://arxiv.org/abs/2606.22719

This is one of the closest contemporary examples of a learned system turning historical analogs into reusable decision guidance under a strict temporal cutoff.

At each month-end, the system:

```text
constructs a decision-time macro state
→ retrieves K=4 historical macro-analog months from ≥12 months earlier
→ critic LLM compresses the analogs into ONE tactical rule
→ rolling rule memory feeds an actor LLM
→ actor ranks seven equity style factors
```

The evaluation is explicitly leakage-aware: CPI/unemployment are lagged to actual availability and unreleased inflation is represented by archived Cleveland Fed nowcasts available at the decision date.

### Why this matters

It realizes a compact form of:

`historical analogs → abstraction/rule → target action`.

That is closer to analogical transfer than a plain kNN reference class. It also creates a natural analogue to a future historical-event system where several past crises are compressed into one conditional mechanism lesson.

### The most important result is a caution

The full LLM pipeline reports a **median monthly Spearman rank IC of +0.154**, but the authors find that a simple kNN macro-analog baseline under the same time-safe information set recovers a comparable median signal. The LLM's residual advantage is concentrated in mean rank IC / extreme rankings and is statistically underpowered in the 36-month sample.

This is a crucial benchmark-design lesson:

> **the gain from rich LLM reasoning must be separated from the gain produced merely by retrieving a good historical neighborhood.**

A CANA-like system should therefore be compared against strong non-generative analogue/reference-class baselines using exactly the same candidate-source universe and temporal constraints.

---

## 6. The case/class frontier is now narrower

The broad idea

```text
rich precedent + reference class
```

is established prior art. The unresolved frontier is a specific integration problem:

```text
raw target event
→ learned relational/mechanistic representation
→ retrieve a few rich precedents S1...Sk
→ construct a broader reference class C under stated comparability criteria
→ produce P(Y | C)
→ derive precedent-specific projected claims p1...pn
→ compare each projection against target evidence and outside-view base rate
→ license / condition / veto / request evidence
→ update applicability memory when outcomes arrive
```

No general open-event foundation-model system found in this sweep closes that loop.

---

## 7. Why the outside view should not simply dominate

A pure reference-class system can be wrong when the target contains a genuinely exceptional mechanism. Historical analogy is valuable precisely because it can represent the reason for deviation.

The controller therefore needs a burden-of-proof rule:

```text
outside-view base rate = prior discipline
rich mechanism analogy = candidate reason to deviate
```

A deviation from the reference-class prediction should require explicit target-side evidence for the mechanism that allegedly makes the case exceptional.

This can be operationalized:

```text
reference class escalation rate: 0.28
mechanism analogue forecast: 0.68
claimed exceptional factor: X

controller decision:
  0.68 is not licensed until target evidence for X crosses threshold τ
```

The point is not to force all reasoning back to base rates. It is to make **historical exceptionalism testable**.

---

## 8. Implication for Historical Transfer Bench

The benchmark should include a **case-vs-class conflict track**.

Each target can provide:

- one or more vivid, mechanism-rich precedents;
- a larger historical reference-class pool with realized outcomes;
- multiple defensible and misleading class definitions;
- target-side evidence that may or may not justify deviation from the base rate.

Score whether the model can:

1. resist a famous precedent when the broad class contradicts it and no exceptional mechanism is evidenced;
2. correctly deviate from the base rate when a target-specific mechanism is well supported;
3. identify when the reference class itself is invalid/too heterogeneous;
4. report uncertainty rather than choose one side mechanically;
5. state which claim changes when case evidence and class evidence conflict;
6. outperform a strong time-safe kNN/reference-class baseline rather than merely redescribe its signal.

---

## Bottom line

The literature falsifies any claim that `case analogy + outside view` is an unexplored idea. It has empirical and forecasting precedents going back at least to Lovallo–Clarke–Camerer and is now being modernized through ML-enabled reference-class construction and leakage-aware LLM analog retrieval.

The defensible 2026 frontier is:

> **Can a foundation model build semantically rich historical precedents and a statistically calibrated reference class from the same open event universe, then demonstrate incremental value over strong analogue baselines by controlling individual historical lessons rather than merely producing a persuasive analogy narrative?**
