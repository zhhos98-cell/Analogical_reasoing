# Field Map — Analogical Reasoning in AI (2026)

This document maps the **current AI field on its own terms**. Historical theories are deliberately parked for now. The purpose is to establish what researchers presently mean by analogical reasoning, which computational subproblems are actually being studied, where communities overlap, and where the empirical bottlenecks are.

## 1. Scope: what counts as analogical reasoning here?

A useful minimal definition is:

> **Analogical reasoning transfers relational structure from one situation/domain to another in a way that supports recognition, inference, prediction, explanation, or solution generation.**

This is narrower than generic similarity and broader than `A:B::C:?` word puzzles. The field currently uses the term *analogy* for several different operations that should not be collapsed:

- **analogy recognition** — determine whether two cases instantiate the same relational pattern;
- **analogy retrieval** — find a useful source case given a target problem;
- **analogical mapping** — align entities/roles/relations between source and target;
- **matching/adjudication** — decide which of several plausible sources is structurally appropriate;
- **analogical projection** — transfer a rule, relation, causal mechanism, or solution from source to target;
- **analogical generation** — invent candidate source analogies;
- **analogical learning** — use sets of analogous cases as a training signal to induce transferable structure;
- **analogical discovery** — use cross-domain correspondence to generate a genuinely new hypothesis or solution.

Several adjacent topics overlap but should be tagged separately rather than treated as identical: relational reasoning, abstract reasoning, in-context learning, Raven/ARC-style rule induction, metaphor, case-based reasoning, causal reasoning, retrieval-augmented generation, and program induction.

## 2. A computational pipeline for organizing the field

The most useful field-wide decomposition is not by model family but by **where in the analogical pipeline the work occurs**:

`target representation ↔ source search → relation extraction → structural alignment → matching/adjudication → projection/inference → execution → validation/generalization → learning/update`

The arrows are not strictly sequential. Representation affects retrieval; candidate mappings can trigger rerepresentation; failed projection can cause a new source search.

### Stage A — Target representation

The system must determine what entities, relations, events, attributes, roles, and causal dependencies matter in the target. Many benchmark papers quietly provide this structure through the format of the task. Open-ended systems must infer it.

**Current evidence:** representation quality is becoming an explicit concern. Concept-vector work finds that some relational concepts are internally stable while more abstract transformations are not reliably captured by simple linear representations. YARN shows that different abstraction levels can produce very different mapping quality.

### Stage B — Source retrieval / generation

Given a target, find or generate candidate analogous cases. This can mean memory retrieval, vector search, RAG over a corpus, generation from model parameters, or search over a structured case base.

**Current evidence:** LLMs are often broad but noisy source generators. AnaloBench shows that retrieval from large story banks becomes difficult even when scale increases. Strategy experiments find high recall but low precision. The August 2026 diversity study shows that model-generated analogies are often domain-homogeneous, revealing a second problem: the candidate search space itself can collapse.

### Stage C — Relation extraction / abstraction

Infer the relation that matters, rather than relying on entity or surface similarity. This is the central boundary between association and analogy in much current work.

**Current evidence:** models can encode many relational concepts, but abstract relations are less stable; visual models frequently identify *what* changed while failing to represent *how* it changed precisely. Architectures with explicit relational channels improve data efficiency and generalization on controlled tasks.

### Stage D — Structural alignment / mapping

Construct correspondences between source and target roles or relational structures.

**Current evidence:** story/narrative benchmarks consistently show a near/far gap. Mechanistic work finds that successful cases exhibit stronger structural alignment in internal representations. Graph and neuro-symbolic systems explicitly optimize correspondence constraints instead of leaving alignment implicit.

### Stage E — Matching / adjudication

Decide whether a candidate analogy is actually appropriate, especially when several plausible sources exist. This is distinct from retrieving a candidate or finding some mapping.

**Current evidence:** this is one of the clearest weak points. In strategic decision experiments, LLMs retrieve many valid candidates but also generate many false positives; humans show the reverse precision–recall profile. Much of the benchmark literature prespecifies the source, thereby bypassing this stage.

### Stage F — Projection / inference

Transfer the discovered relational rule, causal mechanism, or solution to the target and generate a candidate conclusion.

**Current evidence:** models may internally encode the correct relation yet still fail to apply it. Hidden-state patching can partially repair these failures, suggesting a dissociation between representation and use.

### Stage G — Execution

Carry out any domain-specific operation required after the analogy is understood: indexing, counting, symbolic manipulation, code execution, spatial transformation, etc.

