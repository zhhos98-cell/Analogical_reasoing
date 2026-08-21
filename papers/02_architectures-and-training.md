# 02 — Architectures & training

Work that changes the learning system itself rather than merely prompting a pretrained model to produce analogies.

## Altabaa 2024

### Abstractors and relational cross-attention: An inductive bias for explicit relational reasoning in Transformers

**Awni Altabaa, Taylor Webb, Jonathan D. Cohen, John Lafferty.** ICLR 2024.  
Canonical: https://openreview.net/forum?id=XNa6r6ZjoB  
Preprint: https://arxiv.org/abs/2304.00195

**Mechanism.** Introduces the Abstractor and relational cross-attention, designed to disentangle relational information from object-level features. The architectural claim is that explicit relational inductive bias improves sample efficiency and systematic generalization.

**Why it belongs here.** This is one of the clearest cases where a cognitive claim about relations has become a neural architectural constraint rather than an analogy-themed benchmark.

**Historical collision.** Gentner/systematicity is the nearest classical analogue. The deeper unresolved issue is representation selection: the architecture privileges relations once available, but does not by itself solve which relational description is the right one.

---

## Zhou 2025

### Self-supervised Analogical Learning using Language Models

**Ben Zhou, Sarthak Jain, Yi Zhang, Qiang Ning, Shuai Wang, Yassine Benajiba, Dan Roth.** arXiv, 3 Feb 2025.  
Canonical: https://arxiv.org/abs/2502.00996

**Mechanism.** SAL generates surface-distinct cases that share a reasoning process, extracts high-quality symbolic solutions from cases the model can solve, and uses those solutions as analogical supervision for harder cases.

**Why it belongs here.** It moves analogy from inference-time prompting toward a **training-data and supervision principle**. The relevant object is not an analogy answer but an invariant reasoning schema transferred across cases.

**Historical collision.** Closest to analogical schema induction and transfer. Hesse becomes relevant when asking which analogically generated supervision should be rejected; Whewell becomes relevant if the system must choose among competing abstractions rather than receive a conceptualization step for free.

---

## Dats 2026

### On the Geometry of Analogical Reasoning in Latent Space

**Oleg Dats.** GRaM workshop, PMLR 326 (2026), 135–144.  
Canonical: https://proceedings.mlr.press/v326/dats26a.html

**Mechanism.** Treats analogical consistency as a latent-space geometric constraint: paired examples should share a displacement, and a task-level transformation can be estimated from those differences.

**Why it belongs here.** It makes a very explicit proposal about what an analogical relation should look like geometrically, rather than assuming attention will discover the right structure implicitly.

**Historical collision.** Useful as a deliberately minimal case against which richer accounts can be tested. A single displacement captures stable relation transfer but leaves open systematicity, causal relevance, negative analogy, and representation plasticity.

**Watch question.** When does a simple translation geometry fail because the relation itself must be redescribed at a different level of abstraction?
