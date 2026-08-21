# 05 — Generalization, adjudication & failure

Work that reveals where analogy breaks: far transfer, source diversity, over-application, and failure to distinguish a plausible analogy from a licensed inference.

## Stevenson 2026

### Can Large Language Models Generalize Analogy Solving Like Children Can?

**Claire E. Stevenson, Alexandra Pafford, Han L. J. van der Maas, Melanie Mitchell.** TACL 14 (2026), 612–626.  
Canonical: https://aclanthology.org/2026.tacl-1.28/  
DOI: https://doi.org/10.1162/tacl.a.614

**Finding.** Children and adults transfer a learned analogy-solving procedure from the Latin alphabet to a near-transfer Greek domain and then to unfamiliar symbols much more robustly than LLMs.

**Why it is core.** It isolates a central distinction between high benchmark accuracy and genuinely portable relational procedure. The failure is especially relevant to claims of human-like abstraction.

**Historical collision.** Gentner explains why relational structure should support far transfer, but the paper also raises a representation question: when the surface code changes radically, what invariant description does the model preserve? This links to relational bottlenecks and to Hofstadter-style recoding.

---

## Shen 2026

### On the Diversity of Analogy Making in Large Language Models

**Yuanhao Shen, Daniel Xavier de Sousa, Caio César Sifuentes Barcelos, Hongyu Guo, Xiaodan Zhu.** arXiv, 4 Aug 2026.  
Canonical: https://arxiv.org/abs/2608.03233

**Finding.** Across ten contemporary open- and closed-source LLMs, analogy generation is strongly domain-homogeneous. Methods that increase diversity often reduce analogy quality. Causal information-flow analysis suggests that the regions governing diversity differ across models.

**Why it is latest/core.** Most analogy work asks whether the model can map a supplied source to a target. This paper moves upstream to **which candidate analogies are generated at all**. A system with perfect mapping over a narrow source repertoire still has weak analogical intelligence.

**Historical collision.** This opens a source-retrieval and conceptual-search problem. Hofstadter is highly relevant because analogy making is treated as an active search through fluid descriptions rather than selection from a fixed database. Whewell becomes relevant when candidate diversity must be disciplined by explanatory or predictive value.

**Repo question.** Can diversity be increased without quality collapse by rewarding structural/causal novelty rather than surface-domain novelty alone?

---

## Failure-mode slot: transfer veto / negative analogy

The current literature is much stronger on `find relation → align → transfer` than on **when to refuse transfer**.

A Hesse-inspired benchmark should hold most of a mapping constant while changing one inference-critical relation. Desired test structure:

`high surface similarity + high partial structural alignment + one causal/essential mismatch → transfer should be blocked`

This would distinguish relational recognition from analogical adjudication. It is a priority gap for later experimental work.