**Current evidence:** some apparent analogy failures are auxiliary execution failures. Counterfactual letter-string work shows that code execution can restore performance when the bottleneck is precise indexing/counting. This matters methodologically: a benchmark may conflate analogy with another capability.

### Stage H — Validation and generalization

Check whether the inferred relation works in a new domain, new alphabet, new surface form, longer context, or unseen transformation.

**Current evidence:** this is the main empirical fault line. Frontier models often perform well in familiar or near-transfer settings but degrade under shuffled alphabets, new symbol systems, far narrative analogies, longer stories, and unfamiliar visual transformations. Specialized meta-learning can outperform much larger frontier models on controlled out-of-distribution transfer.

### Stage I — Learning / update

Use analogical structure itself as supervision or as a mechanism for rapid task acquisition.

**Current evidence:** this is still early. Self-supervised Analogical Learning constructs surface-distinct examples sharing a reasoning schema and uses them for training. Meta-learning work shows that curriculum structure, copying subtasks, and heterogeneous training domains can strongly alter analogical generalization.

## 3. The field is currently five partially overlapping communities

### 3.1 Behavioral capability and human-comparison research

**Question:** Do frontier models actually possess robust analogy-making competence, and how does their error profile differ from humans?

Typical methods:
- zero/few-shot testing of pretrained LLMs;
- counterfactual or distribution-shift variants;
- adult/child comparison;
- surface-vs-relational distractors;
- near/far transfer;
- paraphrase and answer-order robustness.

Representative line:
- Webb et al. (2023), *Emergent analogical reasoning in large language models*;
- Hodel & West (2024) response;
- Lewis & Mitchell (TMLR 2025), robustness tests;
- Webb et al. (PNAS Nexus 2025), counterfactual tasks with code execution;
- Johnson et al. (CoNLL 2025), verbal analogies and association;
- Musker et al. (JML 2025), human-like vs human-level performance;
- Stevenson et al. (TACL 2026), near/far alphabet transfer.

**What this community has established:** high raw accuracy does not settle whether a model has robust relational abstraction. Small changes in task format, symbol system, context length, or distractors can produce large performance changes.

### 3.2 Benchmark and task-design research

**Question:** What would a serious test of analogy look like beyond word-pair completion?

Key benchmark families:
- **proportional/verbal analogies** — compact relation completion, often knowledge-heavy;
- **letter-string analogies** — controlled rule induction and compositional transfer;
- **matrix / Raven / ARC-like tasks** — abstract transformation and rule induction;
- **narrative/story analogies** — systems of relations over long text;
- **visual/multimodal analogies** — transformations over attributes and spatial relations;
- **open-world retrieval/matching** — find a source among many plausible cases;
- **discovery tasks** — use analogies to produce new technical/scientific solutions.

Core datasets/benchmarks:
- E-KAR (2022): knowledge-intensive verbal analogy with rationales;
- StoryAnalogy (2023/24): large story-pair corpus for identification and generation;
- ARN (TACL 2024): near/far narrative analogies and disanalogies;
- AnaloBench (EMNLP 2024): long-context analogy identification and large-bank retrieval;
- KiVA (ICLR 2025): 4,300 kid-inspired visual transformations;
- Prowise verbal analogy set / CoNLL 2025: 872 problems with 14,006 children;
- TACL 2026 letter-string transfer suite: Latin → Greek → novel symbols;
- NARB (2026 preprint): narrative/rhetorical parallelism with representation probes;
- ADR-bench (2026): open-ended historical analogy retrieval/integration for foresight.

**Major benchmark problem:** each dataset isolates only part of the pipeline. A model can look strong because the source is prespecified, the relevant relation is obvious, the answer set is constrained, or auxiliary computation is easy.

### 3.3 Architectures and training for relational/analogical abstraction

**Question:** Can a model be designed or trained so that relational structure is an inductive bias rather than an accidental emergent property?

Main approaches:

1. **Relational architectural bias**
   - Abstractors / relational cross-attention (ICLR 2024);
   - relational bottleneck framing (Trends in Cognitive Sciences 2024);
   - Dual Attention Transformer (ICML 2025), separating sensory and relational information flow.

2. **Analogical contrastive / meta-learning**
   - Meta-Analogical Contrastive Learning for visual reasoning;
   - MLC-based letter-string training in *Transformer See, Transformer Do* (2026).

3. **Analogical supervision**
   - Self-supervised Analogical Learning (2025): generate structurally analogous examples and train on shared reasoning schemas.

4. **Explicit geometric constraints**
   - latent-space relation transformations / analogy geometry.

