# Purpose-Relative Adequacy — An Analogy Is Not Good or Bad in the Abstract

**Snapshot: 21 August 2026.**

Scientific-model evaluation provides a direct formal lesson for analogical reasoning:

> **A source/model can be adequate for one purpose, respect and context while inadequate for another.**

The unit of evaluation is therefore not the source–target pair alone.

---

## 1. Parker — adequacy-for-purpose

**Wendy S. Parker, “Model Evaluation: An Adequacy-for-Purpose View,” _Philosophy of Science_ 87/88 era, published online 2022.**

Parker argues that model quality should ultimately be assessed relative to a **purpose** rather than through generic confirmation of the whole model.

A model is adequate when it can reliably accomplish a particular goal under the relevant conditions of use.

The relation is not merely:

```text
model M ↔ target T
```

but involves:

```text
model M
+ target T
+ user U
+ methodology W
+ background circumstances B
+ purpose P
```

A model can fail because of any part of this problem space.

### Warning against model-wide confirmation

Parker explicitly notes a danger: if one model result fits observations, users may say that “the model is confirmed” and then trust **other outputs** for which the model's idealizations are not adequate.

This is exactly the whole-source transfer error in analogy.

---

## 2. Díez 2026 — the hidden grammar is explicitly multi-parameter

**José Díez, “Representational modelling as ensemble-plus-standing-for. A (weakly) pragmatist account,” _European Journal for Philosophy of Science_ 16, article 62, published 14 August 2026.**  
DOI: https://doi.org/10.1007/s13194-026-00759-4

Díez argues that the simplified form

```text
M represents T
```

hides a richer grammar. His analysis includes:

- `S`: subject/agent;
- `M`: model;
- `T`: target;
- `R`: respects/features relevant to representation;
- `P`: purposes;
- `C`: context of use.

A rough form is:

```text
S uses M, in respects R,
to represent T,
for purposes P,
in context C.
```

Adequacy can vary with the respects, purpose and contextual accuracy requirements.

---

## 3. Direct analogy translation

Replace:

```text
analogy_score(source,target)
```

with something closer to:

```text
transfer_adequacy(
  source,
  target,
  mapped_respect,
  projected_claim,
  purpose,
  context
)
```

or a structured state:

```yaml
source:
target:
agent/controller:
relevant_respects:
projection:
purpose:
context:
required_accuracy:
transfer_status:
```

The same source–target pair can then receive different transfer states for different projections.

---

## 4. Example: one source, several purposes

Suppose source `S` shares a mechanistic pattern with target `T`.

### Purpose P1 — hypothesis generation

```text
Can S suggest a mechanism worth testing in T?
```

Adequacy threshold: relatively low.

Result:

```text
ADEQUATE FOR PURSUIT
```

### Purpose P2 — qualitative explanation

```text
Does S support the claim that mechanism X is actually active in T?
```

Requires target-side fingerprint evidence.

Result:

```text
CONDITIONAL
```

### Purpose P3 — quantitative prediction

```text
Can S support probability 0.70 for outcome Y?
```

Requires quantitative transport/reference-class calibration.

Result:

```text
INADEQUATE / UNKNOWN
```

### Purpose P4 — action

```text
Should intervention A be deployed?
```

Requires probability + stakes + alternatives.

Result:

```text
NOT LICENSED BY ANALOGY ALONE
```

Nothing contradictory occurs. The analogy is adequate for one purpose and inadequate for another.

---

## 5. Relevant respects are projection-specific

Díez's `R` parameter is especially useful.

Two systems can resemble each other in many respects, but the controller should ask:

```text
which respects matter for this projection?
```

Example:

```text
source and target share institutional hierarchy
source and target differ in technology
```

For projection `p1` about command latency, hierarchy may be relevant.

For projection `p2` about information diffusion, the technological difference may dominate.

Thus:

```text
same S,T
p1: LICENSED
p2: VETOED
```

This is claim-level analogy in an explicit pragmatic grammar.

---

## 6. Context controls the accuracy threshold

Díez emphasizes that adequacy comes in degrees and depends on context.

For exploratory brainstorming:

```text
rough analogy acceptable
```

For drug dosing / policy action / high-stakes military forecast:

```text
much stronger transfer accuracy required
```

The controller therefore needs:

```yaml
context:
stakes:
required_calibration:
acceptable_error:
```

This connects model adequacy directly to Fuller's practical problem of extrapolation.

---

## 7. Representation performance vs adequacy

Díez also distinguishes **successfully performing a representation** from the representation being **adequate/correct**.

Analogical translation:

```text
model successfully constructs a coherent source→target mapping
≠
mapping is adequate for the target projection.
```

A system may successfully perform analogy as a cognitive/inferential act while producing a bad world-level inference.

This is exactly why mechanistic hidden-state evidence of mapping should not be treated as final epistemic success.

---

## 8. Benchmark design

For the same source-target pair, vary only:

### Purpose

```text
hypothesis generation
mechanism identification
qualitative prediction
quantitative forecast
action recommendation
```

### Relevant respect

Ask different projected properties that depend on different source–target correspondences.

### Context/stakes

Vary required confidence and cost of error.

Desired behavior:

```text
transfer permission changes appropriately
without changing the underlying source/target description unnecessarily.
```

Metrics:

- purpose-sensitive transfer accuracy;
- respect-selection accuracy;
- false model-wide confirmation rate;
- context-sensitive abstention/calibration;
- cross-purpose trust leakage.

---

## 9. Training implication

Training examples should reuse the same source–target pair under multiple questions:

```text
S,T,purpose=P1 → transfer
S,T,purpose=P2 → conditional
S,T,purpose=P3 → veto/unknown
```

This prevents the model from learning a scalar source-pair utility.

Reward should attach to:

```text
(source,target,respect,projection,purpose,context)
```

rather than:

```text
(source,target).
```

---

## 10. Relation to localism

Purpose-relative adequacy gives a more precise engineering form to localism.

The system can share a common controller grammar across domains:

```text
source / target / respects / purpose / context / projection
```

while each domain supplies different standards for:

- relevant respects;
- acceptable error;
- decisive evidence;
- validation procedure.

Thus one can have architectural universality without epistemic one-size-fits-all.

---

## Bottom line

The right question for analogical AI is not:

> **Is S a good analogy for T?**

It is:

> **For this target projection, in these respects, for this purpose and under this context's accuracy/stakes requirements, is S an adequate surrogate/source?**

That multi-parameter grammar is one of the cleanest direct translations from contemporary philosophy of scientific modelling into an analogical control architecture.
