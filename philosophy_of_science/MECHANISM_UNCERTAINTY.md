# Mechanism Uncertainty — Predictive Transfer Is Not Explanatory Transfer

**Snapshot: 21 August 2026.**

A source/model can predict aspects of a target without correctly representing the mechanism that generates those target outcomes.

This matters for analogy because a system may achieve genuine predictive usefulness while still overclaiming causal/explanatory transfer.

---

## 1. Jensen 2026 — from link uncertainty to mechanism uncertainty

**Sara Pernille Jensen, “Uncertainties about link uncertainty: ML models as phenomenological models,” _Synthese_ 207 (2026), article 111.**  
DOI: https://doi.org/10.1007/s11229-026-05509-w

Jensen revisits Emily Sullivan's claim that scientific ML models are analogous to toy models and that their explanatory limitation is mainly `link uncertainty` between model and target.

Jensen argues that this often grants ML models too strong an explanatory role. Predictive ML models are better understood as **phenomenological models**: empirically grounded representations of informational/statistical dependencies whose deeper target mechanism remains uncertain.

The crucial uncertainty is therefore often:

```text
MECHANISM UNCERTAINTY
```

not simply whether the model has any empirical link to the target.

---

## 2. Three transfer questions

For analogical AI, distinguish:

```text
PREDICTIVE TRANSFER:
Does source-derived information improve target prediction?

CAUSAL TRANSFER:
Does the same causal relationship/mechanism operate in target?

EXPLANATORY TRANSFER:
Does the source provide a scientifically adequate explanation of target behavior?
```

These can receive different answers.

Example:

```yaml
predictive_transfer: LICENSED
causal_transfer: UNKNOWN
explanatory_transfer: UNKNOWN
```

A statistical historical trajectory can forecast well without sharing the same political mechanism.

---

## 3. Why this matters for analogical discovery

Suppose a cross-domain scientific analogue yields a high-performing solution.

That establishes:

```text
pragmatic/predictive utility
```

but does not automatically establish:

```text
mechanistic isomorphism
```

or:

```text
scientific explanation.
```

A discovery agent should therefore avoid narrativizing success into mechanism certainty after the fact.

---

## 4. Target-side mechanism validation

If mechanism transfer is claimed, require additional evidence such as:

- intervention/counterfactual tests;
- predicted fingerprints/outcome features;
- mediator/moderator measurements;
- causal pathway falsification;
- target-side experiments;
- independent mechanistic observations.

This fits the comparative-process-tracing and analogue-experiment branches.

---

## 5. Two uncertainty heads

A controller can maintain:

```text
U_pred:
  uncertainty in the projected target outcome

U_mech:
  uncertainty that the source-side mechanism actually explains target dependence
```

These should not be forced to move together.

Example:

```text
P(outcome Y) = 0.82
mechanism-transfer confidence = 0.41
```

The system can be a strong forecaster and a weak explainer at the same time.

---

## 6. Relation to claim strength

Claim-strength permissions can be augmented with mechanism status.

```text
Prediction:
  supported statistically

Mechanism statement:
  exploratory / unconfirmed

Intervention recommendation:
  requires causal validation
```

This is especially important when acting requires intervention reasoning rather than passive prediction.

---

## 7. Historical analogy translation

Historical analogues frequently blend prediction and explanation:

```text
past trajectory matches
→ therefore same mechanism
→ therefore same outcome
```

Jensen's distinction blocks the middle inference.

A time-series analogue may be useful as:

```text
forecast signal
```

while remaining weak as:

```text
historical causal explanation.
```

Likewise a CANA-style mechanism analogue may be explanatorily plausible but still need quantitative calibration for predictive use.

---

## 8. Benchmark design

Evaluate separate axes:

```yaml
prediction_score:
mechanism_identification_score:
mechanism_falsification_score:
explanation_entitlement:
```

Include cases where:

1. different mechanisms yield the same predictive pattern;
2. same mechanism produces different outcomes under different cofactors;
3. source prediction succeeds for accidental/statistical reasons;
4. source mechanism is correct but quantitative target effect differs.

This prevents outcome accuracy from becoming a universal proxy for analogical epistemic quality.

---

## 9. Failure modes

### Predictive success inflation

```text
forecast correct
→ model claims mechanism confirmed
```

### Mechanism-story inflation

```text
mechanism narrative plausible
→ model assigns excessive predictive probability
```

### Intervention inflation

```text
observational prediction transfers
→ model assumes intervention effect transfers
```

These should be scored separately.

---

## Bottom line

A mature analogue controller should be able to say:

> **This source improves prediction of the target, but the mechanism connecting them remains uncertain.**

or the reverse:

> **This source makes the mechanism plausible, but it does not yet support a calibrated quantitative forecast.**

That separation is essential for responsible analogical reasoning in science.
