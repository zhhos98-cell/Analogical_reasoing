# 06 — Discovery & causal analogy

Work where analogy is used to discover, forecast, or construct solutions in open-ended domains rather than solve a closed analogy item.

## Chen 2026

### Analogical Deep Research: Retrieving and Integrating Historical Analogies for Foresight Analysis

**Yongqiang Chen, Guangyi Chen, Yuewen Sun, Kun Zhang.** arXiv, 15 Jul 2026.  
Canonical: https://arxiv.org/abs/2607.13602

**System.** ADR-bench + Causal Analogical Researcher (CANA).

**Mechanism.** The paper argues that historical analogy is fundamentally causal: surface resemblance is insufficient because useful analogues should align underlying mechanisms. CANA adds structural decomposition, mechanism alignment, structural feedback, and **cross-analogy confirmation**.

**Why it is especially important for this repo.** This is unusually close to the historical constraint problem we want to track. The model is asked not merely to map two supplied domains, but to retrieve historical cases, compare mechanisms, and integrate multiple analogies into foresight.

**Historical collision.** Hesse enters through causal relevance and the distinction between legitimate and misleading transfer. Whewell enters through cross-case confirmation: one successful analogy is weak evidence; convergence across independent analogical lines begins to resemble a computationalized consilience criterion.

**Priority question.** Does cross-analogy confirmation genuinely test independent support, or can several retrieved cases share the same hidden bias/source family and therefore create false consilience?

---

## Larraz & Corma 2026

### Human analogical guidance amplifies LLM performance through cross-domain knowledge activation

**Rafael Larraz, Avelino Corma.** *Nature Communications* 17, 4822 (2026). Published 3 Apr 2026.  
Canonical: https://doi.org/10.1038/s41467-026-70873-7

**Setup.** Historical counterfactual reconstruction of the development of fluid catalytic cracking, using Qwen-2.5-7B with retrieval constrained to pre-1936 literature. The study holds retrieved context fixed while manipulating human analogical guidance and internal representations.

**Finding.** Human analogical guidance strongly redirects the model toward cross-domain principles already present in its accessible context. Representation steering can abolish the resulting solution generation, suggesting that guidance depends on intact internal semantic machinery rather than merely adding external facts.

**Why it is core.** It operationalizes analogy in something much closer to scientific/technical invention than a benchmark item. It also separates **knowledge availability** from **analogical activation/use**, which is crucial for thinking about autonomous discovery.

**Historical collision.** This is where Whewell becomes much more relevant than in ordinary A:B::C:? tasks. The missing capability is not only mapping but autonomous selection of a fruitful conception or cross-domain source. Human guidance currently supplies part of that selection function.

**Repo question.** Can a model learn to generate and rank its own analogical bridges by out-of-sample prediction, causal fit, and consilience, rather than requiring a human to nominate the productive comparison?

---

## Emerging research program

For open-ended analogical intelligence, a useful evaluation loop is:

`observations → candidate representations → candidate source domains → structural/causal alignment → hypothesis transfer → negative-analogy checks → novel prediction → independent-domain confirmation`

This is the part of the map where historical theories of scientific discovery may become directly computationally useful rather than merely interpretive.
