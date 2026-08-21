# Adjacent Fields — Work Solving Analogical Gaps Without Calling It Analogy

This note tracks neighboring research programs whose papers often do **not** use `analogy` in the title, but directly attack capability gaps identified in `GAP_MAP.md`. The purpose is to avoid a vocabulary trap: important progress on analogical intelligence may arrive through information retrieval, abstention/control, program induction, visual abstraction, or agent memory.

The organizing question is not whether a paper self-identifies as analogy research. It is:

> **Does the method solve a computational subproblem that an end-to-end analogical system must solve?**

---

## 1. Reasoning-intensive retrieval → G2 relational retrieval at scale

### Field shift

The information-retrieval community is explicitly moving beyond lexical/semantic relevance toward **inferential relevance**: a document or example is useful because it supports a reasoning process, even when surface similarity is weak.

### BRIGHT — reasoning-intensive retrieval becomes a benchmark problem

**Su et al., BRIGHT, ICLR 2025.**  
Paper: https://proceedings.iclr.cc/paper_files/paper/2025/hash/7a0f8055c838df8e62329a76c7c6403d-Abstract-Conference.html  
Project/code: https://github.com/xlang-ai/BRIGHT

BRIGHT contains roughly 1.4K real-world queries across domains including economics, psychology, mathematics, robotics, coding, and science. A leading general retrieval model that scored around 59 nDCG@10 on MTEB fell to roughly 18 on BRIGHT; explicit query reasoning improved retrieval by as much as 12.2 points.

**Why it matters for analogy.** This is almost the exact retrieval transition required by far analogy:

`semantic similarity relevance → latent inferential relevance`.

BRIGHT is not an analogy benchmark, because relevant documents need not instantiate source–target mappings. But it demonstrates that ordinary embedding similarity is structurally inadequate for cases in which relevance depends on an unstated reasoning bridge.

### Reasoning-Intensive Retrieval becomes a named field

**Wei et al., “A Survey of Reasoning-Intensive Retrieval: Progress and Challenges,” ACL 2026.**  
Canonical: https://aclanthology.org/2026.acl-long.1949/

The survey defines RIR as retrieval where relevance is mediated by **latent inferential links** rather than semantic similarity, and organizes work across benchmarks, retrievers, rerankers, and reasoning-integrated pipelines.

**Calibration.** G2 should no longer be described as an isolated analogy-specific gap. It overlaps with a rapidly crystallizing IR subfield.

### RA-RFT — retrieve by expected reasoning benefit

**Xiao et al., “Learning to Reason by Analogy via Retrieval-Augmented Reinforcement Fine-Tuning,” 2026.**  
Canonical: https://arxiv.org/abs/2606.13680

RA-RFT trains a retriever to rank examples by **expected reasoning benefit rather than semantic overlap**, then reinforcement-fine-tunes the policy with retrieved reasoning traces. On AIME 2025 it reports average@32 gains of +7.1 and +2.8 points over GRPO for Qwen3-1.7B and Qwen3-4B.

This is the strongest current bridge from RIR back into explicit analogy research. It changes the retrieval objective itself.

### UR² / adaptive retrieval — reasoning and retrieval become one policy

**Li et al., UR², ACL 2026.**  
Canonical: https://aclanthology.org/2026.acl-long.580/

UR² jointly optimizes retrieval and reasoning under reinforcement learning rather than treating retrieval as a fixed preprocessing stage.

**Guo et al., ReaLM-Retrieve, 2026.**  
Canonical: https://arxiv.org/abs/2604.26649

ReaLM-Retrieve learns **when** retrieval should intervene during a reasoning trajectory, using step-level uncertainty rather than retrieving only before reasoning begins.

### Remaining gap

RIR is solving `which evidence/example helps reasoning?`, but analogical retrieval requires a stronger criterion:

`which source has transferable relational/mechanistic structure for this target?`

The field is converging on reasoning utility, but general-purpose structural-reuse metrics remain immature.

