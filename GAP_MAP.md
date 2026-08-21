# Gap Map — How Far Has Analogical Reasoning in AI Actually Got? (August 2026)

This is a capability-boundary ledger. It asks what current AI systems can actually do, under which assumptions, and where performance breaks. The central distinction is **component competence** versus **end-to-end analogical intelligence**.

> **Current frontier models can often encode relations, align supplied analogues, and transfer familiar transformations. They are not yet robust at autonomously choosing representations, retrieving distant but structurally useful sources, rejecting plausible-but-wrong analogies, generalizing to genuinely new relational operators, or validating analogical hypotheses in open worlds.**

The most informative evidence comes from stress transitions rather than headline accuracy: familiar → unfamiliar symbols; known → novel transformations; oracle → noisy perception; single → composed rules; short → system-level narratives; supplied source → large source bank; plausible analogy → hard negative; closed benchmark → open-ended discovery.

## Capability boundary

| Capability | Current level | What works | Main break |
|---|---|---|---|
| Encode familiar relations | **Strong** | mechanistic probes and interventions recover relational information | abstract/context-sensitive representations are unstable |
| Map supplied simple structures | **Strong–moderate** | proportional, semantic and controlled structural tasks | non-isomorphic, hierarchical, noisy real-world structures |
| Apply familiar mapped transformations | **Moderate–strong** | many closed tasks; causal interventions can repair outputs | relation can be encoded but misapplied; execution confounds |
| Transfer to new surface symbols | **Moderate with specialised training; weak by default** | meta-learning/curriculum can produce new-alphabet transfer | genuinely novel relational operators remain difficult |
| Compose multiple transformations | **Weak–moderate** | trained compositions sometimes transfer | multi-rule visual composition degrades rapidly |
| Perception-grounded analogy | **Weak–moderate** | simple visual attributes and transformations | perceptual uncertainty, quantification, spatial relations |
| Retrieve from large source banks | **Moderate** | broad semantic retrieval; agentic decomposition helps | surface similarity is a poor proxy for structural utility |
| Generate distant analogues | **Moderate** | cross-domain prompting expands search space | domain homogeneity and diversity–quality tradeoff |
| Select among plausible analogues | **Weak** | reasoning models improve when explicitly cued | high recall but false-positive, internally coherent mappings |
| Reject misleading analogy | **Weak / under-benchmarked** | some negative classification | no reliable veto criterion or calibrated `no analogy` action |
| Learn a reusable analogy policy | **Promising but narrow** | relational architectures, analogical supervision, meta-learning | task specificity; fragmented pipeline objectives |
| Autonomous open-world discovery | **Early** | science/foresight systems show instrumental gains | heavy scaffolding, retrieval design and external validation |

## 1. Representation construction

### Demonstrated

Mechanistic studies now support a real claim that LLMs contain relational information rather than merely matching surface strings. Lee et al. (AAAI 2026) separate relation encoding, relation application and structural alignment; Minegishi et al. show learnable relation-preserving transformations in controlled Transformers. Multimodal systems can often identify **what attribute changed** in simple visual analogies.

### Boundary

The hard problem is choosing the representation itself. Opiełka et al. find that some relations admit stable internal concept vectors while more abstract transformations do not. YARN shows that narrative mapping quality changes sharply with abstraction level. KiVA separates recognising *what* changed from representing *how* it changed. CARV raises the difficulty to compositions of transformations; Gemini-2.5 Pro reaches 40.4% while the reported human baseline is 100%.

**Status: OPEN — high confidence.** The missing procedure is: given a raw target, construct the relational decomposition most useful for comparison rather than assume the benchmark supplied it.

## 2. Relational source retrieval

### Demonstrated

LLMs are strong candidate generators. Analogical prompting can self-generate useful examples; open-ended scientific work shows cross-domain analogy generation can enlarge solution diversity. Retrieval-augmented approaches can also search explicit case banks.

A particularly important 2026 development is **RA-RFT (Retrieval-Augmented Reinforcement Fine-Tuning)**: it trains retrieval toward *expected reasoning benefit* rather than ordinary semantic overlap, then reinforcement-fine-tunes the policy with analogous reasoning traces. On AIME 2025 it reports +7.1 and +2.8 average@32 points over GRPO for Qwen3-1.7B and 4B respectively. This is direct evidence that the field has begun attacking the retrieval objective itself.

### Boundary

