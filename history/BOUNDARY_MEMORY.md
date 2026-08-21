# Boundary Memory — The Negative-Applicability Idea Already Has Strong Neighbors

**Snapshot: 21 August 2026.**

The historical-analogy branch initially treated persistent negative applicability memory as a largely open capability:

```text
source S is useful for target family T
EXCEPT when condition X holds,
because projection p fails under X
```

A deeper 2026 sweep shows that the **general memory primitive is already being built elsewhere**. The remaining historical-analogy gap is narrower: bind the learned boundary to a specific source→target relational mapping and projected lesson in an open event representation.

---

## 1. OBAM — learn discriminative boundaries from highly similar cases with conflicting outcomes

### Dong & Shang 2026 — Online Boundary-Aware Memory for Case-Based Reasoning Agents

**Zheng Dong & Luming Shang.** Amazon Science / ICML 2026 ecosystem.  
Canonical: https://www.amazon.science/publications/online-boundary-aware-memory-for-case-based-reasoning-agents

OBAM starts from exactly the failure that naive case retrieval creates:

> **highly similar cases can have conflicting outcomes, and the discriminative factor may be hidden.**

Instead of simply storing another failed case, OBAM detects decision boundaries online as contrasting cases arrive. Its memory entries encode:

- the **shared pattern** between cases;
- the **discriminative rule** that explains the outcome difference;
- refinements to that boundary as more evidence accumulates.

Across legal, medical and fraud reasoning tasks, the system outperforms ordinary in-context and agent-memory baselines in the reported experiments.

### Historical-analogy translation

This is remarkably close to the desired precedent memory:

```text
S1 and S2 both look like target family T
but outcomes diverge
→ identify discriminative condition X
→ store boundary rule
→ future source reuse should condition on X
```

The missing historical layer is that `shared pattern` and `X` are usually not fixed task features. They must be learned from disputed event mechanisms, institutions, actors and temporal relations.

---

## 2. ForecastCompass — resolved forecasts become factor and calibration memory

### Chang et al. 2026

**Yurui Chang, Yongkang Du, Yuanpu Cao, Jinghui Chen & Lu Lin, _ForecastCompass: Guiding Agentic Forecasting with Adaptive Factor Memory_.**  
Canonical: https://arxiv.org/abs/2605.30858

ForecastCompass (FoCo) rejects raw episodic storage as insufficient for forecasting. It maintains two reusable memories:

### Factor memory

Which predictive dimensions tend to matter for a class of forecasts, including warnings about misleading signals.

### Reasoning memory

How to update probabilities, handle uncertainty/conflicting evidence and remain calibrated.

After questions resolve, FoCo constructs a **retrospective trajectory**, contrasts it with the original forecast, and obtains two discrepancy signals:

```text
ΔF = factor-level error
ΔR = reasoning/calibration error
```

These discrepancies revise the memory used for later predictions. Experiments on Prophet Arena and FutureX with GPT-5-mini and Gemini-2.5-Flash report improvements in probabilistic accuracy and calibration.

### Historical-analogy translation

A historical controller could extend the discrepancy tuple:

```text
Δ = (
  Δrepresentation,
  Δsource_selection,
  Δmapping,
  Δprojection_validity,
  Δforecast_calibration
)
```

This is stronger than generic reflection because the correction is **typed by pipeline stage**.

---

## 3. WorldReasoner — separate outcome, evidence and causal reasoning quality

### Chi, Chamoun, Ding & Vlachos 2026

**_WorldReasoner: Evaluating Whether Language Model Agents Forecast Events with Valid Reasoning_.**  
Canonical: https://arxiv.org/abs/2606.11816

WorldReasoner builds 345 temporally bounded resolved forecasting tasks from 14,141 articles and evaluates agents along three axes:

1. **outcome quality** — was the probability/answer good?
2. **evidence quality** — were the cited pre-cutoff sources relevant and valid?
3. **reasoning quality** — does an optional causal event graph align with post-resolution hindsight structure?

Its controlled experiments find that temporally valid retrieval is a major driver of forecast accuracy and causal graph construction can improve key-event recovery, while agents still struggle to convert grounded evidence into calibrated probabilities.

### Historical-analogy lesson

A fluent precedent explanation can fail in several separable ways:

```text
correct outcome, wrong precedent
correct precedent, wrong causal mapping
correct mapping, uncalibrated probability
wrong outcome but epistemically reasonable pre-cutoff evidence
```

Historical Transfer Bench should preserve these distinctions rather than scoring one final prose answer.

---

## 4. What remains genuinely historical-analogy specific

After these neighboring systems, a defensible open object is:

```text
SOURCE S
+ target T
+ learned relational mapping M
+ candidate projection p
+ later failure evidence E

→ infer discriminative condition X
→ decide which component failed:
     source relevance?
     mapping?
     target rebinding?
     projection validity?
     execution/forecast noise?
→ store applicability boundary B(S, p, X)
→ reuse B on later targets without blacklisting S wholesale
```

OBAM supplies boundary-memory logic.

FoCo supplies discrepancy-driven forecast memory.

WorldReasoner supplies multi-axis validity evaluation.

The historical analogy contribution would be to bind them to an **endogenous, source-specific relational transfer contract**.

---

## 5. Stronger longitudinal benchmark design

The benchmark's negative-applicability phase should now include explicit baselines:

### Baseline A — episodic case memory

Store the failed example verbatim.

### Baseline B — generic reflection memory

Store a verbal lesson.

### Baseline C — OBAM-style boundary memory

Store shared pattern + discriminative condition.

### Baseline D — FoCo-style typed discrepancy memory

Store factor/reasoning discrepancy.

### Proposed historical transfer memory

Store:

```text
source family
mapped relation
projection
blocking condition
boundary confidence
supporting failure/success cases
representation version
```

The proposed system must demonstrate incremental benefit over C/D, not only over raw episodic memory.

---

## 6. A concrete memory object

```yaml
boundary_id: B17
source_family: sovereign-debt-crisis / banking-amplifier
source_instances: [S3, S8]
target_pattern: liquidity-shock + leveraged-intermediary
mapped_relation: forced-sale -> collateral-price feedback
projection: "liquidity shock will amplify through fire-sale dynamics"
status: conditional
blocking_condition: "central liquidity facility absorbs collateral sales before margin spiral"
evidence_for_boundary: [case_12_failure, case_19_success]
confidence: 0.81
representation_version: R4
last_updated: ...
```

This is much closer to reusable analogical intelligence than `remember case 12 was wrong`.

---

## Bottom line

The field already has increasingly sophisticated ways to learn from resolved cases, discover discriminative boundaries and update forecasting memory.

The historical frontier is therefore not generic continual learning. It is:

> **learn and retain the applicability boundary of an individual precedent-derived relation/projection in an open, revisable historical event representation.**