**Updated status for G2:** `OPEN → ACTIVE ENGINEERING FRONTIER`.

---

## 2. Abstention and selective prediction → G3 matching / rejection / veto

### Why this neighboring field is unusually diagnostic

Analogical adjudication requires the system to say:

`I can construct a plausible mapping, but I should not rely on it.`

The abstention literature reveals an almost identical control failure in ordinary reasoning: models may internally recognize that a problem is invalid or underspecified, yet still continue reasoning and emit a confident answer.

### AbstentionBench — reasoning training can make refusal worse

**Kirichenko et al., AbstentionBench, NeurIPS 2025.**  
Canonical: https://arxiv.org/abs/2506.09038  
Code: https://github.com/facebookresearch/AbstentionBench

Across 20 frontier models and 20 datasets, abstention remains unsolved. A particularly important result is that **reasoning fine-tuning degrades abstention by about 24% on average**. Scaling alone has little effect.

**Implication for analogy.** Better generative reasoning can strengthen the model's ability to elaborate a bad analogy without strengthening the policy that decides whether the analogy should be used.

### Detection-to-action gap

**Liu et al., “Answering the Unanswerable Is to Err Knowingly,” AAAI 2026.**  
Canonical: https://ojs.aaai.org/index.php/AAAI/article/view/40496

The authors show that large reasoning models can often recognize flaws in unanswerable questions while failing to translate that recognition into abstention. A monitoring/intervention layer substantially repairs behavior.

**Gu et al., “Bridging the Detection-to-Abstention Gap…,” 2026.**  
Canonical: https://doi.org/10.48550/arXiv.2605.28070

This work explicitly treats answerability judgment and reasoning continuation as separate control decisions.

This distinction maps directly onto analogy:

`detect mismatch ≠ veto transfer`.

### Abstention can be trained as a policy

**Zhai et al., Abstain-R1, Findings ACL 2026.**  
Canonical: https://aclanthology.org/2026.findings-acl.985/

A clarification-aware RLVR objective jointly rewards correct answers, explicit abstention, and correct identification of missing information. A 3B model becomes competitive with much larger reasoning systems on unanswerable-query behavior while retaining answerable-task performance.

### Remaining gap

Generic abstention asks whether a problem is answerable. Analogical adjudication is harder: the target itself may be answerable, and the candidate analogy may be highly coherent, yet **one transferred inference is invalid**.

A dedicated analogy-veto benchmark still needs hard negatives of the form:

`high semantic plausibility + high partial structural fit + transfer-invalid difference`.

It should also permit `no useful analogy` as a first-class output.

**Updated status for G3:** still `OPEN`, but the likely engineering machinery already exists in neighboring selective-control research.

---

## 3. Program / rule / operator induction → G4 novel-operation generalization

### The important distinction

Many analogy benchmarks call something “novel” when only the symbols or operands change. The harder problem is:

`infer an operator never instantiated during training, then execute it compositionally`.

Several adjacent communities now isolate this explicitly.

### Compositional-ARC — new compositions are learnable with the right training regime

**Mondorf et al., Compositional-ARC, ICLR 2026.**  
Canonical: https://iclr.cc/virtual/2026/poster/10008090

A 5.7M-parameter encoder–decoder trained with meta-learning for compositionality generalizes from known transformations to unseen **combinations** of transformations and substantially outperforms o3-mini, GPT-4o, and Gemini 2.0 Flash in the reported setup.

**Important limit.** This demonstrates systematic recombination of known primitives, not unconstrained invention of new primitives.

### Novel Operator Test — operator knowledge and output control dissociate

**Rao et al., “Correct Chains, Wrong Answers,” 2026.**  
Canonical: https://arxiv.org/abs/2604.13065

The benchmark renames Boolean operators and tests deep compositions. It finds cases where models produce correct intermediate reasoning yet wrong declared outputs, separating operator reasoning from final answer production.

This reinforces a general pattern: representation/execution/control must be separately evaluated.

