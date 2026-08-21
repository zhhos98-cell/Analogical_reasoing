# Claim Strength and Extrapolation — Stronger Target Claims Need Stronger Transfer Evidence

**Snapshot: 21 August 2026.**

A central lesson of contemporary extrapolation theory is that there is no single question called `does this source transfer?`.

Different target claims demand different extrapolation arguments and different evidence.

A useful hierarchy is:

```text
CAUSAL RELEVANCE
→ DIRECTION / QUALITATIVE EFFECT
→ QUANTITATIVE EFFECT SIZE / PROBABILITY
→ POLICY / ACTION
```

The evidential burden generally increases as the claim becomes stronger and more decision-consequential.

---

## 1. Fuller 2025 — logical, evidential and practical problems are distinct

Jonathan Fuller, **“Problems of Extrapolation,”** chapter 7 of *The New Modern Medicine* (Oxford University Press, 2025), pp. 307–355.  
DOI: https://doi.org/10.1093/9780190066178.003.0010

Fuller separates three problems:

### Logical problem

What premises would make the extrapolation argument valid?

### Evidential problem

What evidence actually supports those study–target comparability premises?

### Practical problem

Given residual uncertainty, consequences and values, when should we accept/use the extrapolated conclusion?

These are three different control stages.

---

## 2. Extrapolating causal relevance is weaker than extrapolating effect size

Fuller's discussion is particularly useful because it distinguishes **qualitative causal similarity** from **quantitative causal similarity**.

To extrapolate that a factor plays the same qualitative causal role in source and target may require evidence that relevant structures/mechanisms are functionally similar.

To extrapolate the **effect size**, one needs more:

- stronger structural similarity;
- compatible quantitative causal principles;
- information about the distribution of relevant mechanisms/cofactors in source and target;
- sometimes transport formulas or mechanism–cofactor analysis.

Thus:

```text
source establishes: X matters in target
```

is a weaker claim than:

```text
source establishes: X changes target outcome by 20%
```

and should require a weaker transfer contract.

---

## 3. A claim-strength ladder for analogical AI

For each projection, type the target claim.

```yaml
claim_type:
  - RELEVANCE
  - DIRECTION
  - ORDINAL_RISK
  - QUANTITATIVE_PROBABILITY
  - EFFECT_SIZE
  - INTERVENTION_EFFECT
  - ACTION_RECOMMENDATION
```

Then require evidence appropriate to that level.

Example:

```text
Historical analogue suggests that alliance fragmentation is a relevant escalation mechanism.
Status: LICENSED as RELEVANCE claim.

Historical analogue suggests escalation probability is 0.70.
Status: UNKNOWN / insufficient quantitative transport evidence.

Historical analogue implies intervention A should be adopted.
Status: not licensed without target probability, costs, alternatives and decision threshold.
```

---

## 4. Structural analogy can support comparability without directly predicting the target

Fuller's solution to the evidential problem uses structural analogies as evidence that source and target factors play comparable causal roles.

The important logic is:

```text
structural evidence
→ supports a comparability/bridge premise
→ source result + bridge premise
→ target conclusion
```

The structural evidence should not already entail the target outcome; otherwise the source result becomes epistemically dispensable and the extrapolation collapses into the extrapolator's circle.

### AI implication

A transfer controller should distinguish:

```text
E_bridge: evidence that source and target are comparable
E_target: evidence directly predicting the target outcome
```

If the same target evidence alone already establishes the projection, the historical/scientific analogue may add explanation but not independent predictive support.

---

## 5. Different projections from the same source can sit at different claim strengths

One source can support:

```text
p1: mechanism X is relevant                 → strong support
p2: outcome direction is upward              → moderate support
p3: probability is 0.70                      → weak support
p4: take intervention A now                  → requires decision analysis
```

This is another reason whole-source `good analogy / bad analogy` labels are inadequate.

The controller needs projection-specific **claim type + transfer status**.

---

## 6. Practical extrapolation is decision-theoretic

Fuller emphasizes that deciding when to extrapolate cannot be determined by logical/evidential considerations alone.

Practical acceptance depends on:

- cost of false positive;
- cost of false negative;
- benefit of waiting for more evidence;
- urgency;
- ethical constraints;
- availability of alternatives.

Engineering consequence:

```text
P(target claim | evidence)
≠
action automatically.
```

Separate:

```text
EPISTEMIC CONTROLLER
→ calibrated target probability / transfer status

DECISION CONTROLLER
→ action under utilities, constraints and stakes
```

This also matches the pursuit-vs-confirmation distinction elsewhere in the branch.

---

## 7. Transfer-strength calibration benchmark

Construct items where the same source supports successively stronger claims.

Example:

```text
C1: X is causally relevant in T
C2: X increases Y in T
C3: X increases Y by approximately magnitude m
C4: therefore intervention A has expected net benefit
```

Provide evidence sufficient for C1/C2 but insufficient for C3/C4.

A calibrated system should not propagate confidence upward automatically.

Metrics:

- claim-strength overreach rate;
- probability monotonicity under stronger evidential requirements;
- correct abstention at quantitative/action levels;
- calibration by claim type;
- evidence-threshold sensitivity.

---

## 8. Relation to historical analogy

Historical precedent systems often jump silently between claim levels:

```text
past mechanism resembles present mechanism
→ same outcome likely
→ numerical forecast
→ policy recommendation
```

Each arrow needs its own justification.

Historical Transfer Bench should therefore label not only:

```text
LICENSED / CONDITIONAL / VETOED / UNKNOWN
```

but also:

```text
what strength of claim is licensed.
```

A precedent can be highly useful as a **mechanism warning** while being weak as a quantitative forecast.

---

## 9. Relation to scientific discovery

The ladder also separates:

```text
PURSUE mechanism X
```

from

```text
CONFIRM mechanism X
```

and from

```text
QUANTIFY effect of X
```

This avoids converting creative scientific analogy into unjustified numerical certainty.

---

## 10. Engineering hypothesis

A transfer controller that explicitly conditions its evidential threshold on target-claim strength should reduce:

- confident numerical over-transfer;
- action recommendations based on merely qualitative analogy;
- whole-source acceptance;
- false precision.

The simplest test is an ablation:

```text
same analogical reasoning model
vs
same model + explicit claim-strength state / reward
```

and measure quantitative overclaim and calibration.

---

## Bottom line

The correct question is not merely:

> **Does the analogy transfer?**

It is:

> **What exactly is being transferred — causal relevance, direction, magnitude, probability or action — and is the available comparability evidence strong enough for that level of claim?**

That hierarchy is one of the clearest philosophy-of-science constraints that can be made operational in an AI analogue controller.
