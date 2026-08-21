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

## 3. What agreement can still do

Robustness need not be useless.

Agreement across deliberately varied assumptions can help identify:

- conclusions insensitive to some auxiliaries;
- assumptions that actually control the result;
- regions of representational uncertainty;
- disagreement cases that diagnose failure.

The engineering target should therefore be **structured robustness analysis**, not majority vote.

## 4. Multi-analogue confirmation as an intervention over assumptions

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

## 5. Disagreement is epistemically valuable

An analogue that fails to support the dominant projection can be more informative than another confirming source.

A mature system should actively search for:

- counter-analogues;
- same-mechanism/different-outcome cases;
- different-mechanism/same-outcome cases;
- sources that isolate a suspected moderator/boundary condition.

This is a stronger use of source diversity than maximizing confirmation count.

## 6. Relation to cross-analogy confirmation

For systems such as CANA, cross-analogy confirmation is plausible only when supporting sources are sufficiently independent relative to the inferred structural role.

The robustness literature adds a stronger demand:

> independence should be assessed at the level of **assumptions and representational failure modes**, not only event identity.

Two historical cases with no direct genealogical relation can still depend on the same abstract model supplied by the reasoning system.

## 7. Candidate metrics

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
disagreement_type:
```

Possible benchmark metrics:

- raw confirming-source count;
- dependence-adjusted effective source count;
- assumption diversity;
- counter-analogue recall;
- probability response to genuinely independent vs redundant confirmations;
- ability to identify the core assumption shared by robust sources.

## Bottom line

The philosophy of robustness gives a direct constraint on multi-analogue AI:

> **Do not reward agreement among sources unless the system can say what was varied, what remained invariant, and why the sources represent distinct opportunities for error.**

The goal is not more precedents. It is more informative variation.