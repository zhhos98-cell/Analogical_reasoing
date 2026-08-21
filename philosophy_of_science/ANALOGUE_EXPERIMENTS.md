# Analogue Experiments — From Plausibility to External Validation

**Snapshot: 21 August 2026.**

Analogue experiments make source→target transfer unusually concrete. A manipulable source system is used to learn about a target system that is different, inaccessible or not directly manipulable under the relevant conditions.

The philosophical dispute is therefore close to an engineering question:

> **When does a successful source experiment merely make a target hypothesis plausible, and when has the source been externally validated enough to provide confirmation?**

## 1. Crowther 2026 — analogue experiment as an externally unvalidated source

**Karen Crowther, _Dumb holes: universality or analogy? What makes an analogue experiment an analogue experiment?_, Synthese 207:136 (2026).**  
DOI: https://doi.org/10.1007/s11229-026-05538-5

Crowther revisits the debate over laboratory `dumb holes` as analogues of black holes and the possibility of confirming Hawking radiation through analogue systems.

Her proposed distinction is especially useful:

```text
analogue experiment:
source is taken to be analogous to target,
but is not yet known to be the relevant same type of system
for the purpose of the inference.

conventional experiment:
source has been externally validated as probative of the target
for the purpose of the inference.
```

On this view, external validation can **upgrade** an analogue experiment.

## 2. Plausibility vs confirmation

The important boundary is not whether the source experiment works internally.

A laboratory source can exhibit the predicted phenomenon perfectly while still failing to establish that the target instantiates the relevant same structure/universality conditions.

This maps directly to AI:

```text
source solved correctly
+ mapping looks structurally coherent
≠
target projection externally validated.
```

## 3. Model-external arguments matter

The analogue-gravity debate emphasizes arguments about universality/robustness that are external to the immediate formal correspondence between source and target.

Engineering translation:

```text
mapping evidence
+
model-external evidence that the mapping is stable/relevant
→ stronger transfer license.
```

This helps sharpen the role of target-side evidence in an analogy controller.

## 4. An upgrade ladder for AI analogies

A useful control state could distinguish:

### Candidate analogy

```text
plausible source–target correspondence
```

### Evidentially constrained analogy

```text
correspondence + independent evidence for key bridge assumptions
```

### Validated transfer family

```text
correspondence repeatedly survives target-side tests / external validation
```

This is better than treating all analogies as equal once their structure-mapping score crosses a threshold.

## 5. Validation history can become memory

If a source family repeatedly passes/fails target-side validation for a particular projection type, the system can learn an applicability boundary.

For example:

```text
source family F
projection p
valid when universality condition U holds
invalid/uncertain when U is unsupported
```

This connects analogue experiments to continual boundary memory.

## 6. Important caution: validation is purpose-relative

Crowther's `same type of system` notion is explicitly tied to the **purpose of the investigation**.

Two systems need not be identical globally. They need to be externally validated as relevantly the same for the particular inference.

This supports projection-level transfer rather than whole-source acceptance:

```text
S may be validated for p1
but remain merely analogical for p2.
```

## 7. Benchmark implication

Scientific Analogy Bench should distinguish:

- internal source success;
- formal/structural correspondence;
- model-external support for the correspondence;
- target-side validation;
- projection-specific validation history.

A system that generates a brilliant source analogy but cannot identify what would externally validate it should not receive the same epistemic score as one that can.

## Bottom line

Analogue experiments provide a strong engineering metaphor with real epistemic content:

> **an analogy should be able to move through validation states.**

The goal is not just better mapping. It is a controller that knows when a source is still a plausibility device, when independent evidence strengthens the bridge, and when repeated external validation licenses stronger target claims.