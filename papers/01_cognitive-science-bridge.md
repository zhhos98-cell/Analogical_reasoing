# 01 — Cognitive-science bridge

Papers that explicitly connect cognitive theories of analogy to current AI/NLP. These are orientation nodes for the repository rather than merely benchmark papers.

## Petersen 2026

### Modelling Analogies and Analogical Reasoning: Connecting Cognitive Science Theory and NLP Research

**Molly R. Petersen, Claire E. Stevenson, Lonneke van der Plas.** TACL 14 (2026), 711–732.  
Canonical: https://aclanthology.org/2026.tacl-1.32/  
DOI: https://doi.org/10.1162/tacl.a.632

**Why it is core.** The clearest current bridge paper: it surveys cognitive accounts of analogical reasoning and maps them onto NLP problems that are often discussed without an analogy-theoretic vocabulary. It is therefore the best entry point for checking which older mechanisms have already been rediscovered under new names.

**Mechanisms implicated.** relational representation; source retrieval; mapping; transfer; relational vs entity-level similarity.

**Historical collision to inspect.** Gentner and Holyoak are explicit modern reference points. The repo should use the paper as a baseline, then ask what is absent from its genealogy: especially Hesse-style transfer vetoes and Whewellian representation selection / consilience.

**Next repo test.** Build a matrix from each cognitive process named in the paper to a modern NLP implementation and mark whether the implementation is architectural, training-time, inference-time, or evaluative only.

---

## Webb 2024

### The relational bottleneck as an inductive bias for efficient abstraction

**Taylor W. Webb et al.** *Trends in Cognitive Sciences* 28.9 (2024), 829–843.  
Canonical: https://doi.org/10.1016/j.tics.2024.04.001

**Why it is core.** A compact statement of a modern architectural principle that privileges relations over object attributes. It directly addresses the symbolic/connectionist problem and gives a formal language for asking when neural systems can induce abstractions from limited data.

**Mechanisms implicated.** relational abstraction; inductive bias; abstraction efficiency; separation of perceptual/object information from relational information.

**Historical collision to inspect.** Strong family resemblance to Gentner's privileging of relational structure, but it shifts the claim from a psychological mapping rule to an information-processing bottleneck. The unanswered question is upstream: who selects the relations that deserve to pass through the bottleneck? That is where Hofstadter and Whewell become relevant.

**Next repo test.** Compare the bottleneck's formal constraints with structure-mapping systematicity and ask whether a learned relation vocabulary can change during reasoning rather than remain fixed.
