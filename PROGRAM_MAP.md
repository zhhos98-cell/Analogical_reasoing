# Program Map — Who Is Actually Building What?

This map groups the contemporary field by **research program**, not by prestige or by use of the word `analogy`. A program counts as mature when the same researchers or closely linked group move across multiple steps — benchmark, mechanism, architecture, training, or application — rather than publishing one isolated analogy paper.

The purpose is to answer two practical questions:

1. Which gaps already have a sustained research community behind them?
2. Which apparently important gaps still lack a clear “owner” or program?

---

## 1. Relational architecture program — Abstractor → relational bottleneck → Dual Attention / object-centric abstraction

**Core researchers:** Awni Altabaa, John Lafferty, Taylor Webb, Jonathan D. Cohen and collaborators across Yale, UCLA, Princeton and related groups.

Key sequence:

- **Abstractors / relational cross-attention** — ICLR 2024;
- **The relational bottleneck as an inductive bias for efficient abstraction** — TiCS 2024;
- **Dual Attention Transformer (DAT)** — ICML 2025;
- connected visual work such as **OCRA** on object-centric relational abstraction.

### What this program has established

This is probably the clearest architecture-level program in the field. Its thesis is that standard attention is well suited to routing sensory/object information but lacks an explicit mechanism for routing relational information. Abstractors and DAT therefore build relation-specific computational channels rather than expecting generic Transformers to discover them entirely through scale.

The important progression is:

`relational inductive bias as idea`

`→ explicit relational cross-attention`

`→ sensory/relational channel separation and integration`

`→ language/vision and broader task evaluation`.

### Frontier position

Strongest on **representation / relation extraction / architectural inductive bias**. It provides a plausible substrate for G1 and G5 and contributes to far generalization.

### Missing from this program

- autonomous source retrieval;
- candidate analogy adjudication / rejection;
- episodic analogical memory;
- multi-turn analogy control policy;
- open-world validation.

### Program maturity

**HIGH.** Multiple papers, explicit architectural thesis, code/model artifacts, cross-modal expansion.

### Why watch it

If analogical reasoning eventually becomes a standard neural primitive rather than a prompt strategy, this family is one of the strongest candidates for the architectural substrate.

---

## 2. Human-generalization / cognitive evaluation program — University of Amsterdam + Melanie Mitchell / Santa Fe Institute

**Core researchers:** Claire E. Stevenson, Han L. J. van der Maas, Melanie Mitchell, collaborators including Alexandra Pafford, Tamar Johnson, Molly Petersen, Lonneke van der Plas.

Key sequence:

- verbal analogy comparisons between children and LLMs;
- counterfactual / unfamiliar-domain analogy transfer;
- **Can Large Language Models Generalize Analogy Solving Like Children Can?** — TACL 2026;
- **Modelling Analogies and Analogical Reasoning: Connecting Cognitive Science Theory and NLP Research** — TACL 2026.

### What this program has established

This program is unusually good at separating **high benchmark accuracy** from robust transfer. Its experiments ask whether a learned analogy procedure survives surface recoding and domain change, rather than accepting familiar-domain performance as evidence of general abstraction.

The important diagnostic hierarchy is:

`same task / familiar representation`

`→ new alphabet / near transfer`

`→ unfamiliar symbols / far transfer`.

Children and adults remain more robust across these transitions than tested LLMs.

### Frontier position

Strongest on **behavioral diagnosis, human comparison, benchmark validity, and far procedural generalization (G4)**.

### Missing from this program

This is primarily a diagnostic/evaluation program rather than a large-scale architecture or post-training program. Its work tells the engineering community what must be explained and what superficial successes do not count as robust analogy.

### Program maturity

**HIGH as an evaluation/cognitive program; LOW–MEDIUM as an engineering program.**

### Why watch it

This group is likely to continue generating the cleanest “does this really transfer?” tests against which new engineering claims should be calibrated.

---

## 3. Relational mechanistic interpretability — Korea University / AIGEN Sciences / DMIS

**Core researchers:** Taewhoo Lee, Minju Song, Chanwoong Yoon, Jungwoo Park, Jaewoo Kang.

Anchor paper:

- **The Curious Case of Analogies: Investigating Analogical Reasoning in Large Language Models** — AAAI 2026.

### What this line has established

The work uses attention knockout, probes, representation patching, and story analogies to separate several failure modes that behavior-only evaluation collapses together:

- relational information missing from the internal state;
- relation encoded but not correctly applied to new entities;
- structural alignment degraded or misplaced.

This is important because it turns analogical reasoning from a scalar score into a **causal/mechanistic decomposition**.

### Frontier position

Strongest on **internal relation representation, information flow, structural alignment and representation intervention**.

### Missing / uncertain

At present this is best treated as a **strong emerging line**, not yet a long multi-paper analogy program. The obvious next move would be intervention studies on rejection, source selection, or far transfer rather than supplied-source mapping alone.

### Program maturity

