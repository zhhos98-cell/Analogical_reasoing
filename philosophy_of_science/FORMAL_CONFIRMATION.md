# Formal Confirmation — Why Similarity Is Not a Transfer Probability

**Snapshot: 21 August 2026.**

A central contemporary philosophy-of-science question is whether evidence obtained in a source can genuinely **confirm** a hypothesis about a target.

This is stronger than saying that source and target resemble one another.

## 1. Nappo 2022 — confirmation depends on background and a bridge hypothesis

**Francesco Nappo, _Confirmation by analogy_, Synthese 200:35 (2022).**  
DOI: https://doi.org/10.1007/s11229-022-03545-w

Nappo develops a Bayesian account in which similarities and dissimilarities can provide incremental confirmation for an empirical target hypothesis.

The key point for engineering is that similarity does not work directly:

```text
similarity evidence
→ support for a bridge/commonality hypothesis
→ bridge hypothesis is relevant to target hypothesis
→ target hypothesis receives confirmation
```

Background/context determines whether a similarity or dissimilarity is relevant and how much evidential work it performs.

This implies that an AI system needs an explicit or latent answer to:

```text
Why would this shared feature make the projected target claim more probable?
```

rather than only:

```text
How similar are S and T?
```

## 2. Similarities and dissimilarities can contribute in opposite directions

Nappo's odds formulation allows multiple similarities and dissimilarities to contribute differently to support for the bridge hypothesis.

That suggests a natural transfer-controller representation:

```text
positive evidence for bridge B
negative evidence for B
background assumptions
P(B | evidence)
P(target claim | B, background)
```

A critical difference need not make the whole analogy useless. It may specifically weaken the bridge relevant to one projection while leaving another intact.

This lines up with projection-level selective transfer.

## 3. Gebharter & Osimani — there is no single formal structure of analogy

**Alexander Gebharter & Barbara Osimani, _The Formal Structure(s) of Analogical Inference_, Erkenntnis 91 (2026), 923–953; online 2025.**  
DOI: https://doi.org/10.1007/s10670-025-00934-8

They investigate a Bayesian model developed in the analogue-gravity literature and ask whether it generalizes.

A striking result is that under some structures, increasing the believed degree of source–target similarity can **decrease** the confirmation of the target hypothesis.

They then construct an alternative model with monotonic congruence between believed similarity and confirmation, and argue that the models capture **different types of analogical inference**.

### Engineering consequence

There should be no universal assumption:

```text
similarity ↑ ⇒ transfer confidence ↑
```

without specifying the causal/probabilistic role the similarity plays.

The same observed resemblance can behave differently under different inferential structures.

## 4. Two distinct tasks often conflated in AI

A useful distinction is:

### Analogue recognition

```text
Does S resemble T under representation R?
```

### Analogical confirmation

```text
Does evidence E_S from S increase support for target hypothesis H_T,
given background K and bridge B?
```

A model can succeed at the first and fail at the second.

This is very close to the empirical AI failure:

```text
relation encoded correctly
+ structural alignment succeeds
+ projected inference still inappropriate
```

## 5. Formal models are diagnostic, not self-validating

Nappo explicitly treats the Bayesian representation as a way to make the conditions of confirmation precise, not as a substitute for determining whether those conditions hold in scientific practice.

For AI, this is crucial.

A transfer head might correctly implement:

```text
if assumptions A1,A2,A3 hold → P(H_T) rises
```

while the model is wrong that A1,A2,A3 actually hold.

So evaluation must split:

```text
formal/calculational correctness
from
empirical support for the formal inputs.
```

## 6. Candidate engineering object: bridge hypothesis

The philosophy literature suggests making the **bridge** first-class.

Instead of:

```text
S analogous to T → project p
```

use:

```text
S evidence E
→ bridge hypothesis B:
   "S and T share mechanism/role X relevant to p"
→ target hypothesis H
```

Then ask separately:

```text
P(B | similarities, dissimilarities, context)
P(H | B, source evidence, target evidence)
```

This could make analogical failure diagnosis much sharper:

- source evidence wrong;
- bridge unsupported;
- bridge true but irrelevant to H;
- target evidence vetoes H;
- probability calibration wrong.

## Bottom line

Contemporary formal philosophy of analogy gives a direct warning to AI:

> **Similarity is evidence only through an inferential structure. It is not itself a transferable quantity.**

The natural engineering target is therefore not a universal analogy score but a model of how specific similarities/differences support a bridge hypothesis that is itself relevant to a particular projected claim.