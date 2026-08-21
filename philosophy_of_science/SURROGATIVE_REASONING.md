# Surrogative Reasoning — Model-to-Target Inference as a Control Problem

**Snapshot: 21 August 2026.**

Scientific models are often used as **surrogates**: scientists reason about a model/source and then interpret the resulting inference as a claim about a target.

That structure is extremely close to analogical reasoning:

```text
operate/reason on source representation
→ derive source/model result r
→ interpret r in target terms
→ target claim p
```

The scientific-representation literature shows why this operation should be decomposed rather than treated as one similarity score.

---

## 1. Surrogative reasoning condition

A central requirement on scientific representation is that a model allow users to form claims about its target by reasoning with the model.

The inferential conception of representation reverses a common explanatory order:

instead of saying

```text
model represents target because model and target are similar/isomorphic
therefore inference is possible
```

it emphasizes the actual **inferential practice** that connects model to target.

This matters because similarity is neither necessary nor sufficient as a universal explanation of scientific representation.

---

## 2. Demonstration and interpretation are distinct steps

The DDI-style structure is useful for AI:

```text
DENOTATION:
  what target is this source/model being used to stand for?

DEMONSTRATION:
  what follows inside the model/source representation?

INTERPRETATION:
  how is that model result translated into a claim about the target?
```

Analogical systems often blur the second and third steps.

For example:

```text
source mechanism implies outcome O
```

may be internally correct, while

```text
therefore target will exhibit O'
```

fails because interpretation/rebinding is invalid.

---

## 3. Correctly performed transfer can still yield a false target claim

The inferential literature distinguishes the **correctness of an inferential procedure relative to a representation** from truth of all its target conclusions.

That distinction is critical for mechanistic evaluations of LLM analogy.

A model can:

```text
encode source relation correctly
map roles according to its representation correctly
apply the mapped transformation correctly
```

and still be wrong because:

- the representation itself is inaccurate;
- the source is not externally valid for the target;
- an idealization fails in the target;
- the interpretation step over-projects;
- the target changed regime.

Thus hidden-state evidence of correct mapping is not sufficient evidence of correct analogical inference in the world.

---

## 4. Transfer protocol as an explicit object

A modern analogue controller should log its interpretation rule:

```yaml
source_result: r
mapping:
rebindings:
interpretation_rule:
target_claim: p
bridge_assumptions:
validation_state:
```

Then errors can be attributed separately to:

```text
SOURCE DEMONSTRATION ERROR
MAPPING ERROR
INTERPRETATION/REBINDING ERROR
BRIDGE-ASSUMPTION ERROR
TARGET REPRESENTATION ERROR
```

This is much more informative than final-answer accuracy alone.

---

## 5. Inconsistent and idealized representations

Scientific models are often idealized and sometimes internally inconsistent, yet still support useful reasoning.

This creates an important warning for AI:

> **inferential power alone cannot be the criterion of transfer legitimacy.**

A sufficiently expressive source representation can support many internally valid derivations, some of which should not be interpreted as target claims.

The controller therefore needs **restricted inference permissions**:

```text
which demonstrations are exportable?
under what interpretation?
for which target property?
```

This is the same projection-level license problem found throughout the analogy map.

---

## 6. Model vs target uncertainty

Surrogative reasoning also helps separate two uncertainties:

```text
U_model:
  uncertainty about what the source/model itself entails

U_transfer:
  uncertainty about whether that entailment carries to target
```

Generic LLM outputs often merge them into one confidence value.

Better output:

```text
source entailment confidence: 0.95
source→target bridge confidence: 0.55
final target probability: 0.60
```

This is particularly important for analogue experiments and historical precedents, where source understanding may be strong while external validity is weak.

---

## 7. Relation to foundation-model analogy

Modern LLM analogy systems are unusually good candidates for surrogative analysis because they can generate both the source-side demonstration and the target-side interpretation in natural language.

That flexibility is also dangerous: the interpretation step can silently introduce new premises.

Benchmark requirement:

```text
show which target claim came from which source result
show the rebinding operation
show any added target-specific assumptions
```

This turns analogy prose into an auditable transfer path.

---

## 8. AI-specific research questions

1. Can models distinguish source-side entailment confidence from bridge confidence?
2. Can an interpreter/verifier identify when a source conclusion is valid internally but not exportable?
3. Can transfer rules be learned from resolved source→target outcomes?
4. Does explicit interpretation logging improve calibration?
5. Can representation revision be triggered when repeated interpretation errors cluster around one source/target encoding?

---

## 9. Relation to the larger controller

Surrogative reasoning inserts a missing stage into the repo's pipeline:

```text
representation
→ source reasoning / demonstration
→ mapping
→ INTERPRETATION / TARGET REBINDING
→ transfer licensing
→ target prediction
→ validation
```

The interpretation stage deserves its own evaluation rather than being absorbed into mapping or projection.

---

## References

- Frigg & Nguyen, *Scientific Representation* (Cambridge Elements).
- Stanford Encyclopedia of Philosophy, “Scientific Representation,” updated 2026.
- Mauricio Suárez, inferential conception of scientific representation; *Inference and Representation* (2024).
- Work on inconsistent idealizations and inferentialism emphasizes that unrestricted inferential capacity is not sufficient for scientific representation.