**MEDIUM / emerging.** One major dedicated paper with full reproducibility code; worth watching for follow-ups.

---

## 4. Causal / active reasoning / AI-scientist control — CLeaR line around Yongqiang Chen and Kun Zhang

**Core researchers:** Yongqiang Chen, Kun Zhang and collaborators; current work spans the Causal Learning and Reasoning (CLeaR) group and collaborators at MBZUAI / Carnegie Mellon and elsewhere.

Relevant sequence is broader than analogy:

- causal discovery/reasoning with LLMs;
- active-reasoning reinforcement learning;
- **Information Self-Locking** — search/action selection coupled to belief tracking;
- work on belief deviation / active reasoning;
- **Analogical Deep Research / CANA** — mechanism-based source retrieval plus cross-analogy confirmation.

### What this program has established

This is perhaps the most interesting **systems-level neighboring program** because its pieces already correspond to multiple columns in the analogical control loop:

`acquire information`

`→ maintain/update belief`

`→ represent latent mechanisms`

`→ retrieve mechanism-level analogues`

`→ reject/filter`

`→ cross-confirm several sources`.

The group explicitly frames its broader goal around reliable AI scientist agents, long-horizon reasoning, hypothesis generation, belief updating and recursive improvement.

### Frontier position

Strong on **G2 retrieval, G9 active validation/belief update, G11 multi-analogy integration**, and increasingly G1 representation.

### Missing

- learned general analogy-veto policy;
- persistent source–target applicability memory;
- explicit failure credit assignment across representation/retrieval/mapping/projection;
- domain-general independence estimation for cross-analogy evidence.

### Program maturity

**HIGH as an active/causal agent program; MEDIUM as a specifically analogical program.**

### Why watch it

Among current groups, this line may be closest to turning analogical reasoning into one component of a larger **epistemic agent controller** rather than treating analogy as an isolated benchmark.

---

## 5. Analogical search for AI for Science — Stanford (Shen / Druckmann / Zou)

**Core researchers:** Andrew Shen, Shaul Druckmann, James Zou, Stanford University.

Anchor paper:

- **Unlocking LLM Creativity in Science through Analogical Reasoning** — 2026.

### What this program has established

It treats analogy as a **search operator** for open-ended scientific problem solving rather than a cognitive benchmark. The pipeline generates cross-domain problems sharing relational structure and repurposes solutions back into the target domain.

Reported effects include:

- solution-diversity metrics improved by 90–173%;
- novel solutions generated over 50% of the time versus as little as 1.6% for baselines;
- quantitative implementation/validation across four biomedical problem families.

### Frontier position

Strong on **G6 diversity without quality collapse** and the practical side of **G9 open-world discovery/validation**.

### Missing

The current system demonstrates that analogy expands a useful scientific search space. It does not yet establish a generic autonomous controller that knows:

- when analogy should be invoked;
- which candidate analogy deserves epistemic commitment;
- when a transfer should be rejected;
- how failed experiments should update future source selection and relational representation.

### Program maturity

**MEDIUM / high-value application line.** Strong real-world validation, but currently anchored by one major analogy paper.

### Why watch it

This may become economically/scientifically important before general human-like analogy is solved. Analogy can be valuable as controlled diversity generation even with imperfect epistemic reliability.

---

## 6. Reasoning-aware retrieval + post-training — Meta / Rice RA-RFT line

**Core researchers:** Zilin Xiao, Qi Ma, Chun-cheng Jason Chen, Xintao Chen, Avinash Atreya, Hanjie Chen, Vicente Ordonez; paper affiliation includes Meta Superintelligence Labs and Rice University.

Anchor paper:

- **Learning to Reason by Analogy via Retrieval-Augmented Reinforcement Fine-Tuning (RA-RFT)** — June 2026.

### What this line has established

The key engineering move is to replace semantic retrieval relevance with **expected downstream reasoning benefit** and then couple this retriever to reinforcement fine-tuning.

This changes analogy from an inference-time prompting trick into a component of post-training.

### Frontier position

Directly attacks **G2 reasoning-aware analogical retrieval** and part of **G7 unified training**.

### Missing

- open-domain mechanism alignment;
- explicit reject/no-analogy action;
- source applicability/rebinding;
- memory of failed source transfers;
- representation revision.

### Program maturity

**EARLY but strategically important.** One paper, but it sits directly on frontier-model post-training machinery rather than a peripheral benchmark.

### Why watch it

This is the clearest current path by which analogical reasoning could enter a modern reasoning-model recipe without requiring a fully symbolic analogy engine.

---

## 7. Agentic Analogical Reasoning (AAR) — direct control-policy attempt

**Core researchers:** Tianhui Ma, Chuan Qin, Liyi Chen, Qimeng Wang, Chengqiang Lu, Yan Gao, Yi Wu, Yao Hu, Hui Xiong.

Status:

- **Agentic Analogical Reasoning for Large Language Models** — public ICLR 2026 submission; not classified here as an accepted conference result.

