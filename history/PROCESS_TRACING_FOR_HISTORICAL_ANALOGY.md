# Process Tracing for Historical Analogy — Mechanism × Phase, Not Static Event Similarity

**Snapshot: 21 August 2026.**

Historical analogy is often represented as a comparison between two event structures:

```text
source event graph
↔
target event graph
```

Comparative-historical process tracing suggests that this is incomplete. For many political/social historical analogies, **sequence, phase and critical juncture are part of the mechanism**.

A better object is:

```text
mechanism × temporal phase × path-dependent state
```

---

## 1. Comparative process tracing in historical social science

Bo Bengtsson and Hannu Ruonavaara develop comparative process tracing as a method combining:

- theoretical social mechanisms;
- chronology;
- path dependence;
- critical junctures / focal points;
- ideal-type periodization;
- contextual comparison;
- counterfactual analysis.

The method reconstructs each case as a process from `A → B`, then compares the mechanisms and periods rather than treating each case as an unordered feature bundle.

Core methodological paper:

**Bengtsson & Ruonavaara, “Comparative Process Tracing: Making Historical Comparison Structured and Focused,” Philosophy of the Social Sciences 47(1), 2017.**  
DOI: https://doi.org/10.1177/0048393116658549

The approach remains active; e.g. 2026 comparative-process-tracing work on Indonesian healthcare and pension reform reconstructs divergent trajectories under a shared institutional setting.

---

## 2. Why static analogy can fail

Two events can share actors, institutions and causal relations while occupying different **process phases**.

Example abstractly:

```text
Source:
A → repeated B → repeated B → terminal package C → pause

Target/current observation:
A' → repeated B' → repeated B' → C'
```

A static feature matcher may see:

```text
A≈A', B≈B', C≈C'
```

and project another `B'`.

A phase-sensitive representation recognizes:

```text
C = terminal transition
```

so the correct source lesson is **cessation**, not recurrence.

---

## 3. BTF pattern-break cases are phase failures

The resolved FutureSearch/BTF failures already fit this representation.

### EU Iran sanctions

Failure type:

```text
recurrence pattern
→ terminal externally driven deadline package
→ generating process exhausted
```

The analogy failed because the target had crossed into a new phase.

### Argentine peso

Failure type:

```text
pre-election panic trajectory
→ scheduled election
→ information/regime reset
```

Projecting the pre-election trend across the juncture was invalid.

### NYC turnout

Failure type:

```text
historical turnout ceiling under low-competition structure
→ changed competition/mobilization structure
→ old reference class no longer stable
```

Again, the history was real; the phase/structure producing it had changed.

---

## 4. Represent history as trajectories with state transitions

Instead of one event graph:

```yaml
actors:
mechanisms:
relations:
```

use a staged representation:

```yaml
phases:
  - phase_id: P1
    state:
    active_mechanisms:
    enabling_conditions:
    observed_markers:
    transition_conditions:

  - phase_id: P2
    ...

critical_junctures:
  - trigger:
    before_state:
    after_state:
    mechanism_changes:
```

Analogy becomes alignment over **process states** rather than only roles.

---

## 5. Historical source selection should be phase-aware

A source may be useful only at a particular stage.

```text
S at phase 2 may match T now
S at phase 4 may be the relevant forward lesson
```

Therefore retrieval should index:

```text
(source event, source phase)
```

not merely:

```text
source event.
```

This could improve both source precision and projection validity.

---

## 6. Critical-juncture detection as transfer veto

For each projected historical lesson, ask:

```text
Is the target about to cross / has it already crossed a transition
that was absent at the corresponding source phase?
```

Candidate junctures:

- elections;
- deadlines/sunsets;
- regime change;
- institutional reform;
- war entry/exit;
- technological adoption threshold;
- actor replacement;
- liquidity/financial constraint;
- exhaustion of a policy instrument;
- demographic/mobilization change.

If yes, pre-juncture source dynamics should not be automatically projected across the boundary.

---

## 7. Counterfactual comparison

Historical CPT also encourages counterfactual reasoning.

For analogy control, use:

```text
If the target did NOT have difference/juncture X,
would the source trajectory still be expected?
```

This provides a more diagnostic question than:

```text
How similar are the cases?
```

A candidate boundary is useful when manipulating it changes the projected trajectory.

ForecastBench-Sim or other simulated worlds can test this directly before real-history deployment.

---

## 8. Mechanism × phase transfer contract

Proposed output:

```yaml
source_event:
source_phase:
target_phase_estimate:
phase_alignment_confidence:
shared_mechanism:
critical_junctures_between_now_and_projection:

projection:
  statement:
  source_supporting_phase:
  status: LICENSED | CONDITIONAL | VETOED | UNKNOWN
  phase_condition:
  transition_risk:
  evidence_to_monitor:
```

Example:

```text
Projection: another sanctions amendment in Q4
Source support: repeated amendment cadence
Current phase: post-terminal-package
Status: VETOED / strongly downweighted
Reason: cadence-generating deadline process completed
```

---

## 9. Benchmark metrics

Add:

- phase-alignment accuracy;
- critical-juncture recall/precision;
- probability response across a juncture;
- pre/post-juncture source-rank reversal;
- phase-specific transfer macro-F1;
- false continuation rate;
- false regime-change rate.

A particularly useful paired test:

```text
T_before_juncture
T_after_juncture
```

with identical background facts except the transition evidence.

---

## 10. Relation to CANA

CANA is already much richer than superficial event matching: it decomposes mechanisms, retrieves structural analogies and records limitations.

The process-tracing extension is not a replacement. It asks whether the same machinery should represent:

```text
structural role
+
location in historical trajectory
+
transition conditions.
```

This may be especially important for forward events because a mechanism can remain active while the **phase governing its effect changes**.

---

## Bottom line

A high-quality historical analogy should not say only:

> **This event has the same mechanism as that event.**

It should also say:

> **The target currently occupies the source's phase P2, but a critical juncture J is imminent; the source projection p was generated only before/after J, so transfer is conditional on whether the target crosses the same transition.**

That is much closer to historical reasoning than static similarity or a timeless event DAG.
