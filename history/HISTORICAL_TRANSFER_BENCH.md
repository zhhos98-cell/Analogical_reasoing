# Historical Transfer Bench — A Benchmark Specification for Selective Historical Analogy

**Status: design specification, not yet a released dataset.**  
**Snapshot: 21 August 2026.**

The current public benchmark landscape leaves a clean middle layer under-tested.

- **Past Meets Present** evaluates whether a model can acquire/generate a plausible historical analogue for a target event.
- **ARN** shows that narrative analogy benchmarks can deliberately contrast near/far analogies with disanalogies.
- **ADR-bench / CANA** evaluates mechanism-oriented historical analogue retrieval and downstream foresight, including per-analogy limitations, difference awareness, analogy differentiation and temporal-compliance scoring.

What is still missing is a controlled benchmark whose primary object is:

> **Given one or more plausible historical precedents, which specific source-derived claims are licensed in the target, which become conditional after contextual rebinding, which are blocked by a disanalogy, and which remain unresolved?**

The proposed benchmark is therefore not another `find a historical analogy` dataset. It tests **selective historical transfer**.

---

# 1. Core task

For target situation `T` at historical information cutoff `t0`, the system receives or retrieves candidate source precedents `S1...Sk` and produces a structured transfer assessment.

Minimum output for each source:

```text
source: S_i
source representation: R_S
target representation: R_T
mapped relations / roles: ...
critical disanalogies: ...

candidate projections:
  p1: LICENSED
  p2: CONDITIONAL — requires rebinding/condition C
  p3: VETOED — difference d breaks mechanism r
  p4: UNKNOWN — insufficient target evidence

required evidence / verification: ...
source dependence with other precedents: ...
temporal-cutoff compliance: ...
confidence / probability: ...
```

The benchmark should score each stage separately rather than collapsing everything into final forecast accuracy.

---

# 2. Why this is distinct from existing benchmarks

## Past Meets Present

Primary object:

`target → historical source acquisition`.

It demonstrates that candidate precedent generation is feasible. Its general-analogy evaluation uses multidimensional similarity; it does not make downstream historical lesson validity the central label.

## ARN

Primary object:

`narrative pair → analogy / disanalogy classification`, including near/far conditions.

ARN proves that controlled disanalogy construction is practical. But it does not model historical source provenance, time cutoffs, contested event mechanisms, multi-precedent dependence, or projection-by-projection transfer.

## ADR-bench

Primary object:

`pre-cutoff target → historical analogies → mechanism integration → foresight report`.

ADR-bench is much closer. It already includes explicit difference-awareness and temporal-compliance rubrics. The proposed benchmark drills into the remaining control transition:

`identified limitation/disanalogy → exactly which projected claim loses or retains license?`

This benchmark should therefore be treated as **complementary to ADR-bench**, not a replacement.

---

# 3. Case construction

Each benchmark target should include a controlled **precedent set** rather than one gold source.

## Source class A — useful structural precedent

A past event shares one or more target-relevant mechanisms/roles and supports at least one valid projection.

## Source class B — surface-near / mechanism-wrong hard negative

Shares actors, geography, vocabulary, chronology, institutional type, or headline similarity while the inference-critical mechanism differs.

Purpose: test whether semantic familiarity outruns structural validity.

## Source class C — mechanism-near with one critical disanalogy

Most of the structural mapping is valid, but one target condition changes the applicability of a specific projected lesson.

This is the benchmark's most important source type.

Example abstract shape:

```text
S: A → B → C → outcome O
T: A' → B' → C' ...

A~A', B~B', C~C'
BUT target condition X changes C'→O mechanism

p1 derived from A/B: LICENSED
p2 derived from C→O: VETOED
```

## Source class D — sibling / common-cause precedent

Looks like an additional confirmation but belongs to the same institutional series, diffusion chain, technological lineage, common shock, or nested event family as another source.

Purpose: test **effective independent support**, not raw precedent count.

## Source class E — conflicting precedent

Shares an apparently relevant mechanism but historically produced a different outcome under another condition.

Purpose: force the system to expose competing historical trajectories rather than synthesizing a single smooth narrative.

## Source class F — irrelevant but rhetorically seductive precedent

A culturally famous analogy with strong narrative resonance but weak inferential utility.

Purpose: test susceptibility to canonical/vivid history.

---

# 4. Target classes

## T1 — one valid precedent, several decoys

Baseline retrieval + adjudication.

## T2 — partial-transfer target

At least one source is genuinely useful but only some candidate projections survive target-side differences.

## T3 — multiple complementary precedents

