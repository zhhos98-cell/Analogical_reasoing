# Discovery, Pursuit and Confirmation — Analogy Can Be Useful Before It Is Trustworthy

**Snapshot: 21 August 2026.**

Scientific analogies perform different epistemic jobs. One of the most important distinctions for AI is between:

```text
analogy as a reason to generate / explore / pursue a hypothesis
```

and

```text
analogy as evidence that the hypothesis is likely true or transferable.
```

These must not be collapsed.

---

## 1. Pursuit-worthiness is not confirmation

Rune Nyrup's analysis of the liquid-drop model highlights a scientific use of analogy that is neither mere inspiration nor straightforward confirmation.

**Rune Nyrup, “Of Water Drops and Atomic Nuclei: Analogies and Pursuit Worthiness in Science,” BJPS 71(3), 2020.**  
DOI: https://doi.org/10.1093/bjps/axy036

The analogy supported pursuit because it enabled transfer of a well-understood **modelling strategy** to the nuclear domain.

That is a different epistemic function from claiming:

```text
the atomic nucleus is sufficiently like a liquid drop
→ therefore property p is probably true.
```

### AI translation

A retrieved source can justify:

```text
PURSUE hypothesis h
RUN experiment e
CONSTRUCT representation R
TRY operator f
```

without justifying:

```text
BELIEVE h
PROJECT p
ACT on p with high confidence.
```

---

## 2. A permission ladder

Analogical systems should expose different levels of epistemic permission.

Proposed control states:

```text
GENERATE
  source makes hypothesis worth formulating

PURSUE
  source makes hypothesis worth spending compute/data/experiment budget on

PLAUSIBLE
  source supplies some epistemic reason for serious consideration

CONDITIONALLY PROJECT
  source supports a target inference under explicit bridge assumptions

CONFIRM
  source plus independent/target evidence increases confidence in p

ACT
  posterior + stakes/cost threshold justify decision
```

A single `analogy confidence` score obscures these transitions.

---

## 3. Why this matters for scientific-discovery agents

AI-for-science systems often optimize for novelty or candidate generation. In that setting, analogy can be extremely valuable even when transfer reliability is low.

A creative source may:

- suggest a new variable;
- suggest an experiment;
- import a modelling method;
- reveal a new mechanism hypothesis;
- propose a mathematical form;
- generate a synthetic design.

The right action is often:

```text
explore further
```

not:

```text
increase target belief directly.
```

This distinction gives a principled way to tolerate speculative analogy in discovery without contaminating downstream evidence calibration.

---

## 4. Architecture implication: separate proposal and commitment policies

A scientific analogue controller can use two policies:

```text
proposal policy π_gen:
  maximize useful hypothesis diversity / expected information gain

commitment policy π_ep:
  license belief/projection only after relevance, comparability and validation checks
```

This is analogous to search versus verification in other AI systems.

The proposal policy may favor far analogies and conceptual novelty.

The commitment policy should be conservative about:

- source–target bridge assumptions;
- critical disanalogies;
- external validity;
- target-side evidence;
- robustness/dependence;
- calibration.

---

## 5. Benchmark design

Do not score all analogies by whether their target conclusion is true.

Include separate tasks:

### Discovery track

Given an underspecified scientific problem:

- generate useful source domains;
- produce novel hypotheses;
- suggest experiments/representations;
- score later information gain / expert-rated pursuit value.

### Transfer track

Given a candidate source-derived claim:

- identify bridge assumptions;
- license/condition/veto projection;
- provide calibrated probability;
- specify validation evidence.

### Decision track

Given stakes/costs:

- decide whether to act, experiment, wait or abstain.

A model can be strong on discovery and weak on transfer without contradiction.

---

## 6. Training implication

Reward should be stage-specific.

Possible discovery rewards:

```text
R_novelty
R_information_gain
R_experiment_value
R_representation_gain
R_solution_diversity
```

Possible transfer rewards:

```text
R_projection_accuracy
R_calibration
R_boundary_response
R_evidence_grounding
R_abstention
```

The system should not receive the same confidence reward merely because an analogy was generatively productive.

---

## 7. Relation to current AI-for-science analogy work

Recent analogical scientific-discovery systems demonstrate that guided or retrieved analogies can significantly improve solution search and cross-domain activation.

The pursuit/confirmation distinction gives a cleaner interpretation of such results:

> **successful analogy-assisted discovery establishes the value of analogy as a search operator before it establishes analogy as an autonomous confirmation mechanism.**

This prevents overclaiming from creativity results.

---

## 8. Relation to historical analogy

The same distinction matters in policy/foresight.

A historical precedent can be useful because it tells an analyst:

```text
check mechanism X
look for actor Y
consider scenario Z
```

without licensing:

```text
scenario Z is now 70% likely.
```

This gives historical analogy a safe exploratory mode:

```text
precedent as research agenda
```

rather than immediately:

```text
precedent as forecast evidence.
```

---

## Bottom line

A mature analogical intelligence system must answer two different questions:

> **Is this analogy worth pursuing?**

and

> **How much should this analogy change belief or action?**

Science often benefits enormously from analogies that score high on the first and low or uncertain on the second. AI should represent that distinction explicitly.
