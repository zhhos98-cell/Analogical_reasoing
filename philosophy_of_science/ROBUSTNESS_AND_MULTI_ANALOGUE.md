# Robustness and Multiple Analogues — Agreement Is Not Automatically Independent Evidence

**Snapshot: 21 August 2026.**

Multi-source analogical systems often rely on a plausible intuition:

```text
if several different sources support the same target claim,
confidence should increase.
```

The philosophy-of-science literature on robustness shows why this inference needs conditions.

## 1. Derivational robustness

A result is derivationally robust when several models with different auxiliary assumptions produce the same result.

It is tempting to treat this like repeated independent measurement.

**McLoone, Orzack & Sober (2025), _The epistemic status of derivational robustness_.**  
DOI: https://doi.org/10.1007/s13194-025-00673-1

They argue that agreement among multiple model derivations does not straightforwardly have the same confirmatory significance as agreement among multiple empirical measurements. A standard Bayesian defense faces serious problems.

### AI translation

```text
3 analogues supporting p
≠
3 independent observations supporting p.
```

The sources may share:

- the same mechanism assumption;
- the same representational bias;
- one underlying causal lineage;
- the same source corpus;
- the same LLM-generated abstraction;
- the same missing confounder.

## 2. Ensemble diversity itself requires justification

**Margherita Harris (2025), _Robustness Reexamined_.**  
DOI: https://doi.org/10.1515/krt-2025-0002

Harris argues that model-based robustness is more difficult to treat as confirmatory than it first appears. Even an ensemble of apparently different models may not adequately sample the relevant representational uncertainty space.

This is almost exactly a multi-analogue retrieval problem:

```text
source diversity in names/domains
≠
independence in inferential structure.
```

A system needs a reason to believe its source set explores genuinely different failure modes.

## 3. Lehtinen 2026 — inferential rules clarify what robustness can establish

**Aki Lehtinen, _Inferential rules for confirmatory robustness_, European Journal for Philosophy of Science 16:34 (2026).**  
DOI: https://doi.org/10.1007/s13194-026-00722-3

Lehtinen responds directly to recent criticism by giving two non-standard inferential update rules.

### Derivational Confirmation Rule (DCR)

Using component `X` in deriving result `R` can increase confidence in:

```text
P(R | X)
```

when relevant variation in other model components shows that `R` persists.

### Derivational Disconfirmation Rule (DDR)

If `R` can be derived **without** component `X`, this lowers the reason to think `X` is required for `R`.

The important point is not the exact notation. Robustness can reveal which components are doing inferential work and which auxiliaries are dispensable.

## 4. Robustness is still not automatically empirical confirmation

Lehtinen's positive account preserves an important limitation:

```text
robust model result
≠
empirically confirmed real-world result.
```

Derivational robustness can strengthen an indirect confirmation chain when an empirically validated result and a model prediction depend on the same relevant components. Without such an empirical bridge, robustness mainly changes confidence in the model-level conditional relationship.

### AI translation

Several analogues may establish:

```text
projection p is insensitive to source-specific auxiliaries x,y,z
```

without establishing:

```text
p is true in target T.
```

The latter still needs target-side/externally validated evidence.

## 5. What agreement can still do

Agreement across deliberately varied assumptions can help identify:

- conclusions insensitive to some auxiliaries;
- assumptions that actually control the result;
- regions of representational uncertainty;
- disagreement cases that diagnose failure.

The engineering target should therefore be **structured robustness analysis**, not majority vote.

## 6. Multi-analogue confirmation as an intervention over assumptions

A stronger procedure is:

```text
source S1 supports p under assumptions A + x
source S2 supports p under assumptions A + y
source S3 supports p under assumptions A + z
```

Then ask:

```text
what common structure A is doing the work?
are x,y,z genuinely different?
is p robust because of A,
or are all sources reproducing one shared mistake?
```

This turns multi-analogue reasoning into a form of assumption sensitivity analysis.

A Lehtinen-inspired controller could additionally ask:

```text
Can p still be obtained when suspected auxiliary x is removed?
If yes, lower x's claimed relevance.
If no, x may be part of the active bridge — now seek empirical/target evidence for x.
```

## 7. Disagreement is epistemically valuable

An analogue that fails to support the dominant projection can be more informative than another confirming source.

A mature system should actively search for:

- counter-analogues;
- same-mechanism/different-outcome cases;
- different-mechanism/same-outcome cases;
- sources that isolate a suspected moderator/boundary condition.

This is a stronger use of source diversity than maximizing confirmation count.

## 8. Relation to cross-analogy confirmation

For systems such as CANA, cross-analogy confirmation is plausible only when supporting sources are sufficiently independent relative to the inferred structural role.

The robustness literature adds two stronger demands:

1. independence should be assessed at the level of **assumptions and representational failure modes**, not only event identity;
2. agreement should identify what is **invariant under meaningful variation**, then seek an external/target evidential bridge before calling that invariance empirical confirmation.

Two historical cases with no direct genealogical relation can still depend on the same abstract model supplied by the reasoning system.

## 9. Candidate metrics

A multi-analogue controller could record:

```yaml
source_id:
projection:
shared_core_assumptions:
source_specific_assumptions:
data_provenance:
mechanism_lineage:
representation_generator:
independence_estimate:
auxiliary_removed:
projection_survives_without_auxiliary:
external_validation_link:
disagreement_type:
```

Possible benchmark metrics:

- raw confirming-source count;
- dependence-adjusted effective source count;
- assumption diversity;
- counter-analogue recall;
- probability response to genuinely independent vs redundant confirmations;
- ability to identify the core assumption shared by robust sources;
- correct down-weighting of auxiliaries shown dispensable;
- ability to distinguish robust model-level support from empirical target confirmation.

## Bottom line

The philosophy of robustness gives a direct constraint on multi-analogue AI:

> **Do not reward agreement among sources unless the system can say what was varied, what remained invariant, which auxiliaries were shown dispensable, and what empirical bridge connects the invariant structure to the target.**

The goal is not more precedents. It is more informative variation plus external grounding.