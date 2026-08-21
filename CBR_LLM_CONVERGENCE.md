# CBR–LLM Convergence — Why the Old “Structured Cases vs Flexible Foundation Models” Contrast Is Collapsing

**Snapshot: 21 August 2026.**

The repository originally used a useful contrast:

- foundation models are strong at flexible, endogenous representation but weak at disciplined case reuse;
- classical Case-Based Reasoning (CBR) is strong at `retrieve → reuse/adapt → revise → retain` but usually assumes clearer case structure.

The contrast is now becoming too sharp. Work in 2025–26 is rapidly **neuralizing CBR itself**: LLMs perform similarity assessment and adaptation; case-selection policies are learned from reward; case memories store abstract correction operators rather than raw examples; successful deployment interactions rewrite future retrieval policy.

The remaining distinction is therefore narrower:

> **Modern CBR is learning flexible case selection/adaptation, but it still rarely represents and certifies source→target transfer at the level of open, induced relational correspondences.**

---

## 1. ICCBR 2026 shows that LLM–CBR is now a central program

The 34th ICCBR, held in Bremen on 13–16 August 2026, contains 36 reviewed papers and a full section titled **LLM-Based CBR: Prompting, Adaptation, and Generation**. The proceedings also contain work on multimodal case reasoning, retrieval, failure-aware reuse, explicit agent memories, strategic negotiation, tool-plan adaptation and judgment revision.

Proceedings: https://link.springer.com/book/10.1007/978-3-032-33865-5

This is not a marginal revival. The contemporary CBR community is explicitly treating LLMs as components that can implement or learn parts of the case cycle.

---

## 2. Keep Adaptation Simple — explicit decomposition can make reuse worse

### Regulagedda, Krupashankar & Leake, ICCBR 2026

**Keep Adaptation Simple: Implicit vs. Explicit Adaptation for LLM-Based CBR**

The paper compares architectures along two axes:

- multi-stage retrieval vs a unified LLM retrieval process;
- explicit adaptation vs implicit/minimal adaptation.

Explicit adaptation decomposes reuse into separate stages: extract a solution approach, construct a new reasoning chain for the target, run error analysis, then answer. Implicit adaptation simply provides the retrieved case to the solver and lets the LLM adapt internally.

The striking result is negative: across the tested mathematical reasoning settings, **explicit multi-stage adaptation consistently degrades performance**, while unified retrieval with minimal adaptation performs strongly for sufficiently large models. The authors' failure analysis over hundreds of cases attributes many failures to **compounding stage errors**: each stage treats the predecessor's transformed output as authoritative instead of repeatedly grounding itself in the original target problem.

Available manuscript: https://ravimaithrey.com/research/keeping-adaptation-simple.pdf

### Consequence for analogical control

The lesson is not “avoid explicit control”. It is more precise:

> **separate control variables from repeated lossy natural-language transformations.**

A future analogical controller may benefit from explicit state variables such as applicability, binding, uncertainty, or failure type while keeping much of representation/adaptation latent or jointly optimized. A pipeline with nine independent LLM prose stages could be *less* reliable than a smaller shared-state controller.

This creates a design tension the repo should track:

`interpretability / modular diagnosis`

vs

`error propagation from repeated explicit transformations`.

---

## 3. TextBFGS — retrieve operators, not raw cases

### Zhang et al., 2026 / ICCBR 2026

**TextBFGS: A Case-Based Reasoning Approach to Code Optimization via Error-Operator Retrieval**  
Canonical preprint: https://arxiv.org/abs/2602.00059

TextBFGS moves beyond nearest-example reuse. It maintains a dynamic memory of successful **error/gradient → correction-operator** trajectories. Given new textual feedback, it retrieves historical abstract correction patterns and applies the resulting operator to the current program/text. Successful adaptations are retained back into memory.

Operationally:

`current error signal`

`→ retrieve historical correction operator`

`→ adapt operator to current object`

`→ execute / evaluate`

`→ retain successful operator trajectory`.

The paper reports improved code-optimization pass rates with fewer model calls and strong cross-task transfer relative to stateless first-order baselines.

### Why it matters for analogy

TextBFGS is much closer to **schema/operator retrieval** than ordinary CBR. The reusable unit is not the source case's surface content but a transformation abstracted from past failures.

That directly attacks a key analogical target:

`retrieve the transformation that worked in an analogous failure state`,

rather than

`retrieve a semantically similar previous problem`.

