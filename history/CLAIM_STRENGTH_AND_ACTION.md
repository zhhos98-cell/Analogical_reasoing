# Historical Analogy Claim Strength — Warning, Forecast and Action Are Different Permissions

**Snapshot: 21 August 2026.**

Historical precedents are often rhetorically compressed into one move:

```text
past case resembles present case
→ therefore the same thing will happen
→ therefore we should act accordingly
```

A transfer-valid historical system should split this into distinct claim strengths.

---

## 1. Historical analogies can be useful at a weak claim level

A precedent may securely support:

```text
mechanism X deserves attention
actor Y may become pivotal
constraint Z is worth checking
scenario Q should be included
```

without supporting:

```text
Q is 70% likely
```

or:

```text
policy A should be adopted.
```

This distinction lets historical analogy remain useful even when quantitative transport is weak.

---

## 2. Proposed claim-strength ladder

```text
H1 — RESEARCH RELEVANCE
     this precedent identifies a mechanism/factor worth investigating

H2 — QUALITATIVE MECHANISM
     the same mechanism is plausibly active in the target

H3 — DIRECTIONAL TRAJECTORY
     the mechanism makes outcome Y more/less likely

H4 — QUANTITATIVE FORECAST
     the precedent contributes to a numerical probability/magnitude

H5 — DECISION RECOMMENDATION
     the forecast plus costs/stakes licenses action A
```

Each level requires additional evidence.

---

## 3. Example

A past sanctions episode might license:

```text
H1:
terminal legal deadlines matter for policy cadence
→ strong
```

and perhaps:

```text
H2:
current sanctions process also has a terminal deadline mechanism
→ conditional on target evidence
```

but not automatically:

```text
H4:
probability of another amendment = 0.70
```

The numerical claim requires a broader statistical/reference-class calibration and evidence about target-specific mechanism strength.

---

## 4. Historical warning vs historical prediction

This distinction is especially important for policy intelligence.

A historical analogue can function as a **warning system**:

```text
if mechanism X is active, failure mode F becomes possible
```

This can be valuable even if:

```text
P(F)
```

cannot be estimated reliably.

A controller should therefore be able to output:

```yaml
precedent_utility: HIGH
qualitative_mechanism_support: MODERATE
quantitative_forecast_support: LOW
policy_action_support: UNKNOWN
```

instead of one analogy confidence.

---

## 5. Reference-class role grows with claim strength

Rich event analogy may be enough to motivate H1/H2.

For H3/H4, the system increasingly needs:

- competing precedents;
- outcome frequencies;
- reference classes;
- transportability estimates;
- calibrated forecasting models;
- target-side evidence.

For H5 it additionally needs:

- action costs;
- false-positive/false-negative consequences;
- alternatives;
- timing;
- ethical/political constraints.

Thus the architecture should add components as claim strength rises rather than force one precedent to do all epistemic work.

---

## 6. Benchmark extension

Historical Transfer Bench should annotate:

```yaml
projection_id:
claim_strength: H1|H2|H3|H4|H5
transfer_status: LICENSED|CONDITIONAL|VETOED|UNKNOWN
max_licensed_strength:
```

Example:

```text
projection: escalation mechanism X is relevant
max licensed strength: H2

model output: 75% escalation + recommend mobilization
error type: CLAIM-STRENGTH OVERREACH
```

---

## 7. New metrics

### Maximum Licensed Claim Strength accuracy

Can the model identify the strongest conclusion justified by the precedent/evidence?

### Overreach rate

How often does it move from qualitative support to quantitative/action certainty without enough evidence?

### Underuse rate

How often does excessive caution cause it to discard a precedent that is useful at H1/H2?

### Claim-strength calibration

Does numerical confidence fall appropriately as the requested claim becomes stronger than the evidence allows?

---

## 8. Interaction with persuasion risk

Historical analogies can increase perceived confidence even when their quantitative evidential force is weak.

This makes claim-strength labeling important for user-facing systems.

Instead of:

> “The historical analogy suggests escalation.”

output:

```text
Historical relevance: high
Evidence that the same mechanism is active: moderate
Quantitative forecast contribution: weak
Action implication: not established by the analogy alone
```

This prevents rhetorical vividness from masquerading as probability.

---

## 9. Interaction with process phase

Claim strength is also phase-dependent.

A precedent may strongly support a mechanism warning before a critical juncture but lose directional/quantitative force across the transition.

Therefore:

```text
(source, source_phase, target_phase, projection, claim_strength)
```

is a more precise transfer object than:

```text
source event → target event.
```

---

## 10. Training signal

Resolved forecasting datasets can mine claim-strength overreach cases:

```text
rationale correctly identifies a relevant mechanism
→ model assigns extreme numerical probability
→ outcome resolves against prediction
```

Training should not teach `the mechanism was useless`.

Instead teach:

```text
mechanism relevance retained
quantitative permission reduced
```

This is exactly the sort of partial applicability memory the broader project needs.

---

## Bottom line

A historical precedent can be **epistemically valuable without being quantitatively transportable**.

The controller should therefore answer:

> **What is the strongest historical lesson this source actually licenses — a research lead, a mechanism claim, a directional forecast, a numerical probability, or an action recommendation?**

That is a more disciplined use of history than either rejecting analogies wholesale or letting a vivid precedent silently escalate into policy certainty.
