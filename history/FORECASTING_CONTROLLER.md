# Forecasting-Trained Models as the Calibration Layer for Historical Analogy

**Snapshot: 21 August 2026.**

Historical-analogy systems currently inherit their probability judgments from generic language models or agent scaffolds. A separate 2026 forecasting line shows that **forecasting calibration itself can be trained**, suggesting that the eventual precedent controller need not rely on generic reasoning ability alone.

---

## 1. OpenForecaster — forecasting as a post-training objective

### Chandak et al., ICML 2026

**Nikhil Chandak, Shashwat Goel, Ameya Prabhu, Moritz Hardt & Jonas Geiping, _Curating the Future: A Scalable Recipe for Training Open-Ended Forecasters_** (earlier title: _Scaling Open-Ended Reasoning to Predict the Future_).  
Canonical: https://arxiv.org/abs/2512.25070  
Project: https://openforecaster.github.io/scaling-data/

The work creates **OpenForesight**, roughly 52k forecasting questions automatically curated from global news, and post-trains Qwen3 thinking models into **OpenForecaster 8B**.

The leakage design is especially relevant to historical analogy:

- an offline/static news corpus is used for training-data creation and retrieval;
- training events stop before the base model release / held-out future period;
- final testing occurs on later real events not inspected during model development;
- RL can use the eventual resolved outcome as supervision even when detailed expert reasoning traces are unavailable.

Forecasting training improves **accuracy, calibration and consistency**, and the authors report that calibration improvements transfer to other forecasting benchmarks. The 8B specialized model competes with much larger proprietary models on held-out open-ended forecasts.

### Historical-analogy implication

The analogy controller should not necessarily be:

```text
generic LLM
+ historical retrieval prompt
+ verbal confidence
```

A stronger architecture is:

```text
historical precedent generator / mapper
→ forecasting-trained calibration head/controller
→ probability / abstention / evidence-acquisition decision
```

The reward can explicitly penalize:

- overconfident transfer from vivid precedents;
- failure to use base rates;
- failure to update when target evidence arrives;
- excessive confidence under competing mechanism representations;
- repeated use of a source family after its applicability boundary has failed.

---

## 2. FutureSim — evaluation should be longitudinal, not one-shot

### Goel et al., ICML 2026 AI Forecasting Workshop Best Paper

**Shashwat Goel et al., _FutureSim: Replaying World Events to Evaluate Adaptive Agents_.**  
Canonical: https://arxiv.org/abs/2605.15188

FutureSim replays real-world news chronologically from January–March 2026 and asks agents to forecast events beyond their model knowledge cutoff. Questions resolve during the simulation, giving agents real feedback while the news environment continues to change.

The benchmark is difficult: the best evaluated agent reaches about **25% accuracy**, and several agents have a **negative Brier skill score**, worse than making no prediction under the benchmark baseline.

Its importance for historical analogy is the evaluation structure:

```text
time t0: retrieve precedents → forecast
new evidence arrives
some forecasts resolve
system observes transfer success/failure
→ update memory / source applicability / probability discipline
time t1: new target / revised target
```

This is almost exactly the environment required to test whether analogical applicability memory improves through experience.

### Stronger benchmark than retrospective explanation

A historical-transfer controller should be evaluated on a chronological replay where:

- future target evidence is unavailable until its historical release time;
- precedent recommendations are logged before resolution;
- projected claims receive proper-scoring-rule probabilities;
- failures later become training/test-time adaptation signals;
- the benchmark measures whether the controller changes *which precedents it trusts and for which projections*.

---

## 3. Forecasting training does not solve representation or transfer validity

OpenForecaster solves a different problem from CANA.

```text
OpenForecaster:
question + evidence → calibrated prediction

CANA:
target event → historical mechanism analogues → structural inference
```

The useful integration is not to relabel forecasting as analogy. It is to use forecasting-trained probability discipline **after** analogy has generated a structured hypothesis.

A precedent can be structurally interesting while contributing little incremental predictive information. The controller needs to learn that distinction.

---

## 4. Proposed joint objective

For candidate precedent `S`, projection `p`, target `T` and reference class `C`:

```text
R =
  - proper_scoring_loss(p)
  + source_retrieval_utility
  + disanalogy_localization_reward
  + calibration_reward
  + evidence_update_reward
  - hindsight_leakage_penalty
  - correlated_precedent_double_counting
  - repeated_invalid_transfer_penalty
```

The historical component supplies structured transfer hypotheses; the forecasting component supplies empirical accountability.

---

## 5. Benchmark consequence

Historical Transfer Bench should eventually have two evaluation modes:

### Static transfer diagnosis

Can the system correctly label:

`LICENSED / CONDITIONAL / VETOED / UNKNOWN`?

### Dynamic forecast replay

Can the same transfer assessments improve probabilities over time, and does the system learn from resolved failures?

Metrics:

- projection macro-F1;
- Brier score / log score;
- calibration error;
- Brier skill relative to reference-class and non-analogy baselines;
- update responsiveness after new evidence;
- applicability-memory improvement;
- repeated-invalid-transfer rate.

---

## Bottom line

The 2026 forecasting literature removes one excuse for historical analogy: probability calibration need not be left as an emergent property of a generic LLM.

The stronger frontier is therefore:

> **mechanism-rich precedent generation and selective transfer, coupled to a forecasting-trained controller that is rewarded on future outcomes and evaluated through chronological replay.**