No source covers the target alone; different sources support different positions. Tests CANA-style distributed evidence.

## T4 — correlated multi-precedent target

Several apparent confirmations belong to one dependence cluster.

## T5 — conflicting-precedent target

Several mechanism-plausible sources imply different target trajectories.

## T6 — no sufficiently useful historical precedent

The correct system action is **NO VALID / SUFFICIENTLY LICENSED ANALOGY**, possibly followed by evidence acquisition rather than forced analogy generation.

This is important because candidate-generation systems are otherwise rewarded for always producing a historical story.

## T7 — representation-ambiguous target

Two or more defensible causal/structural decompositions imply different source rankings.

Purpose: test whether the model treats its own representation as uncertain rather than as the target itself.

---

# 5. Projection labels

Each candidate source should be paired with explicit potential projections rather than one source-level gold label.

Four core labels:

### LICENSED

The source relation/mechanism is sufficiently preserved to support the target claim under the benchmark's evidence standard.

### CONDITIONAL

The source supports the claim only after an explicit contextual rebinding or if condition `C` holds.

The system must state the condition.

### VETOED

A known source–target difference blocks the projected inference.

The system must identify the difference and the affected mechanism/role.

### UNKNOWN / NEED EVIDENCE

Current target evidence does not determine whether the relevant source relation is transferable.

The system should state what evidence would discriminate the alternatives.

These labels should be independently annotated before model evaluation.

---

# 6. Annotation structure

A benchmark item should contain more than prose gold answers.

Suggested schema:

```yaml
item_id:
target_id:
target_cutoff:
target_brief_vintage:
target_outcome_hidden_until_eval:

candidate_target_representations:
  - id:
    mechanism_graph_or_structured_roles:
    historiographic_source:
    confidence:

sources:
  - source_id:
    source_date:
    source_representation:
    provenance:
    source_class: A|B|C|D|E|F
    dependence_cluster:
    mapped_roles:
    critical_disanalogies:
    projections:
      - projection_id:
        statement:
        label: LICENSED|CONDITIONAL|VETOED|UNKNOWN
        condition_if_any:
        blocking_difference_if_any:
        evidence_required_if_unknown:
        gold_rationale:

counter_precedents:
source_dependence_graph:
```

The benchmark should preserve annotator disagreement where historians/experts disagree on mechanism structure rather than forcing one false oracle.

---

# 7. Representation plurality

Historical mechanisms are contestable. For a subset of benchmark items, provide at least two defensible target/source decompositions derived from distinct expert or historiographic interpretations.

Evaluation should ask:

1. Does the system recognize that source ranking is representation-dependent?
2. Can it report different transfer assessments under competing mechanism hypotheses?
3. Does later evidence rationally reweight those representations?
4. Does the system collapse one generated causal graph into an unquestioned fact?

A useful output is:

```text
Under representation R1, S1 is strongest and p2 is licensed.
Under representation R2, S3 is strongest and p2 is vetoed.
Current evidence weakly favors R1 (0.62).
Evidence E would discriminate R1/R2.
```

This is much closer to real historical/strategic comparison than one oracle event graph.

---

# 8. Temporal-control arms

Every foresight item should have a strict historical cutoff. A serious benchmark should distinguish three validation tiers.

## Arm A — normal modern model with cutoff prompt

Tests cheap practical deployment.

## Arm B — black-box hindsight audit

Adapt HindsightBench-style manipulations:

- actual date shown;
- date masked;
- date transplanted to another period;
- outcome-memory probe.

Measure changes not only in final predictions but also in:

- source retrieval;
- source ranking;
- mechanism mapping;
- disanalogy selection;
- transfer labels;
- confidence.

## Arm C — hard time-locked / vintage-consistent baseline

For targets near available historical cutoffs, use models such as Ranke-style time-locked checkpoints or other future-information-isolated systems to estimate how much modern-model performance depends on hindsight.

Where numerical historical data are used, preserve vintage values rather than later revisions.

---

# 9. Dependence controls

Each multi-precedent target should include a **source–source dependence graph**.

Possible edge types:

- same institutional series;
- direct imitation / policy diffusion;
- technological ancestry;
- common exogenous shock;
- nested/part-whole event relation;
- common dataset/source provenance;
- shared historiographic genealogy;
- retrieval-cluster dependence.

Metrics should distinguish:

`raw confirming precedent count`

from

`dependence-adjusted effective support`.

A system that retrieves three cases from one historical lineage should not receive the same multi-source score as a system finding genuinely independent confirmations.

---

# 10. Core metrics

## M1 — source retrieval recall

Did the model find useful sources?

