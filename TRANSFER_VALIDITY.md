# Transfer Validity — The Gap Is Narrower Than “Analogy Rejection”

This note refines the most important open gap in the repository. A broad claim such as “AI lacks mechanisms for rejecting bad transfers” is no longer defensible. Two neighboring technical communities already contain substantial machinery for deciding whether source experience can be reused in a target:

1. **Case-Based Reasoning (CBR)** develops retrieval, adaptation, failure detection, revision, and retention over explicit cases.
2. **Causal transportability** gives formal criteria for when conclusions from a source environment can be transported to a target, including recent approximate certificates when exact transfer fails.

The narrower unresolved problem is:

> **Can a foundation-model system learn transfer validity in an open, learned representation space where neither the source case structure nor the target ontology is supplied in advance?**

That is a much stronger and more precise gap.

---

## 1. Case-Based Reasoning is a live neighboring field, not historical background

The 34th International Conference on Case-Based Reasoning (ICCBR 2026, Bremen, 13–16 August 2026) is particularly revealing. Its 36 reviewed papers are explicitly organized around foundations/retrieval, explainable and multimodal CBR, LLM-based CBR, dynamic real-world applications, and workflows/security.

The proceedings contain several papers whose computational questions map almost one-to-one onto the analogical-control pipeline:

- adaptation-guided retrieval;
- failure-aware matching and reuse;
- retrieval-augmented self-reflection;
- LLM-based case adaptation;
- explicit case-based agent memory;
- precedent retrieval + tool-plan adaptation + judgment revision;
- case-based calibration of reasoning/execution.

Barry Smyth's 2026 field analysis describes CBR as a stable translational framework that imports ideas from core AI and exports case-based principles into applied domains, while arguing that the resurgence of retrieval-centric AI creates a major opportunity for renewal.

A 2025 CBR–LLM research manifesto and a separate review of CBR for LLM agents had already framed the integration problem around the classic case cycle of retrieval, adaptation/reuse, revision and learning/retention.

### Consequence for this repo

We should stop treating `retrieval → reuse → revise → retain` as a new decomposition invented by contemporary analogy papers. CBR has treated these transitions as first-class computational objects for decades, and the 2025–26 community is actively rebuilding them around LLMs and agents.

---

## 2. Adaptation-guided retrieval: retrieval should minimize downstream transformation cost

### Sipp & Lieber, ICCBR 2026

**An Adaptation-Guided and Efficient Case Retrieval Approach Based on a Dichotomy of the Case Space**  
Springer chapter: https://link.springer.com/chapter/10.1007/978-3-032-33865-5_3

The retrieval objective is explicitly **adaptation effort**: retrieve the case that can solve the target with minimal subsequent adaptation. The search method recursively partitions the case space and is applied to the general adaptation system Olaaaf.

This is important because it anticipates the same shift seen in 2026 reasoning-aware retrieval:

`semantic similarity / nearest neighbour`

`→ expected downstream usefulness / adaptation cost`.

RA-RFT expresses the criterion as expected reasoning benefit; adaptation-guided CBR expresses it as minimal effort needed to transform the retrieved case into a target solution. They are not identical objectives, but they attack the same interface from two communities.

### Gap implication

G2 `relational retrieval` should be decomposed into:

- **source relevance** — is the source structurally/inferentially useful?
- **adaptation cost** — how much target-specific transformation is required?
- **expected transfer benefit** — after adaptation cost and failure risk, does using the source improve the target outcome?

A useful future retrieval score may need all three rather than similarity alone.

---

## 3. CARM: failure-aware acceptance already implements reject-and-search-more

### Nkisi-Orji, Salimi & Wiratunga, ICCBR 2026

**Failure-Aware Matching-Based Adaptation for Generalisable Reuse**  
Springer chapter: https://link.springer.com/chapter/10.1007/978-3-032-33865-5_4

CARM addresses structured solution reuse across domains. It represents target problems as sets of needs and candidate solutions as graphs of reusable components. Adaptation becomes affinity-driven matching between target needs and candidate components, with cardinality-aware optimization controlling constructed solution size.

The critical control step is **failure-aware acceptance**:

`retrieve cases`

`→ match/recombine components`

`→ construct candidate solution`

`→ accept if adequate`

`→ otherwise expand the retrieval neighbourhood and rematch`.

The framework is evaluated on two structurally different domains, MultiWOZ task-oriented dialogue and O*NET occupation data. Its significance for this repo is conceptual: failure is not merely a final score. It is a signal that changes the next retrieval/adaptation action.

Earlier work by the same research line on failure-driven transformational reuse already used an acceptance threshold to expand the neighbourhood and rematch when a constructed explanation strategy was inadequate.

### Gap implication

The statement `rejection/control is absent` is too broad.

What remains absent from mainstream foundation-model analogy is a **learned open-world version** of CARM's control logic where:

- source and target are not already encoded in a shared explicit schema;
- target needs/components must be induced from raw language, vision, or mixed evidence;
- the failure criterion itself may be uncertain;
- rejection must decide whether to search farther, rerepresent the target, remap, or abandon analogy entirely.

---

## 4. CAST: cases can calibrate reasoning depth and predicted failure modes

### Pang et al., ICCBR 2026

**Case-Based Calibration of Adaptive Reasoning and Execution for LLM Tool Use**  
Preprint: https://arxiv.org/abs/2605.15041

CAST treats historical execution trajectories as structured cases. Rather than copying whole outputs, it extracts:

- **complexity profiles**, used to estimate an appropriate reasoning strategy;
- **failure profiles**, used to predict likely structural breakdowns.

