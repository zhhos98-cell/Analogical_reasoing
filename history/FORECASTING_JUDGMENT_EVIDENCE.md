# Do Historical Analogies Actually Mark Better Forecasting Judgment?

**Snapshot: 21 August 2026.**

A historical-analogy system should eventually be judged against real forecasting outcomes, not only expert ratings of whether its analogies sound plausible. A useful 2026 reality check comes from large-scale forecasting-tournament data.

## Karvetski et al. 2026 — 55k forecast rationales

**Christopher W. Karvetski et al., “Measuring Judgment Quality in Natural-Language Explanations: Evidence from Forecasting Tournaments.”**  
Canonical: https://arxiv.org/abs/2606.30987

The study uses more than **55,000 probabilistic forecast–rationale pairs** from the IARPA ACE forecasting tournament and scores 60 theory-guided Explanation Quality Markers (EQMs) with LLMs. The questions span political, economic and security domains and resolve against realized outcomes.

The paper explicitly includes several precedent-related patterns:

- **Analogies** — using another event/question as an analogy;
- **Historic Expertise** — advanced historical knowledge relevant to the question;
- **Best Practices** — including historical precedents while balancing differences in the current context;
- **Statistical Reasoning** — comparison classes, base rates and other statistical use of past occurrences;
- **Statistical Causal Blend** — combining statistical evidence with causal drivers.

### Main result

The *composite* EQM score is meaningfully related to forecasting accuracy:

- forecast-level correlation ≈ **0.19**;
- forecaster-level correlation ≈ **0.51**;
- it outperforms pre-LLM text-analysis composites.

But isolated historical/analogical language is not itself a strong quality marker. In the reported OLS coefficients:

- `Analogies`: about **0.001** forecast-level, **0.012** forecaster-level;
- `Historic Expertise`: approximately **0.000 / 0.000**;
- the strongest positive signals include rationale–forecast alignment and other broader reasoning/alignment patterns;
- confirmation bias, extreme confidence, simplification and rationale/forecast misalignment are associated with worse performance.

The authors emphasize that structured analytical reasoning patterns as a family tend to associate with better accuracy; no analytical pattern is negatively correlated with both accuracy measures. The important point for this branch is narrower:

> **historical analogy is not a sufficient quality signal by itself.**

---

## Implication for historical-analogy AI

A benchmark that rewards `uses a historical precedent` risks measuring style rather than judgment.

The stronger target is a **bundle of disciplined operations**:

```text
historical precedent
+ explicit source/target differences
+ reference-class/base-rate comparison
+ competing precedent / disconfirming evidence
+ calibrated probability
+ rationale–forecast consistency
+ update conditions
```

This aligns with what the rest of this branch has found from different directions:

- CANA makes mechanism alignment and limitations explicit;
- reference-class forecasting supplies outside-view calibration;
- competing-hypothesis methods force diagnostic comparison;
- legal precedent supplies distinguishing/veto operations;
- temporal validation prevents hindsight from masquerading as foresight.

The forecasting-tournament evidence suggests these should be treated as a **joint judgment architecture**, not as decorations around an analogy.

---

## Benchmark consequence

Historical Transfer Bench should include a rationale-quality audit but should not make analogy presence a positive label.

Useful auxiliary measures:

- rationale–probability alignment;
- explicit condition to update;
- presence of counter-precedent / counterevidence;
- use of a defensible base rate;
- confidence penalty for unresolved mechanism ambiguity;
- avoidance of extreme confidence when projection validity is partial;
- post-resolution calibration / Brier score.

A model should be able to score highly while saying:

> `No historical precedent is sufficiently diagnostic here; the broad reference class supports 0.35 and current evidence does not justify departing from it.`

That is a better historical-analogy system than one that always produces an eloquent past parallel.