## M2 — source precision / seductive-precedent rejection

How many retrieved sources were actually useful?

## M3 — mechanism/role alignment accuracy

Were the inference-relevant correspondences identified?

## M4 — critical-disanalogy localization

Did the model identify the difference that changes transfer validity?

## M5 — projection transfer macro-F1

Four-way classification over:

`LICENSED / CONDITIONAL / VETOED / UNKNOWN`.

This should be the benchmark's headline metric.

## M6 — condition/rationale accuracy

For CONDITIONAL/VETOED labels, did the model name the correct controlling condition or blocking difference?

## M7 — calibration

Brier score / ECE or other proper scoring rule over projection validity.

## M8 — no-analogy selective accuracy

Can the system abstain when no sufficiently useful precedent exists without collapsing source recall?

## M9 — hindsight sensitivity

Change in source choice/mapping/transfer labels under date mask/transplant.

## M10 — dependence awareness

Does the model discount correlated precedents and identify dependence reasons?

## M11 — competing-representation calibration

Does the model preserve plausible alternative mechanism decompositions and update them rationally?

## M12 — counter-analogy coverage

Can it retrieve/source cases that challenge the favored precedent rather than only confirming it?

---

# 11. Longitudinal phase — negative applicability memory

A static benchmark is insufficient for the broader analogical-control frontier.

Create sequences of related targets:

### Episode 1

Source `S` supports `p1` but a condition `X` makes `p2` fail.

The system receives verification/failure evidence.

### Episode 2

A new target again resembles `S`; condition `X` is present.

Desired behavior:

- keep `S` useful for `p1`;
- down-weight/veto `p2`;
- retrieve an alternative source for the blocked mechanism.

### Episode 3

A third target resembles `S`, but `X` is absent.

Desired behavior:

- restore `p2` eligibility;
- avoid **over-blacklisting** the source after one failed transfer.

This directly tests whether memory stores an applicability **boundary** rather than a binary `good source / bad source` judgment.

Metrics:

- boundary retention;
- false blacklisting rate;
- repeat invalid-transfer rate;
- source-specific vs projection-specific memory;
- transfer-calibration improvement over episodes.

---

# 12. Human comparison

A serious benchmark should not simply label model performance with one expert gold answer.

At least three human conditions are useful:

1. **unstructured experts** — ordinary historical/strategic comparison;
2. **structured-analogy experts** — explicitly list multiple sources, similarities and differences;
3. **AI-assisted experts** — inspect machine precedent sets and transfer contracts.

This can reveal whether the useful human–machine division of labor is:

`machine source recall + human adjudication`,

or whether a trained controller can eventually improve precision without sacrificing search breadth.

---

# 13. Persuasion sub-study

Because historical analogy can increase perceived confidence in leaders' decisions, benchmark quality should eventually be separated from rhetorical effect.

A preregistered human study could randomize:

- recommendation only;
- recommendation + valid analogy;
- recommendation + seductive transfer-invalid analogy;
- recommendation + analogy with explicit limitations;
- recommendation + competing precedents;
- recommendation + calibrated no-analogy result.

Measure:

- decision confidence;
- willingness to act;
- structural understanding;
- recall of limitations;
- calibration to actual decision quality.

The key question is whether **analogy persuasiveness can exceed analogy validity**.

---

# 14. Minimal viable benchmark

A first release need not be huge. A high-quality MVP could contain:

- **40 target situations**;
- 6–10 curated candidate precedents per target;
- ~4 candidate projections per useful source;
- at least 10 no-valid-precedent targets;
- at least 10 correlated-precedent targets;
- at least 10 representation-ambiguous targets;
- 2 temporal-control arms for all cases;
- hard time-locked evaluation for a smaller historical subset;
- 3 related-target sequences for longitudinal applicability memory.

This would already test dimensions absent from simple historical-analogue acquisition while remaining small enough for expert annotation and source auditing.

---

# 15. Falsification criterion for the claimed gap

The current branch labels projection-level historical transfer control as a **high-confidence open frontier based on the public literature sweep, not a proof of absence**.

That claim should be weakened or retired if an existing or new system demonstrates, on open historical events:

- endogenous/source-target event representation;
- hard-negative and no-valid-precedent handling;
- explicit mapping of disanalogy to the affected projected claim;
- partial transfer rather than whole-source acceptance/rejection;
- calibrated projection uncertainty;
- dependence-aware multi-precedent integration;
- source/mapping-level hindsight controls;
- failure-driven update of applicability boundaries.

The benchmark is designed so the field can falsify the gap rather than merely discuss it.
