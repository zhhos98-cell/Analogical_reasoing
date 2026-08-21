# Last-Mile Scan — Partial Transfer, Learned Representations, and Negative Transfer

**Snapshot: 21 August 2026.**

This note stress-tests the remaining claim that open-world analogical reasoning still lacks a unified `learn representation → choose source → decide what transfers → revise after failure` loop. The search focuses on work that comes unusually close without using analogy as its primary label.

## 1. Latent contextual bandits + causal transportability: three pieces already coexist

### Deng, Kyrki & Baumann (2025)

**Transfer Learning in Latent Contextual Bandits with Covariate Shift Through Causal Transportability**  
Canonical: https://arxiv.org/abs/2502.20153

This is one of the closest adjacent systems found so far. The true context is latent, the agent observes a potentially high-dimensional proxy, and source/target environments differ by covariate shift. Naively reusing source knowledge produces negative transfer. The method therefore combines:

- high-dimensional proxy observations;
- a learned VAE-style latent representation for causal-effect estimation;
- a causal transport formula specifying what source knowledge can be reused;
- online bandit interaction and target reward;
- explicit avoidance of negative transfer.

The paper's key formal distinction is already highly suggestive for analogy. A causal effect conditioned on the true latent context can be directly transportable, while the same effect conditioned on the observed proxy is **not** directly transportable; the target posterior over latent context must be accounted for. Thus a representation that looks sufficient at the observational level can license the wrong transfer.

### Why this still does not close the analogy gap

The transfer object is fixed in advance: a causal effect under a specified SCM/selection-diagram family. The system does not autonomously propose competing relational descriptions of a raw source and target, decide which relations constitute the analogy, or use failed transfer to revise that relational ontology.

It therefore gets remarkably close to:

`learned representation + validity-aware transfer + online outcome`,

but not:

`open source/target representation + analogical mapping + claim-level applicability + relational rerepresentation`.

---

## 2. Representation-based multi-source domain adaptation: “what should be represented and transferred?” is already explicit

### Ng et al., ICML 2025

**A General Representation-Based Approach to Multi-Source Domain Adaptation**  
Canonical: https://proceedings.mlr.press/v267/ng25a.html

This work starts from high-dimensional observations and asks directly what latent representation should be learned for transfer. It argues that simply preserving all predictive information can be underspecified, and instead partitions learned representations of the label's Markov blanket into parents, children, and spouses. This yields an identifiable domain-adaptation framework under broader distribution shifts.

### Analogy relevance

This invalidates another overly broad gap statement: modern transfer learning does already jointly study **representation learning and selective transfer**.

What remains different in analogy is the unit of transfer. Domain adaptation typically fixes the prediction variable/task and learns which latent factors support target prediction. Open analogical reasoning must often infer the task-relevant relational vocabulary itself and may project multiple new claims rather than optimize one fixed target label.

---

## 3. Unknown-source Bayesian transfer: negative applicability can be inferred from noisy proxies

### Sloman, Martinelli & Kaski, UAI 2025

**Proxy-informed Bayesian transfer learning with unknown sources**  
Canonical: https://proceedings.mlr.press/v286/sloman25a.html

PROMPT gives a Bayesian account of negative transfer when source identity/differences are partly unknown. It can operate without explicit knowledge of the source data-generating source and without target observations for fine-tuning, using noisy proxy information instead. The core diagnosis is that negative transfer can arise from misspecified beliefs about source causes that are not transferable.

### Analogy relevance

This weakens the claim that transfer-validity machinery always requires complete knowledge of source differences. Uncertainty over hidden source differences can itself be modeled.

The remaining analogy-specific challenge is still relational: the model must infer *which correspondence or projected claim* depends on the non-transferable cause, not merely robustify an overall predictive transfer.

---

## 4. Transportable representations: representation and transportability already have a formal bridge

### Jalaldoust & Bareinboim, AAAI 2024

**Transportable Representations for Domain Generalization**  
Canonical: https://ojs.aaai.org/index.php/AAAI/article/view/29175

The paper defines representations suited for domain generalization from causal transportability, and then relaxes direct access to the underlying causal graph through a graphical-invariance duality result. This is an important prior bridge between `learn/identify a representation` and `prove that it supports transfer`.

### Consequence

The frontier cannot be described merely as “combine learned representations with transportability”; that combination already exists in restricted forms. The remaining open requirement is stronger:

> **learn a relational source–target representation whose individual projected inferences can be selectively licensed, vetoed, or revised under open-domain evidence.**

---

## 5. Current best boundary after the last-mile scan

Several adjacent communities now cover nearly every pairwise combination:

| Combination | Existing evidence |
|---|---|
| learned representation + transfer | ICML multi-source DA; transportable representations |
| latent representation + formal transport | latent contextual bandits + causal transportability |
| transfer validity + uncertainty | generalized causal transportability; Bayesian negative-transfer methods |
| retrieval + adaptation cost | modern CBR; RA-RFT |
| retrieval + online utility learning | CASCADE / Memento |
| failure detection + targeted repair | Skill-RAG / Doctor-RAG / AgentRx |
| failure + state/representation expansion | BALAR / WorldEvolver |

What remains thin is the **relational granularity and feedback coupling**:

1. the system itself proposes what source and target relations should be compared;
2. source utility is evaluated after target-specific rebinding/adaptation;
3. transfer validity is estimated **per projected relation/claim**, not only per model/domain/task;
4. a failed projected claim is attributed to the source, representation, mapping, applicability assumption, or execution;
5. that attribution can change the relational representation itself;
6. the resulting positive and negative applicability boundary persists into later retrieval.

This is a considerably narrower claim than the repository began with, and therefore a stronger one.

## 6. Proposed benchmark signature

A decisive benchmark should force all of these operations in one environment:

`raw target`

`→ choose among multiple possible relational decompositions`

`→ search a heterogeneous source bank`

`→ adapt/rebind candidate sources`

`→ output several candidate projections`

`→ mark each as licensed / vetoed / uncertain`

`→ receive executable or observational feedback`

`→ diagnose why one transfer failed`

`→ revise representation or source policy`

`→ face a related later target where the learned applicability boundary matters`.

The key score would be neither answer accuracy nor mapping accuracy alone. It would jointly measure **source precision, claim-level transfer calibration, failure attribution, rerepresentation quality, and later reduction in repeated negative transfer**.