### Zero-shot logical rule induction

**Phua, “A Foundation Model for Zero-Shot Logical Rule Induction,” 2026.**  
Canonical: https://arxiv.org/abs/2605.04916

The Neural Rule Inducer represents predicates through domain-agnostic statistical properties rather than predicate identity, enabling zero-shot transfer across variable identities and task settings without retraining.

This is relevant because it explicitly tries to make rule induction independent of surface vocabulary.

### BDH-CQ — previously unseen visual transformations learned from demonstrations

**Engdahl et al., BDH-CQ, 10 Aug 2026.**  
Canonical: https://arxiv.org/abs/2608.09888

A 150M recurrent latent-reasoning model conditions its memory on task demonstrations and solves queries through iterative latent computation. It reaches 29.5% pass@2 on ARC-AGI-1 at a reported computed cost of $0.00070/task. The paper frames the acquired behavior as a **demonstration-conditioned operator schema**: demonstrations bind a reusable visual operation for the current task without parameter updates at inference time.

Controlled analysis still finds difficult concepts including ordering, nesting, conditional rule selection, unseen parameter values, and composition. This makes BDH-CQ particularly important for G4: it is a serious positive result on in-context operator induction, while clearly exposing remaining limits.

### Remaining gap

We should split G4 into two sub-gaps:

- **G4a — unseen composition:** recombine known primitives in new configurations. Rapidly improving; specialised meta-learning can do this well.
- **G4b — unseen primitive/operator induction:** infer a genuinely new relational operation from sparse examples and deploy it robustly. Still much harder.

**Updated status:** `G4a = PARTLY SOLVED under specialised training`; `G4b = OPEN`.

---

## 4. Object-centric / neuro-symbolic visual reasoning → G1 + G5

### OCRA — perception and relational abstraction must both be explicit

**Webb, Mondal & Cohen, “Systematic Visual Reasoning through Object-Centric Relational Abstraction,” NeurIPS 2023.**  
Canonical: https://arxiv.org/abs/2306.02500

OCRA combines object-centric representation learning with explicit relational abstraction and obtains systematic generalization on abstract visual tasks. The important architectural lesson is that relational reasoning cannot simply assume clean objects are already supplied.

### CARV — composition exposes decomposition failure

**Du et al., CARV, 2026.**  
Canonical: https://arxiv.org/abs/2603.27958

CARV extends visual analogy from a single source pair to multiple source pairs whose rules must be extracted and composed. On 5,500 samples, Gemini-2.5 Pro reaches 40.4% while the reported human baseline is 100%. The main diagnosed failures are symbolic decomposition of visual changes and robustness under complex settings.

### I-RAVEN-X — uncertainty breaks reasoning despite more test-time compute

**Camposampiero et al., I-RAVEN-X, 2025/26.**  
Canonical: https://arxiv.org/abs/2510.17496

The benchmark increases rule length, operand/attribute complexity, and perceptual uncertainty. Reasoning models improve on some longer symbolic relations but remain highly vulnerable to uncertain perception and cannot robustly explore multiple probabilistic interpretations.

### Compositional neuro-symbolic ARC systems

**Das et al., “Compositional Neuro-Symbolic Reasoning,” 2026.**  
Canonical: https://arxiv.org/abs/2604.02434

The system explicitly separates object extraction, neural transformation proposal, and symbolic cross-example consistency filtering. On ARC-AGI-2 public evaluation it reports improving a base LLM from 16% to 24.4%, and 30.8% when combined with another solver.

### Remaining gap

The key unsolved interface is:

`uncertain perception → multiple candidate object/relational decompositions → rule induction → composition → consistency-based selection`.

Most language-model analogy benchmarks start **after** this hard representation problem has been solved for the model.

**Updated status for G1/G5:** open, with strong evidence that modular/object-centric representations and explicit consistency filtering outperform pure end-to-end generation on selected tasks.

---

## 5. Agent trajectory memory → G10 continual analogical memory and post-retrieval reuse

