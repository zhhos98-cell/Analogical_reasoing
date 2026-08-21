# Current Map — Eight Problems in Scientific Analogy and Transfer

**Snapshot: 21 August 2026.**

The useful unit is not a philosopher or a historical school. It is an **epistemic operation** that a scientific analogue must survive before a source can support a target inference.

## P1 — Source/target representation

Before similarity can be assessed, source and target must be represented under some description.

This is not neutral. Different variables, levels of abstraction or conceptualizations can produce different analogues.

**Current evidence:** Valente et al. (2024) show that spatial climate-analogue methods face both **source non-uniqueness** and **target non-uniqueness**; the choice of climate indicators and dissimilarity metric helps determine what counts as the analogue in the first place.

**AI translation:** representation selection should be part of the inference state, not hidden preprocessing.

---

## P2 — Plausibility / relevant similarity

Similarity is multidimensional. A high geometrical or semantic score does not by itself establish inferential relevance.

Climate analogues make this especially clear: geometrical similarity can lose information when moving from physical climate variables to socioeconomic effects.

**AI translation:** source retrieval should optimize downstream inferential utility or relevance, not semantic similarity alone.

---

## P3 — Logical transfer

Suppose source and target really are comparable in some respects. What exactly follows?

The extrapolation literature distinguishes the **logical problem** from the evidential problem. A valid transfer argument must state what study/source result is being transferred and what comparability premises connect source to target.

**AI translation:** projection generation and projection validity are separable. A mapping can be correct while a particular projected claim is not licensed.

---

## P4 — Evidence for comparability

It is one thing to write a comparability premise and another to have evidence for it.

Fuller (2025) calls this the **evidential problem of extrapolation**. Structural analogies can sometimes supply evidence that source and target factors play corresponding causal roles, but the evidence must not simply smuggle in the target conclusion.

**AI translation:** a model-generated mechanism graph cannot validate itself. Transfer conditions need target-side evidence, provenance or falsifiable tests.

---

## P5 — Confirmation

Does evidence from the source actually raise the probability of a hypothesis about the target?

Nappo (2022) gives a Bayesian account in which similarities and dissimilarities support a target hypothesis only relative to background/context and a bridge hypothesis. Gebharter & Osimani (2025/26) show that different Bayesian structures capture different forms of analogical inference and that increasing believed similarity need not always increase target confirmation.

**AI translation:** `similarity ↑` must not mechanically imply `transfer confidence ↑`.

---

## P6 — Difference, uncertainty and applicability boundaries

Scientific extrapolation usually relies on assumptions that remain uncertain. Khosrowi (2023) argues that a serious framework must explicitly manage uncertainty around extrapolation assumptions rather than merely list them.

Negro & Mudrik (2026) likewise treat the **problem of difference** as central to extrapolating consciousness to nonstandard systems: structural similarity is useful, but no simple similarity threshold settles when the analogy is sufficient.

**AI translation:** the controller needs conditional/veto/unknown states and uncertainty over applicability, not a binary analogue/non-analogue label.

---

## P7 — Multiple sources, robustness and competing analogues

Several supporting analogues are not automatically several independent confirmations. Agreement can arise from shared assumptions, shared data or redundant representations.

Scientific practice often uses ensembles of models, organisms, experiments or analogue systems because their agreement and disagreement reveal different vulnerabilities.

**AI translation:** count effective evidence, not raw precedent count. Track dependence and retrieve counter-analogues.

---

## P8 — Representation revision and target-side validation

An analogy can fail under one representation and become informative after justified conceptual revision.

Gibson (2025) argues that Darwin's analogy between artificial and natural selection only supported natural selection after substantive conceptual revisions; formal structure alone cannot explain the change in evidential role.

This implies a stronger feedback loop:

```text
representation
→ analogy
→ failed/ambiguous transfer
→ revise representation
→ remap
→ test on target
```

**AI translation:** failed transfer should be capable of triggering relational rerepresentation rather than only lowering a source score.

---

# A compact contemporary PoS pipeline

```text
construct source/target representation
→ identify candidate relevant similarities
→ state exact projected conclusion
→ make comparability assumptions explicit
→ gather evidence for/against those assumptions
→ compute/assess confirmation under background knowledge
→ propagate uncertainty and differences
→ compare alternative sources/representations
→ test consequences in the target
→ revise representation or applicability boundary
```

# The key mismatch with current AI

Many current AI systems are strongest in the middle:

```text
retrieve → abstract → align → project
```

Contemporary philosophy of science concentrates on the boundaries around that operation:

```text
Why this representation?
Why is this similarity relevant?
What evidence warrants transfer?
How much support is gained?
Which difference blocks which conclusion?
What target observation would falsify the transfer?
```

That makes philosophy of science less a source of decorative historical concepts than a candidate **specification language for transfer control**.

# Core current literature

- Nappo & Valente (2026), *Analogical Reasoning in Science*, Cambridge Elements in Philosophy of Science. DOI: 10.1017/9781009526494.
- Gebharter & Osimani (2026 issue / 2025 online), *The Formal Structure(s) of Analogical Inference*, Erkenntnis 91:923–953. DOI: 10.1007/s10670-025-00934-8.
- Nappo (2022), *Confirmation by analogy*, Synthese 200:35. DOI: 10.1007/s11229-022-03545-w.
- Valente, Bobadilla, El Skaf & Nappo (2024), *Tales of twin cities: what are climate analogues good for?*, EJPS 14:34. DOI: 10.1007/s13194-024-00597-2.
- Khosrowi (2023), *Extrapolating from experiments, confidently*, EJPS 13:18. DOI: 10.1007/s13194-023-00520-1.
- Fuller (2025), *Problems of Extrapolation*, in *The New Modern Medicine*. DOI: 10.1093/9780190066178.003.0010.
- Negro & Mudrik (2026), *Extrapolating Other Consciousnesses: The Prospects and Limits of Analogical Abduction*, Philosophy of Science 93:181–202. DOI: 10.1017/psa.2025.10104.
- Gibson (2025), *Conceptual revision: how Darwin's analogy supported his theory*, Biology & Philosophy 40:16. DOI: 10.1007/s10539-025-09988-y.
- Boniolo, Boniolo & Valente (2023), *Prediction via Similarity: Biomedical Big Data and the Case of Cancer Models*, Philosophy & Technology. DOI: 10.1007/s13347-023-00608-9.