# From Epistemic Norms to Rewards — What Can Actually Be Operationalized?

**Status: engineering hypothesis map, not an established training recipe.**  
**Snapshot: 21 August 2026.**

The philosophy-of-science branch is useful only if its distinctions can be tested against modern AI systems. This note separates constraints with existing engineering analogues from constraints that remain research hypotheses.

## 1. Already supported by neighboring AI work

### A. Reward reasoning utility rather than semantic similarity

RA-RFT (Xiao et al., 2026) trains a retriever from judge-distilled labels of **expected reasoning benefit**, then uses retrieved analogical traces during reinforcement fine-tuning under verifiable outcome rewards.

This is already an operational form of a philosophical relevance claim:

```text
retrieval relevance ≠ lexical/semantic proximity.
```

It does not yet evaluate projection-specific epistemic validity, but it shows that `usefulness for downstream reasoning` can be learned as a separate signal.

### B. Reward analogical transfer directly in controlled environments

Zhu et al. (2026) include **analogical transfer** as one of four explicitly rewarded reasoning families in an RLVR study over synthetic knowledge graphs.

This shows that analogy-specific post-training is technically feasible when the environment provides verifiable outcomes.

### C. Cross-analogue consistency can act as a self-supervised reward

Co-Reward (2025) constructs semantically analogous question pairs and rewards cross-question agreement in reasoning/outcomes. It reports gains over self-reward baselines.

This is evidence that cross-case invariance can be used as reward shaping, but it should not be confused with epistemic robustness: correlated/incorrect analogues can agree.

---

# 2. Philosophy-derived signals that look directly benchmarkable

These do not require access to hidden philosophical truth. They can be evaluated in controlled or resolved tasks.

## R_rel — projection relevance

Question:

```text
Does the mapped relation f actually help predict/project g?
```

Train on matched cases where:

- f is genuinely predictive of g;
- f is structurally shared but irrelevant to g;
- a different relation h is the true moderator.

Reward discrimination between mapping and relevance.

## R_boundary — critical-difference response

Measure probability movement when an inference-critical disanalogy is introduced:

```text
ΔP_boundary = P(p | mapping)
              - P(p | mapping + blocking condition)
```

Reward large appropriate changes and penalize sensitivity to irrelevant differences.

## R_unknown — calibrated abstention / evidence request

Give cases where transfer validity cannot be determined from current evidence.

Reward:

```text
UNKNOWN / NEED EVIDENCE
```

plus correct identification of the discriminating observation, rather than forced transfer.

## R_counter — counter-analogue search

Reward retrieval of sources that would falsify or qualify the favored projection, not only sources that agree.

This can be evaluated whenever a benchmark supplies outcome-divergent, mechanism-near sources.

## R_revision — useful rerepresentation

After an initial failure, allow representation revision and reward only revisions that improve held-out related cases.

Penalize bespoke rewrites that repair one example but do not generalize.

---

# 3. Signals that require explicit evidence structure

## R_evid — comparability-evidence quality

Fuller's logical/evidential distinction suggests scoring separately:

```text
A. the transfer argument would be valid if comparability assumption C were true;
B. the system has independent evidence that C is true.
```

A controlled benchmark can provide evidence snippets with provenance and label which assumptions they support/refute.

The model should not receive full reward for inventing a convenient comparability premise.

## R_bridge — bridge-hypothesis support

Using Nappo-style structure:

```text
observed similarities/differences
→ bridge hypothesis B
→ target hypothesis H.
```

Score whether evidence supports B and whether B is actually relevant to H.

This localizes failures better than one end-to-end answer reward.

## R_falsifier — target-side test quality

Reward a system for identifying observations/interventions that would discriminate:

```text
transfer valid
vs
transfer invalid / competing mechanism.
```

In simulations this can be verified directly. In real science/history it may require expert annotation or future resolution.

---

# 4. Robustness rewards need special care

A naive reward such as:

```text
more agreeing analogues = higher reward
```

is epistemically unsafe.

The robustness literature suggests rewarding **informative variation** instead:

```text
R_rob = agreement after varying relevant auxiliaries
        + identification of shared core
        + counter-source coverage
        - redundancy/dependence
```

Lehtinen (2026) makes this more precise through Derivational Confirmation and Disconfirmation Rules: learning that a result survives without an auxiliary can increase confidence that the result depends on the core rather than that auxiliary. But derivational robustness alone does not automatically produce empirical confirmation; an empirical/indirect confirmation link is still needed.

For AI this means a robustness reward should ask:

```text
what was varied?
what remained invariant?
which component was shown dispensable?
what empirical/target evidence links the invariant core to reality?
```

---

# 5. Candidate composite objective

A research prototype could begin with:

```text
R_total =
    R_outcome
  + λ1 R_rel
  + λ2 R_boundary
  + λ3 R_evid
  + λ4 R_calibration
  + λ5 R_counter
  + λ6 R_revision
  + λ7 R_falsifier
  + λ8 R_rob
  - λ9 R_circularity
  - λ10 R_redundancy
  - λ11 R_ad_hoc_revision
```

This is **not** proposed as the correct final reward function. Its value is experimental decomposition: ablate each signal and measure whether it improves far transfer, selective rejection, calibration and out-of-domain performance.

---

# 6. Circularity penalty

Extrapolation can become circular when the system supports target comparability using the same conclusion it is trying to project.

Synthetic tasks can explicitly contain:

```text
independent bridge evidence
vs
conclusion-derived pseudo-evidence.
```

Reward models for preferring independent support.

In real tasks, provenance/evidence graphs can help detect whether a stated warrant is merely downstream of the target claim.

---

# 7. Validation-state reward

Analogue-experiment philosophy suggests a source can move through stages:

```text
CANDIDATE
→ PLAUSIBILITY_SUPPORTED
→ BRIDGE_EVIDENCE_SUPPORTED
→ TARGET_VALIDATED
```

Reward the model for assigning the strongest claim only when the required evidence state is met.

This is a form of epistemic calibration at the **status level**, not only probability calibration.

---

# 8. Shared controller, local reward predicates

Localism suggests that the output grammar can be universal while evidence predicates are domain-specific.

Shared state:

```text
LICENSED / CONDITIONAL / VETOED / UNKNOWN
bridge
blocking difference
uncertainty
falsifier
validation state
```

Domain-local reward predicates:

```text
physics: universality / equation / perturbation evidence
biomedicine: mechanism/cofactor/intervention evidence
history: institutional/temporal/provenance evidence
climate: physical + socioeconomic comparability
```

The experiment is whether a shared controller can learn to invoke different warrant modules rather than one universal similarity threshold.

---

# 9. Falsification criterion for the PoS→AI program

This entire translation should be regarded as unhelpful if adding these epistemic-control signals does not improve at least one of:

- out-of-distribution analogical transfer;
- hard-negative rejection;
- projection-level calibration;
- no-valid-analogy abstention;
- robustness under representation/metric changes;
- recovery from boundary-condition failures;
- target-side prediction or experimental efficiency.

If ordinary outcome-only RL learns the same behavior more efficiently, the philosophical decomposition has explanatory interest but little engineering value.

## Bottom line

There is already evidence that analogy-aware retrieval and analogical transfer can be trained with modern post-training methods. The open experiment is narrower:

> **Do relevance, evidential support, boundary sensitivity, robustness and validation-state signals add measurable transfer control beyond end-to-end answer rewards?**

That is a falsifiable way to make contemporary philosophy of science interact with frontier analogical-reasoning engineering.