AnaloBench still shows limited gains on long, abstract retrieval from larger source spaces. In strategic analogical matching, LLMs exhibit extremely high recall after a cue but substantially weaker precision. CANA/ADR reports that generic deep-research agents tend to retrieve on surface resemblance rather than mechanisms. The August 2026 diversity study finds generated analogies cluster in a narrow set of domains and that increasing diversity can reduce quality.

**Status: OPEN, actively attacked — high confidence.** The target is `large source space + weak surface similarity + strong structural/mechanistic utility`. RA-RFT is a serious step, but evidence is still concentrated in math/reasoning traces rather than open-domain structural retrieval.

## 3. Structural mapping

### Demonstrated

This is probably the strongest component at present. Supplied-source mapping works well on many proportional/semantic tasks. Mechanistic work identifies internal alignment signals. Explicit relational architectures (Abstractors, relational cross-attention, Dual Attention) improve sample efficiency/systematic generalization. Hybrid systems such as YARN can pair learned text abstractions with an explicit mapping stage.

### Boundary

Real cases are partial, noisy, hierarchical and often non-isomorphic. Long narrative analogies retain a large near/far gap; visual mapping deteriorates under composition or uncertain perception.

**Status: PARTLY SOLVED.** Pairwise mapping over reasonably clean representations is no longer the deepest bottleneck. The main pressure has shifted upstream to representation/retrieval and downstream to matching/rejection.

## 4. Projection and execution

### Demonstrated

LLMs often transfer a recognised relation to a target. Causal patching can restore some failed applications. Specialised meta-training can learn procedures that transfer to new symbols and some compositions.

### Boundary

A model can encode the correct relation and still fail to apply it. Counterfactual letter-string work also shows that some apparent analogy failures are auxiliary indexing/counting failures; code/tool execution can restore performance. Hellwig et al. obtain strong new-alphabet transfer but do not solve completely novel transformations.

**Status: PARTLY SOLVED, task-dependent.** Benchmarks should separate representation failure, mapping failure, transfer-rule failure, and low-level execution failure.

## 5. Matching, adjudication, and rejection

This is currently one of the clearest bottlenecks.

Sen, Workiewicz & Puranam isolate a precision–recall asymmetry. With explicit analogy cues, LLM recall can approach 1.0 while human recall is much lower; humans maintain higher precision, while LLMs often admit spurious matches. The dangerous cases are not merely superficial: reasoning models can construct **internally coherent causal schemas that are nevertheless the wrong analogy**.

Most benchmarks contain too few hard negatives of the form:

`high semantic plausibility + high partial structural fit + inference-invalid`.

**Status: OPEN — very high confidence; priority gap.** A mature system needs a learned selection/veto mechanism, calibrated uncertainty, and the ability to return `no useful analogy` rather than satisfy an analogy-seeking prompt.

## 6. Robust far generalization

The recurring distinction is between changing **operands/notations** and changing the **relational operator itself**.

Specialised meta-learning can produce impressive new-alphabet transfer. Yet Lewis & Mitchell show large drops under task-preserving reformulations; Stevenson et al. find humans/children transfer procedures to Greek/unfamiliar symbols much more robustly; Hellwig et al. still fail on completely novel transformations; KiVA and CARV show the same problem in vision.

**Status: OPEN — very high confidence.** The unsolved target is procedure-level generalization to unseen relational operators, not ordinary OOD transfer to new surface tokens.

## 7. Perception-grounded and compositional analogy

I-RAVEN-X is a particularly strong stress test. o3-mini drops from 86.6% on I-RAVEN to 17.0% on the harder extension despite using 3.4× more reasoning tokens; DeepSeek-R1 drops from 80.6% to 23.2%. A specialised neuro-symbolic probabilistic model drops much less, from 98.6% to 88.0%. CARV independently reports only 40.4% for Gemini-2.5 Pro on multi-pair compositional visual analogy versus 100% for humans.

**Status: OPEN — high confidence.** More test-time reasoning does not repair a bad perceptual/relational representation. Textualized or oracle-perception tasks substantially overestimate grounded analogical competence.

## 8. Learning analogy rather than prompting it

Three mature-enough directions are visible:

1. **architectural inductive bias** — relational attention / Abstractors / Dual Attention;
2. **analogical supervision** — train on surface-distinct cases sharing a solution schema (e.g. SAL);
3. **meta-learning / curricula** — induce transferable procedures through heterogeneous tasks and intermediate copying skills.

