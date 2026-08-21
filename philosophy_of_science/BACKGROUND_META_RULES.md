# Background Meta-Rules — Relevance Between Mapping and Projection

**Snapshot: 21 August 2026.**

A central missing object in many analogy pipelines is the rule that explains why a shared feature should make a projected feature more likely.

## 1. Zwirn & Zwirn 2026

**Hervé Zwirn & Denis Zwirn, _Reasoning by Analogy and by Difference_, Journal for General Philosophy of Science 57 (2026), 135–167.**  
DOI: https://doi.org/10.1007/s10838-025-09718-8

Their account treats analogy as always relative to a **domain / point of view**. There is no absolute statement that `A is analogous to B`; there is only analogy with respect to some property domain/function.

More importantly, analogical inference requires meta-level background rules connecting the shared dimension to the projected dimension.

Schematically:

```text
f(A) = f(B)
g(B) = β
background meta-rule: f determines g with strength λ
→ infer g(A) = β with corresponding defeasible strength
```

## 2. Why this is a useful missing layer

Most computational pipelines can already estimate:

```text
f(A) ≈ f(B)
```

but often jump directly to:

```text
g(B) → g(A).
```

The meta-rule supplies the **relevance relation**:

```text
Why should sameness on f tell us anything about sameness on g?
```

Engineering translation:

```text
mapping score
+
projection-specific relevance rule
→ transfer strength.
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

But a controller should additionally represent exception conditions and domain shift.

## 5. Competing analogies become competing rule applications

When sources disagree, the question is not only which source is more similar.

Instead ask:

```text
which background rule connects each source mapping to the projected claim?
how strong is that rule in this target context?
which exception / counter-rule is active?
```

This is a cleaner way to localize disagreement.

## 6. Relation to bridge hypotheses

Nappo's Bayesian `bridge hypothesis` and Zwirn & Zwirn's meta-rule perform related but not identical functions.

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

## 7. Training opportunity

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

This begins to look like learning **analogical relevance operators** rather than memorizing analogies.

## Bottom line

The meta-rule framework provides a strong candidate answer to the interface between mapping and transfer:

> **A correspondence becomes inferentially useful only when background knowledge links the mapped feature to the property being projected.**

For AI, that suggests a dedicated projection-relevance layer, explicitly separable from source retrieval and structural alignment.