This neighboring line was not in the original four-gap sweep, but it is directly relevant once analogy becomes an agent capability rather than a benchmark answer.

### Agent Workflow Memory

**Wang et al., Agent Workflow Memory, ICML 2025.**  
Canonical: https://proceedings.mlr.press/v267/wang25bx.html

AWM induces reusable workflows from past trajectories and retrieves them for future tasks. It reports substantial gains on Mind2Web and WebArena, including stronger cross-task/domain transfer.

### Retrieval is not reuse

**Li et al., “Beyond Retrieval: Query-Conditioned Reuse of Long-Horizon Agent Trajectories,” Aug 2026.**  
Canonical: https://arxiv.org/abs/2608.12847

This work isolates **post-retrieval reuse** as its own bottleneck. With retrieval held fixed, query-conditioned reusable notes outperform direct full-trajectory injection; across 2,391 target instances the reported average success is 62.3%, +10.7 points over full trajectories, using 48.9% fewer online tokens.

The reusable representation explicitly records procedure, bindings, applicability conditions, and verification requirements.

**Why it matters for analogy.** Even after finding a good source episode, a system still has to decide:

- which parts are invariant;
- which bindings must change;
- under what conditions the source procedure applies;
- how the transferred procedure should be verified.

That is almost exactly the post-mapping transfer problem in operational form.

### Remaining gap

Current agent memory predominantly learns from successful workflows and task trajectories. A mature analogical memory should also store **failed transfers and applicability boundaries**, so previous mistakes reduce future false-positive analogies rather than merely adding more cases to retrieve.

**Updated status for G10:** `EARLY → ACTIVE adjacent field`.

---

# Cross-field synthesis: the same missing layer keeps reappearing

These adjacent communities independently decompose their problems in strikingly similar ways:

| Community | Old simplification | New explicit bottleneck |
|---|---|---|
| Retrieval | retrieve semantically similar context | retrieve context with expected reasoning utility |
| Abstention | model either knows or does not know | detection and action/control can diverge |
| Program induction | solve familiar rules | infer/recombine operators, then execute them |
| Visual reasoning | end-to-end pixels → answer | object representation → rule proposal → consistency filter |
| Agent memory | retrieve a past trajectory | decide what is reusable, rebind it, check applicability, verify |

This suggests that the next important abstraction for analogical AI may be a **control architecture** rather than another mapping module.

A candidate end-to-end control loop is:

`construct candidate representations`

`→ search memories/sources by reasoning utility`

`→ infer candidate correspondences/operators`

`→ score applicability and uncertainty`

`→ reject or select`

`→ transfer with target-specific rebinding`

`→ execute / test`

`→ verify outcome`

`→ store success AND failure boundary`

`→ update future retrieval and selection`

No current general system closes this loop robustly across domains.

---

# Revised research priorities

## Priority A — build a real adjudication benchmark

This remains the least occupied high-value gap. Borrow from abstention/selective prediction, but design candidate analogies whose problem is **transfer validity**, not answerability.

Required properties:

- hard positive and hard negative source cases;
- high partial structural similarity;
- controlled inference-critical mismatch;
- explicit `no useful analogy` option;
- precision/recall/calibration, not accuracy alone;
- separate scoring for detection of the mismatch and actual veto behavior.

## Priority B — evaluate retrieval by downstream transfer utility

Use the RIR lesson: similarity is only a proxy. A source should be scored by whether it improves the target reasoning/solution under controlled budgets.

## Priority C — split “novel generalization” into composition vs operator induction

Every paper should be coded for:

- new operands;
- new symbol system;
- new composition of known operators;
- unseen operator with examples;
- unseen operator with noisy/ambiguous examples.

## Priority D — treat source reuse as a first-class stage

After retrieval/mapping, evaluate whether the model correctly rewrites source-specific bindings and conditions before transfer.

## Priority E — add negative memory

Track whether systems store failed analogies / failed trajectories and whether this improves later precision rather than merely recall.
