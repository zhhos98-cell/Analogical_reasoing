# 03 — Mechanisms & interpretability

Work asking what Transformer representations actually do during analogical reasoning: relation extraction, alignment, transfer, and abstraction.

## Minegishi 2026

### Emergent Analogical Reasoning in Transformers

**Gouki Minegishi, Jingyuan Feng, Hiroki Furuta, Takeshi Kojima, Yusuke Iwasawa, Yutaka Matsuo.** arXiv, 2 Feb 2026.  
Canonical: https://arxiv.org/abs/2602.01992

**Mechanism.** Formalizes analogy as correspondence across categories and reports two components: geometric alignment of relational structure in embedding space and application of a functor-like transformation inside the Transformer. The paper also studies when the capability emerges as data, optimization, and scale change.

**Why it is core.** It treats analogy as a mechanistically decomposable learned phenomenon, not merely a behavioral capacity.

**Historical collision.** The geometric-alignment component invites direct comparison with structure mapping. The functor language provides a different formal route to relation-preserving transfer. The open problem is whether the relevant category/representation is supplied by the experiment or discovered by the model.

---

## Lee 2026

### The Curious Case of Analogies: Investigating Analogical Reasoning in Large Language Models

**Taewhoo Lee, Minju Song, Chanwoong Yoon, Jungwoo Park, Jaewoo Kang.** AAAI 2026, 40(37), 31492–31500. Published 14 Mar 2026.  
Canonical: https://doi.org/10.1609/aaai.v40i37.40414  
Code: https://github.com/dmis-lab/analogical-reasoning

**Mechanism.** Uses attention knockout, representation patching, probes, and story analogies to separate relation encoding from relation application. Relational information appears in mid-upper layers; correct story analogy is associated with stronger structural alignment.

**Why it is core.** The important result is a decomposition of failure: a model can fail because relational information is missing, because it is not transferred correctly, or because structural alignment degrades. That maps unusually well onto classical cognitive decompositions.

**Historical collision.** Gentner is the obvious comparison for structural alignment. Hesse becomes useful one step later: even a correctly aligned relation may still be an illegitimate inference if an inference-critical negative difference is present.

**Next experiment.** Add adversarial pairs where structural alignment remains high but one causal/essential relation blocks transfer; test whether hidden-state alignment predicts confident false analogy.

---

## Opiełka 2025

### Analogical Reasoning Inside Large Language Models: Concept Vectors and the Limits of Abstraction

**Gustaw Opiełka, Hannes Rosenbusch, Claire E. Stevenson.** arXiv, 5 Mar 2025.  
Canonical: https://arxiv.org/abs/2503.03666

**Mechanism.** Searches for invariant internal representations of relational concepts. It reports attention heads carrying concept vectors for some verbal relations and shows that correct internal representation can coexist with incorrect output; more abstract concepts do not always yield stable linear representations.

**Why it is core.** It sharply separates **having an abstraction** from **successfully using it**, and provides a concrete failure point for claims that function vectors straightforwardly represent concepts.

**Historical collision.** This is close to the representation problem. A Whewell/Hofstadter question is whether the failure is absence of a concept vector or the deeper fact that the relevant conception is context-sensitive and cannot be represented as a fixed invariant vector at all.