**Main result:** explicit relational bias can yield major gains in sample efficiency and controlled systematic generalization. This is currently much stronger evidence for *engineering analogical competence* than simply scaling a generic language model.

### 3.4 Mechanistic interpretability and internal representation

**Question:** What internal computations correlate with or cause successful analogical reasoning?

Methods:
- layer-wise probes;
- representational similarity analysis;
- attention knockout;
- activation/representation patching;
- steering with function/concept vectors;
- geometric analysis of embedding structure;
- synthetic training trajectories.

Representative work:
- Opiełka et al. (2025), concept vectors and abstraction limits;
- Lee et al. (AAAI 2026), relation encoding vs application vs alignment;
- Minegishi et al. (2026), emergence dynamics and geometric/functor-like mechanisms;
- Hellwig et al. (2026), a small transformer whose learned letter-string algorithm can be mechanistically reconstructed;
- NARB work (2026), probing vs prompting dissociations.

**Emerging consensus:** `representation present` does not imply `behavior correct`. Models can encode task-relevant relational structure that standard generation fails to use. This creates a major distinction between competence, access, and execution.

### 3.5 Open-ended analogy systems and analogical discovery

**Question:** Can analogy improve real problem solving when the source is not provided and the answer is not known in advance?

Approaches:
- self-generated analogical exemplars before reasoning;
- retrieval over large case banks;
- RAG plus analogical guidance;
- causal/mechanism-aligned retrieval;
- cross-domain solution search;
- integration of multiple analogies.

Representative work:
- DeepMind, *Large Language Models as Analogical Reasoners* (2023): self-generated relevant exemplars before solving math/code/reasoning tasks;
- AnaloBench (2024): large-bank source retrieval;
- strategy matching study (2026): retrieval/matching precision–recall tradeoff;
- Larraz & Corma (Nature Communications 2026): analogical guidance activates cross-domain technical knowledge;
- Shen, Druckmann & Zou (2026), *Unlocking LLM Creativity in Science through Analogical Reasoning*: analogy expands open-ended scientific solution diversity;
- CANA / ADR (2026): mechanism alignment and cross-analogy confirmation for foresight;
- CHAIRO (ACL 2026): end-to-end analogical retrieval and rule induction in moderation, best treated as an application of the pipeline rather than evidence for general analogy competence.

**Current status:** highly promising, but most systems still receive crucial scaffolding: a curated corpus, an analogy-oriented prompt, human-provided guidance, a predefined decomposition, or an external evaluator.

## 4. What the field actually agrees on by mid-2026

### 4.1 Near analogy is much easier than far analogy

Models handle analogies best when source and target share vocabulary, entities, familiar relations, or training-distribution structure. Cross-domain/system-level analogies remain substantially harder. ARN, long-story benchmarks, letter-string transfer, and visual analogy work all converge on this pattern.

### 4.2 Association is a persistent shortcut

High semantic association can masquerade as relational understanding. Verbal analogy experiments with child-derived distractors show heavy reliance on association; narrative systems often prefer surface similarity; open-world retrieval often returns topically similar cases rather than mechanism-level matches.

### 4.3 Scale helps, but does not solve the core problem

Larger models often improve on short or familiar tasks. Gains flatten or become unreliable in long-context analogy, far transfer, retrieval from large banks, or counterfactual symbol systems. Small models with a strong training curriculum or relational inductive bias can outperform frontier LLMs on specific OOD analogy tasks.

### 4.4 Representation and application are dissociable

A model may internally encode the correct relation but fail to transfer or express it. This is supported by concept-vector analyses, probes, and causal representation patching.

### 4.5 Prompting can improve performance without proving an analogical mechanism

Few-shot examples, chain-of-thought, and self-generated analogous demonstrations often improve accuracy. This tells us analogy can be a useful **inference strategy**, but by itself does not show that the model learned a reusable structural mapping mechanism.

### 4.6 Evaluation is heavily confounded by auxiliary capabilities

Counting, indexing, long-context attention, parsing, domain knowledge, spatial manipulation, and answer formatting can determine whether an analogy item is solved. Code-augmented counterfactual experiments make this especially clear.

### 4.7 Retrieval and adjudication are becoming central

The field is moving from `given source + given target → answer` toward `target → find source → decide whether it is valid → use it`. The strategy study, AnaloBench, analogy-diversity work, and ADR make this transition visible.

### 4.8 Open-ended discovery is the new frontier, not yet a solved capability

2026 work in scientific creativity and foresight suggests that analogical search can expand solution spaces and activate remote knowledge. What remains unclear is whether models can autonomously select fruitful representations and sources, reject plausible but misleading analogies, and validate the resulting hypotheses without substantial scaffolding.