A fourth direction is now appearing around reasoning-aware retrieval and multi-step analogy policies. RA-RFT is especially important because retrieval and policy learning are co-designed around reasoning utility rather than semantic similarity.

**Status: ACTIVE / UNSOLVED.** There is still no public evidence that a general frontier foundation model has an end-to-end post-training objective that jointly learns representation, source retrieval, mapping, rejection, transfer and validation across text, vision and open worlds.

## 9. Open-world analogical discovery

### Demonstrated

2026 provides real evidence that analogy is useful as a **search operator**. Shen, Druckmann & Zou report 90–173% improvements in solution-diversity metrics, novel solutions over 50% of the time versus as little as 1.6% for baselines, and quantitative gains after implementing generated approaches on four biomedical problems. Larraz & Corma show that explicit analogical guidance can strongly amplify solution synthesis in a historical FCC reconstruction. CANA/ADR uses mechanism alignment and cross-analogy confirmation for foresight retrieval/integration.

### Boundary

These results still rely on scaffolding: explicit analogical prompts or human-selected analogies, curated corpora/problem sets, retrieval infrastructure, task-specific evaluators/LLM judges, decomposition loops, and downstream experimental selection. In Larraz & Corma, autonomous success remains rare (≤10%) while explicit structured analogical scaffolding can reach 100% in the reported setup.

**Status: EARLY BUT REAL.** The strongest claim today is `analogy expands and redirects the search space`, not `autonomous systems reliably discover and validate the best analogy end to end`.

The unsolved loop is:

`problem representation → source search → structural/mechanistic matching → rejection → projection → executable test → evidence update → revised search`.

## Ranked gaps

### Tier 1 — empirically established

**G1 Representation selection.** Construct the useful relational description rather than receive it from the task format.

**G2 Relational retrieval at scale.** Retrieve structurally useful sources when semantic/surface similarity is weak.

**G3 Matching / rejection.** Reject persuasive, partially aligned but inference-invalid analogies.

**G4 Novel-operation generalization.** Transfer the procedure of analogizing to unseen transformations/operators, not merely new operands or symbols.

**G5 Grounded compositional analogy.** Maintain relations under perception uncertainty, spatial structure, and multi-rule composition.

### Tier 2 — active engineering frontier

**G6 Diversity without quality collapse.** Broaden source search without generating arbitrary remote analogies.

**G7 Unified analogical training.** Jointly optimize retrieval, mapping, selection, projection and validation rather than train isolated stages.

**G8 Calibrated analogical uncertainty.** Learn when no candidate is reliable enough to transfer.

### Tier 3 — frontier research program

**G9 Autonomous validation.** Convert projected hypotheses into executable tests and update confidence from evidence.

**G10 Continual analogical memory.** Let successful and failed analogies alter future representations and retrieval policies, rather than merely accumulating text in a vector store.

**G11 Multi-analogy integration.** Combine several partial analogies while accounting for dependence/correlated errors so agreement does not become false confirmation.

## Strongest research bets to monitor

1. **Mapping will cease to be the central bottleneck before analogy itself is solved.** Clean pairwise mapping is advancing faster than representation, retrieval and rejection.
2. **Reasoning-aware retrieval is becoming a first-class training target.** RA-RFT is an important signal: retrieval can be trained for downstream reasoning utility rather than semantic proximity.
3. **Specialised relational systems can beat generic scaling on specific OOD transitions.** I-RAVEN-X and meta-learning results make this difficult to dismiss as a pure scale problem.
4. **Visual/embodied analogy will force representation learning back to centre stage.** Longer chains of thought cannot compensate for wrong perceptual decomposition.
5. **Scientific analogy may become practically valuable before general analogical intelligence is solved.** Search-space expansion can be useful even when epistemic selection and validation remain imperfect.

## What future papers should change in this ledger

For every new result record:

- source **supplied / retrieved / generated**;
- near transfer type: new operands vs new surface symbols;
- far transfer type: new compositions vs genuinely new operators;
- presence of **hard negative analogues**;
- whether `no valid analogy` is an allowed action;
- oracle/symbolic perception vs raw multimodal input;
- candidate-selection **precision/recall**, not final accuracy alone;
- whether open-world claims have external/experimental validation or only model-judge novelty;
- whether learning changes representation/retrieval policy or merely adds demonstrations.

The ledger should be updated when a paper crosses a capability boundary, not simply because it uses the word *analogy*.