### What this line is trying to establish

AAR is unusually direct about the control-policy framing. It repeatedly alternates:

`thinking → analogizing → contextualizing`

and trains analogical trajectories through generation, re-weighted trajectory training and mixed training. Analogies can be internally generated or externally retrieved.

### Frontier position

Potentially attacks **G7 unified analogical policy training** more directly than any other current system we have found.

### Missing / evidence caveat

The public evidence is currently a submission rather than a peer-reviewed accepted result. More importantly, downstream task improvement does not by itself establish:

- calibrated rejection;
- epistemic validity of selected analogies;
- failure memory;
- evidence-sensitive multi-analogy confirmation;
- representation revision after failed transfer.

### Program maturity

**WATCH / too early to call.** Conceptually important; evidence status lower than the accepted programs above.

---

## 8. Structural mapping + LLM abstraction — YARN / knowledge-representation line

**Core researchers:** Mohammadhossein Khojasteh, Yifan Jiang, Stefano De Giorgis, Frank van Harmelen, Filip Ilievski.

Anchor paper:

- **YARN: Enhancing Structural Mapping with LLM-derived Abstractions for Analogical Reasoning in Narratives** — 2026 preprint.

### What it establishes

YARN explicitly separates representation formation from mapping: LLMs decompose/abstract narratives, and an explicit mapping component aligns them.

The particularly useful finding is negative: **there is no universally optimal abstraction level**. This makes representation selection itself experimentally visible.

### Frontier position

Important bridge between **G1 representation selection** and explicit structural mapping.

### Missing

- learned dynamic choice/revision of abstraction level;
- source retrieval at scale;
- rejection/control policy;
- memory/validation loop.

### Program maturity

**MEDIUM / emerging hybrid line.** Valuable modularization, but too early to treat as a large program.

---

# Gap ownership map

| Gap | Strongest current programs attacking it | Coverage status |
|---|---|---|
| G1 representation selection | relational architecture; YARN; object-centric visual; active reasoning/BALAR | **active but fragmented** |
| G2 relational retrieval | RA-RFT / reasoning-intensive retrieval; CANA | **fast-moving engineering frontier** |
| G3 adjudication / rejection | CANA hard filters; adjacent abstention research | **no clear analogy-specific owner** |
| G4 novel-operation generalization | UvA/Mitchell diagnostics; meta-learning/ARC operator induction | **active, composition ahead of new primitives** |
| G5 grounded compositional analogy | OCRA/relational architectures; ARC/neuro-symbolic visual systems | **active but far below robust human transfer** |
| G6 source diversity without quality collapse | Stanford science-AR; analogy-diversity work | **emerging** |
| G7 unified analogical training/control | AAR; RA-RFT | **very early** |
| G8 calibrated analogical uncertainty | generic abstention/conformal work | **analogy-specific work sparse** |
| G9 autonomous validation/belief update | CLeaR active reasoning; AI-for-science agents; world-model revision | **active adjacent field** |
| G10 analogical memory / failed-transfer memory | agent workflow memory / QCR / failure-memory systems | **analogy-specific applicability memory sparse** |
| G11 multi-analogy integration | CANA | **one unusually explicit program; independence estimation open** |

---

# The conspicuous orphan gaps

After mapping programs rather than papers, three gaps stand out because they do **not** yet have a clearly established analogy-specific research program behind them.

## Orphan 1 — plausible-analogy rejection

Many groups improve retrieval, mapping or generation. Few train and evaluate a system whose core task is to reject a seductive but inference-invalid analogy.

## Orphan 2 — pipeline-level failure attribution

No clear program currently owns:

`failed transfer → diagnose representation vs retrieval vs mapping vs projection vs execution → update the correct module`.

Neighboring agent-debugging and belief-revision work has the primitives, but analogy research has not yet consolidated them.

## Orphan 3 — analogy-specific negative memory

Agent memory research is learning from failed trajectories, but very little work stores a relational applicability boundary of the form:

`source S failed for target class T because relation/condition X does not transfer`.

These three orphan gaps are especially important because they all optimize **precision and epistemic discipline**, whereas much of the current field optimizes recall, mapping ability, or solution diversity.

---

# Bottom line

The field is no longer a loose collection of analogy benchmarks. Several real programs now exist, but they occupy different layers:

- **architecture:** relational bottleneck / Abstractor / DAT;
- **diagnosis:** UvA/Mitchell and Korea DMIS;
- **retrieval + post-training:** RA-RFT / RIR;
- **causal agent control:** CLeaR / CANA;
- **open-ended scientific search:** Stanford science-AR;
- **direct analogical trajectory training:** AAR, still early;
- **hybrid mapping:** YARN.

The underoccupied territory lies between these programs. The most consequential next step is not another proof that a model can generate or map an analogy; it is **a controller that knows when an analogy is applicable, when to reject it, how to revise after failure, and what failure should change in memory and representation.**