## 5. The main unresolved research questions

### Q1. How should the target be represented before source search?
Most benchmarks make this easy. Open-world analogy cannot.

### Q2. How can retrieval optimize for relational usefulness instead of topical similarity?
Embedding retrieval naturally rewards semantic proximity, which can conflict with far analogy.

### Q3. How should candidate analogies be ranked or rejected?
The field has much better machinery for generating candidates than for deciding that a coherent analogy is **wrong or irrelevant**.

### Q4. How are multiple relations bound into a coherent system?
Word-pair relations are easier than multi-entity narratives, causal systems, or technical processes. Long-context results suggest scaling alone is insufficient.

### Q5. Can a model generalize the *procedure of analogizing* to genuinely new domains?
The Latin → Greek → symbol results and novel-transformation failures suggest current models often learn domain-bound procedures rather than a portable operation.

### Q6. Can analogical structure become a pretraining or post-training objective at scale?
Current evidence comes mostly from small models, task-specific architectures, SFT/meta-learning, or generated supervision. Public evidence that frontier-model training recipes contain a dedicated analogical objective remains limited.

### Q7. What is the causal internal algorithm?
Mechanistic results are rapidly improving but remain model- and task-specific. We do not yet know whether different model families converge on the same internal analogical computation.

### Q8. How should multimodal analogy work?
KiVA and related tasks show strong failures on counting, rotation, reflection, and spatial relations. Textual relational competence does not transfer cleanly to vision.

### Q9. Can multiple analogies be integrated rather than merely listed?
Open-world reasoning often needs several imperfect precedents whose shared mechanism matters more than any one source. ADR/CANA is one of the first explicit attempts at this.

### Q10. What would falsify the claim that a system has general analogical intelligence?
The field still lacks a broadly accepted evaluation protocol combining contamination resistance, far transfer, source retrieval, mapping, rejection, projection, and open-domain validation.

## 6. Benchmark landscape by pipeline coverage

| Benchmark/task | Representation | Retrieval | Mapping | Matching/rejection | Projection | Far/OOD transfer | Modality |
|---|---:|---:|---:|---:|---:|---:|---|
| classic verbal A:B::C:? | low | no | partial | weak | yes | usually weak | text |
| letter-string analogy | constrained | no | yes | weak | yes | **strongly testable** | symbolic text |
| E-KAR | constrained | no | yes | MCQ | yes + rationale | limited | text |
| ARN | narrative | no | **yes** | disanalogy | limited | **near/far** | text |
| AnaloBench | narrative | **yes** | yes | selection | limited | long-context | text |
| KiVA | visual | no | rule extraction | selection | **yes** | object transfer | vision/multimodal |
| strategy matching | naturalistic | **yes** | yes | **central** | decision | multiple targets | text |
| ADR-bench | open event | **yes** | causal | **central** | foresight | cross-domain | text + retrieval |
| scientific analogy generation | open problem | generated | implicit | evaluator-dependent | **solution generation** | cross-domain | text + scientific tasks |

No single benchmark currently covers the whole pipeline.

## 7. Method-family map

| Method family | What it tries to solve | Main strength | Main weakness |
|---|---|---|---|
| prompting / analogical exemplars | source generation + projection | cheap, model-agnostic | mechanism ambiguous |
| RAG / case retrieval | source search | scalable memory access | surface-similarity bias |
| explicit relational attention | relation abstraction | sample efficiency, OOD structure | often tested on controlled tasks |
| meta-learning / curriculum | portable procedure | strong controlled generalization | task-specific training |
| contrastive analogical learning | relational invariance | learns cross-instance structure | depends on good positive/negative pair construction |
| graph / neuro-symbolic mapping | correspondence constraints | explicit structure and interpretability | representation bottleneck, combinatorics |
| activation probing / patching | internal mechanism | causal/mechanistic evidence | local to model/task |
| causal/mechanism-aligned agents | matching + integration | closer to real-world analogy | decomposition/evaluation often externally supplied |

## 8. The strongest current research clusters to watch

This is a **community map**, not a ranking.

