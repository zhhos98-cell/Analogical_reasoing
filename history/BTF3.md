# BTF-3 — A Larger Frozen Environment for Historical-Transfer Experiments

**Snapshot: 21 August 2026.**

Bench to the Future 3 (BTF-3) is currently one of the most useful real-world substrates for testing whether historical analogies improve forecasts rather than merely improve narratives.

Canonical dataset: https://huggingface.co/datasets/BTF-2/BTF-3  
Evaluation page: https://drb.futuresearch.ai/

## Dataset

BTF-3 contains **1,907 resolved pastcasting questions**:

- **1,515 binary** questions;
- **392 numeric** questions;
- target present dates from late April to late May 2026;
- resolutions from mid-May to early July 2026;
- a 30-day cohort plus a 60-day extension;
- a frozen pre-resolution web corpus for each target.

The numeric track is especially useful for transfer work because it lets us measure whether a precedent changes an entire predictive distribution rather than only a yes/no answer.

FutureSearch reports that each question is researched against a server-side frozen corpus containing tens of thousands of pages. The agent operates at a simulated `now`; search tools cannot return post-cutoff documents. This makes BTF-3 substantially cleaner than ordinary retrospective prompting, though parametric hindsight in the model weights remains a separate concern.

## Why it matters for historical analogy

A historical-analogy experiment can run multiple agents on exactly the same target, information cutoff and retrieval environment:

```text
B0  base-rate / simple structured baseline
B1  ordinary forecast agent
B2  time-safe kNN historical analogue retrieval
B3  reference-class forecast
B4  rich historical-precedent retrieval
B5  mechanism mapping
B6  projection-level transfer controller
B7  calibrated forecasting controller
```

The incremental value of historical analogy is then an empirical quantity rather than an interpretive judgment.

For binary targets use Brier score / Brier skill. For numeric targets use the benchmark's distributional scoring rule and test whether rich precedent reasoning improves both location and calibration.

## Current public performance context

The FutureSearch evaluation page currently reports pooled BTF-3 scores where lower is better. At the 21 August 2026 snapshot, the top listed FutureSearch system is around **0.116**, Claude Opus 5 xhigh around **0.118**, and GPT-5.6 Sol high around **0.135**. These figures should be treated as a moving leaderboard snapshot, not a permanent benchmark property.

The important methodological point is that a complete BTF-3 run can return 1,907 graded results within hours against the same frozen evidence environment. That enables genuine ablation rather than waiting months for prospective questions to resolve.

## Historical-transfer mining strategy

BTF-3 can be mined for candidate boundary cases by searching for forecasts with:

```text
high confidence
+ rationale citing recurrence / historical precedent / past regime
+ wrong resolution or large distributional error
+ pre-cutoff evidence of a regime change, terminal condition or discriminative factor
```

These cases can then be converted into controlled experiments:

1. **pattern only**;
2. **pattern + critical boundary evidence**;
3. **pattern + irrelevant difference**;
4. **matched case where the boundary is absent**.

Measure the probability response induced by the difference, not only final accuracy.

## Caveat: frozen web is not frozen model weights

BTF-3 prevents retrieval leakage, but a 2026 model may already contain facts about some May–July 2026 outcomes. Historical-transfer work should therefore pair BTF-3 with:

- parametric hindsight probes;
- model-cutoff comparisons;
- entity/date masking where feasible;
- time-locked models for selected historical periods;
- prospective ForecastBench rounds as the final validation tier.

## Bottom line

BTF-3 turns historical analogy from a small-case interpretive exercise into a scalable ablation problem:

> **Does adding a rich, selectively controlled historical precedent improve out-of-sample probability forecasts beyond strong time-safe analogue and reference-class baselines?**

If not, mechanism-rich analogy may be explanatory decoration rather than added predictive intelligence.