Its domain is still executable text/code, where feedback is unusually clear and verification cheap. But the architectural principle is important.

---

## 4. Memento — learned case selection as continual agent policy

### Zhou et al., 2025

**Memento: Fine-tuning LLM Agents without Fine-tuning LLMs**  
Canonical: https://arxiv.org/abs/2508.16153  
Code: https://github.com/Memento-Teams/Memento

Memento formulates memory-based continual adaptation as a **memory-augmented MDP**. A CBR planner reads and writes episodic cases, while a neural case-selection policy learns which past experiences are useful. A separate executor acts through tools.

The important distinction from static RAG is that retrieval itself becomes a learned policy. The case bank changes over time and the Q-function can be updated from experience without changing the underlying LLM weights.

This is already close to a general `reason from past successful trajectories` controller for long-horizon agents.

### Remaining analogy-specific weakness

The learned value is attached mainly to whole cases/plans. It does not explicitly represent:

- which relational correspondence made a case transferable;
- which part of a source should be vetoed;
- which failed binding should become a negative applicability boundary;
- how to assign failure to representation vs mapping vs projection.

---

## 5. CASCADE — deployment-time case learning with contextual-bandit guarantees

### Guo et al., 2026

**CASCADE: Case-Based Continual Adaptation for Large Language Models During Deployment**  
Canonical: https://arxiv.org/abs/2605.06702  
Code: https://github.com/guosyjlu/CASCADE

CASCADE formalizes deployment-time learning as an online case-reuse problem. It uses a fixed embedding stage for broad recall and an online contextual-bandit reranker to learn **expected case utility** from binary environmental feedback. Successful interactions enter the case bank; the retrieval policy improves over deployment time.

Across 16 tasks spanning medicine, legal analysis, code, search, tool use and embodied interaction, the paper reports a 20.9% macro-averaged success improvement over zero-shot prompting and provides no-regret guarantees for its online retrieval formulation.

### Why this narrows the frontier gap

A previously plausible claim was:

`LLM systems do not continually learn which past cases transfer.`

CASCADE makes that claim untenable.

The sharper missing capability is:

`LLM systems do not yet reliably learn *why* a case transfers at the relational level and use that diagnosis to support partial transfer, negative applicability memory, and rerepresentation.`

---

## 6. What modern CBR already covers

| Capability | 2026 CBR/LLM status |
|---|---|
| semantic / learned case retrieval | strong and active |
| retrieval by downstream adaptation utility | active |
| failure-aware reject-and-search-more | demonstrated |
| LLM-based implicit adaptation | demonstrated |
| explicit adaptation and verification | demonstrated, with error-propagation caveats |
| abstract operator retrieval | demonstrated in TextBFGS |
| learned deployment-time case-selection policy | demonstrated in Memento/CASCADE |
| successful-case retention | standard / demonstrated |
| multimodal and agent case memory | active |
| negative/failure case reuse | active but heterogeneous |

What remains relatively weak is **relation-level transfer bookkeeping** under representations that the model invents on the fly.

---

## 7. Revised convergence picture

Instead of three cleanly separated traditions, the current landscape looks like three **converging capabilities**:

### Foundation-model reasoning

Strength:

`raw language / image → flexible latent representation → generation`.

### Modern neural CBR

Strength:

`experience → learned retrieval → adaptation/reuse → reward/failure → retention`.

### Causal abstraction / transportability

Strength:

`source model ↔ target model → invariance / discrepancy → licensed query transfer + uncertainty`.

The frontier is their overlap:

`raw open-world cases`

`→ induced relational representations`

`→ utility/adaptation-aware retrieval`

`→ source-target binding`

`→ claim-level transfer validity`

`→ execution / evidence`

`→ relational failure attribution`

`→ applicability memory + rerepresentation`.

---

## 8. Design implication: the controller probably should not be a long chain of prose modules

The ICCBR adaptation result is a useful architectural warning. The repository's conceptual decomposition remains necessary for measurement, but **measurement decomposition does not imply inference-time implementation must use a separate LLM call for every stage**.

A plausible system may instead combine:

- shared latent/structured state for relation and binding variables;
- learned retrieval and source utility scores;
- compact explicit validity/uncertainty heads;
- tools/environment for verification;
- sparse routing only when failure is detected;
- persistent case/operator memory.

This would preserve diagnosability without repeatedly rewriting the whole problem through a brittle sequence of natural-language transformations.

That is now a stronger engineering hypothesis than “build a fully explicit nine-stage analogy agent.”
