# Background Meta-Rules — Relevance Between Mapping and Projection

**Snapshot: 21 August 2026.**

A central object in rigorous analogy theory is the rule that explains why a shared feature should make a projected feature more likely. This is **not a new computational idea**: symbolic AI work on determination rules made this object explicit decades ago. The contemporary opportunity is narrower — learn, validate and update such relevance rules in open representation spaces rather than assume them in a hand-built knowledge base.

## 1. Symbolic AI prior art — Davies & Russell 1987

**Todd Davies & Stuart Russell, _A Logical Approach to Reasoning by Analogy_, IJCAI-87, pp. 264–270.**

They analyze the domain knowledge needed to justify analogical projections and represent it with **determination rules**. In schematic form:

```text
Q = F(P1,...,Pm)
```

If source and target agree on the determining variables `P1...Pm`, the rule licenses projection of `Q` from source to target.

This work was explicitly computational/AI-oriented and was designed to specify what information is relevant enough to decide a projected property.

Therefore the repo should never claim that a `relevance rule between mapping and projection` is novel.

### The old bottleneck

The determination relation must itself be known or well supported.

As later philosophical analyses emphasize, writing down the missing rule merely relocates the justification problem:

```text
Why should we believe P1...Pm determine Q in this domain?
```

That is exactly where modern learned/open-world systems may differ from hand-engineered symbolic systems.

---

## 2. Zwirn & Zwirn 2026 — extend the rule space

**Hervé Zwirn & Denis Zwirn, _Reasoning by Analogy and by Difference_, Journal for General Philosophy of Science 57 (2026), 135–167.**  
DOI: https://doi.org/10.1007/s10838-025-09718-8

Their account treats analogy as always relative to a **domain / point of view**. There is no absolute statement that `A is analogous to B`; there is only analogy with respect to some property domain/function.

They retain determination-style meta-rules but make them probabilistic/non-monotonic and broaden the possible relation between mapped and projected dimensions.

Schematically:

```text
f(A) = f(B)
g(B) = β
background meta-rule: f determines g with strength λ
→ infer g(A) = β with corresponding defeasible strength
```

## 3. Reasoning by difference is broader than vetoing similarity

The framework distinguishes four directions of meta-level dependence:

```text
similarity → similarity       (determination)
difference → difference       (separation)
similarity → difference       (counter-determination)
difference → similarity       (counter-separation)
```

This is valuable because source–target differences need not simply lower a global analogy score.

A difference can be **positive evidence** for a particular projection, while a similarity can sometimes be evidence that another property should differ.

That is much richer than:

```text
positive analogy adds points
negative analogy subtracts points.
```

## 4. Meta-rules may be probabilistic and exception-ridden

Empirical determination rules are rarely exceptionless. The account allows probabilistic/non-monotonic forms.

This is close to an applicability model:

```text
P(g(A)=g(B) | f(A)=f(B), context) = λ.
```

But a modern controller additionally needs exception conditions, domain shift and evidence for why the rule should be trusted in this target.

## 5. Why this still matters for foundation models

Modern LLM systems increasingly learn:

```text
representation
retrieval
mapping
```

from open text/data rather than receiving a symbolic ontology.

The unsolved modernized problem is therefore not:

```text
invent the notion of determination/relevance.
```

It is:

```text
learn candidate relevance rule f → g
from heterogeneous evidence
→ estimate its domain/context of validity
→ identify exceptions/boundaries
→ calibrate its strength
→ update it after target outcomes
→ preserve provenance/evidence.
```

That is a different engineering problem from supplying a determination rule manually.

## 6. Competing analogies become competing rule applications

When sources disagree, the question is not only which source is more similar.

Instead ask:

```text
which background rule connects each source mapping to the projected claim?
how strong is that rule in this target context?
which exception / counter-rule is active?
```

This is a cleaner way to localize disagreement.

## 7. Relation to bridge hypotheses

Nappo's Bayesian `bridge hypothesis` and determination/meta-rules perform related but not identical functions.

A useful engineering decomposition is:

```text
mapping:
  S and T share feature/relation f

bridge/relevance rule:
  sharing f tends to imply shared/contrasting g

projection:
  g(S)=β therefore candidate g(T)=β (or ≠β)

context/evidence:
  support or defeat the bridge/relevance rule in this case
```

This creates a typed place for transfer failure.

## 8. Training opportunity

Instead of training only on source-target-answer triples, construct examples containing:

```text
shared dimension f
projected dimension g
context C
observed target outcome
```

and learn whether the relation `f → g` is:

```text
supportive
separating
counter-determining
irrelevant
conditional on C
```

The novelty, if any, would lie in **learning and validating open-world analogical relevance operators**, not in the existence of determination rules themselves.

## 9. Falsification criterion

The modern relevance-head hypothesis should be weakened if:

- end-to-end outcome training learns projection relevance equally well without an explicit rule state;
- learned rules fail to generalize beyond the domains used to identify them;
- extracted meta-rules merely paraphrase model outputs without improving calibration or transfer;
- symbolic/causal tools already provide the required relation more reliably in the target domain.

## Bottom line

The historical computational lesson and contemporary philosophy converge:

> **A correspondence becomes inferentially useful only through background knowledge connecting the mapped feature to the property being projected.**

The 2026 research question is not whether that layer should exist conceptually. It is whether foundation-model systems can **learn, calibrate, falsify and revise it in open domains**.