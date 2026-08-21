# 04 — Structure mapping & neuro-symbolic systems

Work that explicitly separates learned representation formation from mapping/alignment machinery.

## Khojasteh 2026

### Enhancing Structural Mapping with LLM-derived Abstractions for Analogical Reasoning in Narratives

**Mohammadhossein Khojasteh, Yifan Jiang, Stefano De Giorgis, Frank van Harmelen, Filip Ilievski.** arXiv, 31 Mar 2026.  
Canonical: https://arxiv.org/abs/2603.29997

**System.** YARN (Yielding Abstractions for Reasoning in Narratives).

**Mechanism.** LLMs first decompose narratives and produce abstractions; a separate mapping component then aligns source and target units. The design is motivated by a basic mismatch: classical cognitive mapping engines assume structured inputs, whereas LLMs can form representations from raw text but are sensitive to surface similarity and prompting.

**Why it is core.** This is perhaps the cleanest current attempt to reconnect old analogical mapping machinery with contemporary representation learners. It also makes the key unresolved problem empirically visible: **no single abstraction level is optimal across cases**.

**Historical collision.** The mapping half descends from the structure-mapping/FAME family. The representation half opens the older dispute over whether analogy begins only after representations are fixed. Hofstadter's critique of hand-built representations and Whewell's selection/construction of the conception are directly relevant here.

**Repo hypothesis.** `abstraction at the right level` may be a modern name for a much larger problem: representation selection should be evaluated together with downstream prediction and cross-domain survival, not locally before mapping.

**Possible experiment.** Generate multiple candidate abstractions for the same narrative pair; rank them not by immediate mapping score alone but by transfer accuracy on held-out consequences and by reuse across independent analogy pairs. This would turn a Whewell-like consilience criterion into a selection signal.

---

## Classical computational anchor: SME / FAME line

The repository will treat classical Structure-Mapping Engine work as **prior computational art**, not only as history. It matters because many current papers rediscover pieces of structural alignment while working with much stronger representation learners.

Key questions for comparison:

1. Which current systems preserve one-to-one correspondence and systematicity explicitly?
2. Which use similarity scores that may quietly reintroduce surface features?
3. Where are candidate inferences generated, and where are they validated?
4. Can the representation change during mapping, or is it frozen before analogy begins?
5. What modern training signal could replace hand-engineered symbolic predicates without losing structural constraints?

A later historical note should separately reconstruct SME, ACME, LISA, Copycat and FAME rather than collapsing them into a single "symbolic analogy" family.