- **University of Amsterdam / ILLC / psychology + Santa Fe Institute network** — human/model comparison, letter-string analogy, generalization, meta-learning, mechanistic representation. The 2026–27 NIAS-Lorentz group “ABCs of Analogy” explicitly organizes around abstraction, broad generalisation, and composition.
- **VU Amsterdam + USC/ISI network** — narrative analogy, benchmark construction, structured abstraction, neuro-symbolic mapping, YARN; also central to Analogy-Angle.
- **Princeton/Yale relational architecture line** — relational bottleneck, Abstractors, Dual Attention Transformer; one of the clearest architecture-first attempts to engineer relational abstraction.
- **UCLA / Microsoft relational-reasoning line** — behavioral analogy tests, relation representation, counterfactual robustness, and current mechanistic questions.
- **Korea University DMIS / AIGEN Sciences** — 2026 mechanistic probing of relation encoding, application, and structural alignment.
- **Google DeepMind** — analogical prompting and multimodal/child-inspired analogy evaluation (KiVA); important but not a single dedicated analogy program.
- **Scientific-discovery / agentic analogy line** — emerging 2026 work using analogical search for biomedical creativity, technical invention, and causal foresight; currently distributed across groups rather than consolidated into one lab.

## 9. Community maturity

Evidence that this is becoming a recognizable field:

- Analogy-Angle I at IJCAI 2024 and Analogy-Angle II at ACL 2025 explicitly bridge AI, NLP, cognitive psychology, benchmarks, algorithms, visual analogy, discovery, and applications.
- TACL 2026 published a field-bridging review focused specifically on modelling analogies and analogical reasoning in NLP.
- A 2026–27 NIAS-Lorentz Theme Group centers on analogy as abstraction + broad generalisation + composition.
- A 2027 Dagstuhl seminar proposal on **Analogical Abstraction: Modeling and Applications** has been accepted.
- Analogy-adjacent abstraction work also appears at THEMA 2026 and neuro-symbolic venues.

At the same time, the field remains fragmented. There is no standard leaderboard, no agreed end-to-end pipeline, no dominant architecture, and no consensus definition of “general analogical intelligence.”

## 10. Recommended core reading order — current field only

1. **Webb, Holyoak & Lu (2023)** — establishes the modern LLM analogy debate.
2. **Lewis & Mitchell (TMLR 2025)** — robustness challenge and counterfactual variants.
3. **Sourati et al. (TACL 2024), ARN** — system-level narrative analogy and near/far distinction.
4. **Ye et al. (EMNLP 2024), AnaloBench** — retrieval + long-context analogy.
5. **Yiu et al. (ICLR 2025), KiVA** — visual analogy decomposition and human/child comparison.
6. **Altabaa et al. (ICLR 2024) + Altabaa & Lafferty (ICML 2025)** — explicit relational architectures.
7. **Opiełka et al. (2025) + Lee et al. (AAAI 2026)** — internal representation and causal mechanisms.
8. **Stevenson et al. (TACL 2026) + Hellwig et al. (2026)** — far transfer and trainable meta-analogical procedures.
9. **Petersen et al. (TACL 2026)** — current field synthesis connecting analogy processes to NLP.
10. **Larraz & Corma (Nature Communications 2026), Shen/Druckmann/Zou (2026), Chen et al. ADR (2026)** — transition from closed-form analogy tests to scientific/open-world discovery.

## 11. Repository schema we should use from here

For every paper, record at least:

- `pipeline_stage`: representation / retrieval / relation-extraction / mapping / matching / projection / execution / validation / learning;
- `task_family`: verbal / letter-string / matrix-ARC / narrative / visual / multimodal / open-world / scientific;
- `method_family`: prompting / RAG / architecture / meta-learning / contrastive / graph-neurosymbolic / interpretability / agent;
- `evidence_type`: behavioral / human-comparison / causal-intervention / training / benchmark / application;
- `source_given`: yes/no;
- `target_structure_given`: yes/no;
- `far_transfer_tested`: yes/no;
- `negative_or_distractor_tested`: yes/no;
- `open_ended`: yes/no;
- `human_baseline`: yes/no;
- `code_or_data`: link;
- `peer_review_status`;
- `main_failure_mode`;
- `core_claim`;
- `confidence`.

This makes it possible to query the corpus by **what part of analogy a paper actually solves**, instead of by whatever terminology its authors happen to use.

## 12. Working conclusion

The field is moving through three phases:

1. **2023–24: capability dispute** — can generic LLMs solve analogy tasks at all, and are results robust?
2. **2024–26: decomposition** — separate relation representation, mapping, retrieval, far transfer, multimodality, and failure modes; introduce specialized architectures and mechanistic probes.
3. **2026 onward: open-world analogical systems** — retrieve/generate remote sources, judge mechanism-level fit, integrate multiple analogies, and use them for discovery.

The decisive frontier is no longer whether an LLM can answer a supplied analogy puzzle. It is whether a system can **construct the right representation, search a large source space, distinguish deep from superficial correspondence, reject attractive false analogies, transfer only what is warranted, and validate the resulting inference in a new domain**.