These case-derived signals are translated into fine-grained reward design and adaptive reasoning during reinforcement learning. On BFCLv2 and ToolBench, the paper reports up to **+5.85 percentage points** in overall execution accuracy while reducing average reasoning length by **26%**.

### Gap implication

Failure memory can already do more than retrieve past mistakes. It can shape the **control policy before execution**.

For analogical reasoning, the analogous target would be a source–target applicability profile such as:

`source family S`

`+ target relational condition X`

`→ likely failure mode F`

`→ down-weight transfer / request additional evidence / search another source / change representation`.

---

## 5. Causal transportability: transfer validity has a formal theory

CBR supplies procedural control over explicit cases. Causal transportability supplies a different resource: formal criteria governing when source conclusions are valid in a target environment.

### Felekis et al., 16 August 2026

**Generalised Transportability via Causal Abstractions**  
Preprint: https://arxiv.org/abs/2608.15645

Classical transportability asks whether a target causal query is identifiable from source experiments plus target observations. This paper moves to a **model-level** formulation grounded in causal abstraction.

Source and target share variables, graph, and interventions while differing at known mechanisms. The system asks whether a map aligns source and target across interventional behaviour.

- If an exact map exists, every target query transports at once.
- If no exact map exists, the best approximate map yields **certified query intervals**.
- The framework explicitly treats non-transportable and target-agnostic regimes rather than returning only a binary success/failure.

This is remarkably close to what analogical adjudication ultimately needs at the epistemic level:

`how much of source structure can be trusted in the target, and with what uncertainty?`

### 2025 transfer-learning bridge

Work on **Transfer Learning through Causal Transportability** already uses transportability criteria to avoid negative transfer in source-to-target decision problems. This reinforces the point that source applicability is not merely a similarity problem; it can be expressed in terms of invariant/changed causal mechanisms.

### Gap implication

G3 and G8 should be linked:

- **G3** is not only `reject bad analogy`; it is `estimate transfer applicability`.
- **G8** is not only generic confidence; it is `quantify uncertainty over the transferred inference`.

The strongest future system would produce something richer than `analogy yes/no`:

`source mapping M is usable for target claims Q1,Q2`

`but not Q3`

`with confidence/bounds determined by the mechanisms that differ`.

---

## 6. Safe in-context learning: harmful source cases can be risk-controlled

**Wynn et al., Safe and Efficient In-Context Learning via Risk Control** (ICLR 2026 submission) provides another adjacent primitive. The system treats incorrect or malicious demonstrations as potentially harmful inputs and uses distribution-free risk control plus dynamic early exit to limit how far in-context examples can degrade performance below a zero-shot baseline, while preserving gains from helpful examples.

OpenReview: https://openreview.net/forum?id=tCjYJ01Jbk

This is not an analogy system and does not test structural transfer validity. It nevertheless demonstrates a useful design principle:

> source experience should be admitted conditionally, under an explicit risk budget, rather than assumed to be beneficial because it was retrieved.

For analogical reasoning, the harder equivalent is to estimate risk from **misleading structural transfer**, not adversarial demonstration labels.

---

# Three communities, three different assumptions

| Community | Source representation | Target representation | Transfer-control mechanism | Main strength | Main assumption that open-world analogy cannot rely on |
|---|---|---|---|---|---|
| **LLM analogical reasoning** | usually raw/generated text or benchmark-provided source | learned/raw target | mostly prompting, learned retrieval, structural alignment, agent scaffolds | flexible representation and generation | transfer validity often weakly specified |
| **Case-Based Reasoning** | explicit structured cases / problem–solution records | explicit query/problem representation | retrieve–adapt–revise–retain; adaptation/failure logic | reusable experience and adaptation control | shared case schema / engineered or learnable adaptation structure |
| **Causal transportability** | SCM / causal mechanisms | SCM / target mechanisms | identifiability, transport maps, approximate certificates | formal transfer validity and uncertainty | causal variables/graph/interventions substantially specified |

The open frontier sits at the intersection:

`foundation-model representation flexibility`

`+ CBR-style adaptation/revision control`

`+ transportability-style validity and uncertainty`.

---

# Refined statement of the core gap

The most defensible formulation is now:

> **Open-world learned transfer validity:** given raw or weakly structured source and target information, autonomously construct candidate relational representations, estimate which source structure is reusable, adapt/rebind it, reject invalid transferred inferences, quantify residual uncertainty, and use failure evidence to decide whether to retrieve farther, remap, rerepresent, or abandon the analogy.

This contains several subproblems:

1. **Endogenous representation** — source/target relational variables are learned, not supplied.
2. **Adaptation-aware retrieval** — retrieve by expected reusable value after transformation cost.
3. **Partial transfer** — accept some mapped relations while vetoing others.
4. **Failure localization** — decide whether failure came from source selection, representation, mapping, adaptation, execution, or target mismatch.
5. **Action after failure** — search wider, change representation, remap, or abstain.
6. **Calibrated validity** — attach uncertainty/bounds to projected claims.
7. **Retention** — store successful and failed transfer boundaries for future retrieval/control.

No current general foundation-model system found in this sweep demonstrates all seven across heterogeneous open domains.

---

# What this changes in the repo

The phrase **“plausible-analogy rejection is an orphan gap”** should be treated as shorthand only. More precisely:

- rejection/failure-aware reuse has a clear owner in CBR;
- source-to-target validity has a mature formal owner in causal transportability;
- generic abstention has a growing owner in selective-prediction/RL research;
- what remains comparatively orphaned is **their integration with learned, open-world relational representations and analogical source search in foundation models**.

That is the gap worth monitoring and, eventually, testing directly.
