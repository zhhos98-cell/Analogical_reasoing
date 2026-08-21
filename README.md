# Analogical Reasoning Observatory

A living map of **current analogical reasoning research in AI**: how models represent relations, retrieve and generate source analogies, align structures, adjudicate candidate matches, transfer rules or mechanisms, generalize across domains, and use analogy in open-ended discovery.

The first priority is to understand the contemporary field on its own terms. Historical theories are deliberately parked until the modern computational landscape is stable.

## Start here

- **[FIELD_MAP.md](FIELD_MAP.md)** — operational map of the field: pipeline, communities, benchmark landscape, method families, empirical consensus, research gaps, and labs/groups to watch.
- **[GAP_MAP.md](GAP_MAP.md)** — capability-boundary ledger: what current systems can actually do, where performance breaks, and which gaps are established versus frontier.
- **[ADJACENT_FIELDS.md](ADJACENT_FIELDS.md)** — research that attacks the same gaps without using `analogy` as its primary label: reasoning-intensive retrieval, abstention/control, operator induction, visual abstraction, agent memory, failure learning, and active belief/state revision.
- **[CONTROL_LAYER.md](CONTROL_LAYER.md)** — coverage matrix for emerging analogical controllers: who already does search, ranking, rejection, rebinding, verification, trajectory training, state revision, and memory update.
- **[TRANSFER_VALIDITY.md](TRANSFER_VALIDITY.md)** — focused bridge to modern Case-Based Reasoning and causal transportability; refines “analogy rejection” into open-world learned transfer validity.
- **[PROGRAM_MAP.md](PROGRAM_MAP.md)** — research-program map: which groups have sustained architecture/evaluation/agent/discovery programs and which gaps still have no clear owner.
- **[data/papers.csv](data/papers.csv)** — structured paper metadata.
- **[data/gaps.csv](data/gaps.csv)** — queryable gap ledger with status, confidence, diagnostic transition, and representative evidence.
- **[data/adjacent_fields.csv](data/adjacent_fields.csv)** — crosswalk from neighboring fields to analogical-reasoning gaps.
- **[data/control_systems.csv](data/control_systems.csv)** — system-by-system control-layer coverage.
- **[data/transfer_validity.csv](data/transfer_validity.csv)** — source–target validity, adaptation, failure-control, and uncertainty mechanisms across CBR and causal transportability.
- **[data/programs.csv](data/programs.csv)** — program maturity, key people/networks, strongest gaps, and missing layers.
- Category notes below — close reading of representative work.

## Latest watchlist — August 2026

| Date | Paper | Why it matters | Category |
|---|---|---|---|
| 2026-08-16 | [Felekis et al., *Generalised Transportability via Causal Abstractions*](https://arxiv.org/abs/2608.15645) | Gives model-level exact source→target transport maps and, when exact transport fails, approximate maps with **certified query intervals**. | Adjacent: transfer validity / uncertainty |
| 2026-08-13 | [Li et al., *Beyond Retrieval: Query-Conditioned Reuse of Long-Horizon Agent Trajectories*](https://arxiv.org/abs/2608.12847) | Separates **retrieval** from post-retrieval **reuse/applicability/rebinding/verification**; highly relevant to analogy transfer. | Adjacent: agent memory / reuse |
| 2026-08-10 | [Engdahl et al., *BDH-CQ: In-Context Learning with Recurrent Latent Reasoning*](https://arxiv.org/abs/2608.09888) | Learns demonstration-conditioned visual operator schemas in recurrent latent memory without parameter updates at inference. | Adjacent: operator induction |
| 2026-08-04 | [Shen et al., *On the Diversity of Analogy Making in Large Language Models*](papers/05_generalization-and-failure.md#shen-2026) | Moves upstream from mapping to **candidate-source generation**; finds domain homogeneity and a diversity–quality tradeoff. | Retrieval / generation failure |
| 2026-08-01 | [Nkisi-Orji, Salimi & Wiratunga, *Failure-Aware Matching-Based Adaptation for Generalisable Reuse*](https://link.springer.com/chapter/10.1007/978-3-032-33865-5_4) | CARM implements `construct → failure-aware accept/reject → widen retrieval → rematch` across structured CBR domains. | Adjacent: CBR adaptation / failure control |
| 2026-08-01 | [Sipp & Lieber, *An Adaptation-Guided and Efficient Case Retrieval Approach*](https://link.springer.com/chapter/10.1007/978-3-032-33865-5_3) | Defines retrieval by **minimal downstream adaptation effort**, not nearest semantic similarity. | Adjacent: CBR retrieval / adaptation |
| 2026-07 | [Wei et al., *A Survey of Reasoning-Intensive Retrieval*](https://aclanthology.org/2026.acl-long.1949/) | Shows that retrieval via latent inferential links is becoming a distinct field, directly overlapping the relational-retrieval gap. | Adjacent: reasoning-intensive retrieval |
| 2026-07 | [Zhai et al., *Abstain-R1*](https://aclanthology.org/2026.findings-acl.985/) | Demonstrates that abstention/clarification can be trained with verifiable rewards rather than expected to emerge from scale. | Adjacent: control / rejection |
| 2026-07-15 | [Chen et al., *Analogical Deep Research*](papers/06_discovery-and-causal-analogy.md#chen-2026) | Open-world retrieval and integration of analogies using mechanism alignment and cross-analogy confirmation. | Discovery / open-world analogy |
| 2026-07 | [Lu et al., *CHAIRO*](https://aclanthology.org/2026.acl-long.1692/) | End-to-end analogical retrieval + rule induction in a real application; useful as an application-level pipeline case. | Analogical induction application |
| 2026-06-11 | [Xiao et al., *Learning to Reason by Analogy via RA-RFT*](https://arxiv.org/abs/2606.13680) | Trains retrieval around **expected reasoning benefit** rather than semantic similarity and couples it to reinforcement fine-tuning. | Retrieval / training |
| 2026-05-11 | [Shen, Druckmann & Zou, *Unlocking LLM Creativity in Science through Analogical Reasoning*](https://arxiv.org/abs/2605.11258) | Uses cross-domain analogies to expand the solution space for open-ended scientific problems. | Scientific discovery |
| 2026-04-07 | [Hellwig et al., *Transformer See, Transformer Do*](https://arxiv.org/abs/2604.06501) | Small meta-trained Transformer generalizes to new alphabets and exposes a reconstructable internal algorithm. | Training / generalization / mechanism |
| 2026-04 | [Stevenson et al., *Can Large Language Models Generalize Analogy Solving Like Children Can?*](papers/05_generalization-and-failure.md#stevenson-2026) | Strong test of near/far procedural transfer: Latin → Greek → unfamiliar symbols. | Generalization |
| 2026-03-31 | [Khojasteh et al., *Enhancing Structural Mapping with LLM-derived Abstractions...* (YARN)](papers/04_structure-mapping-and-neurosymbolic.md#khojasteh-2026) | Hybrid learned representations + explicit structural mapping; abstraction-level choice remains difficult. | Mapping / neuro-symbolic |
| 2026-03-14 | [Lee et al., *The Curious Case of Analogies*](papers/03_mechanisms-and-interpretability.md#lee-2026) | Causally separates relation encoding, relation application, and structural alignment failures. | Mechanistic interpretability |
| 2026 | [Petersen et al., *Modelling Analogies and Analogical Reasoning*](papers/01_cognitive-science-bridge.md#petersen-2026) | Best current field-level orientation connecting analogy processes with NLP research. | Field synthesis |

## The working pipeline

`target representation ↔ source search → relation extraction → structural alignment → matching/adjudication → adaptation/rebinding → projection/inference → execution → validation/generalization → revision/retention`

This pipeline is the main indexing unit for the repo. A paper is classified by **which stage it actually solves or diagnoses**, not just by whether its title contains “analogy”.

## Research map

1. [Cognitive-science / field bridge](papers/01_cognitive-science-bridge.md) — modern process decompositions and their connection to AI/NLP.
2. [Architectures & training](papers/02_architectures-and-training.md) — explicit relational attention, relational bottlenecks, analogical supervision, meta-learning, latent-space constraints.
3. [Mechanisms & interpretability](papers/03_mechanisms-and-interpretability.md) — internal relation representations, alignment, access/application failures, causal interventions.
4. [Structure mapping & neuro-symbolic systems](papers/04_structure-mapping-and-neurosymbolic.md) — explicit correspondence machinery combined with learned representations.
5. [Generalization, adjudication & failure](papers/05_generalization-and-failure.md) — near/far transfer, robustness, false analogies, source diversity, association shortcuts.
6. [Discovery & open-world analogy](papers/06_discovery-and-causal-analogy.md) — source search, scientific creativity, technical invention, foresight, and multi-analogy integration.

## Current empirical picture

By August 2026 the most stable pattern is not “LLMs can” or “LLMs cannot” reason analogically. It is more specific:

- strong performance on many **provided, familiar, near-domain** analogy tasks;
- substantial brittleness under **far transfer, new symbol systems, long narratives, visual transformations, or large source banks**;
- persistent confusion between **association/surface similarity and relational correspondence**;
- evidence that correct relational representations can exist internally even when **application/output fails**;
- explicit relational architectures and carefully designed meta-learning curricula can outperform generic scaling on controlled OOD tasks;
- open-ended analogy for science, strategy, and foresight is emerging rapidly, but still depends heavily on scaffolding, retrieval design, decomposition, or human/evaluator guidance;
- several neighboring fields are independently converging on an explicit **control layer** separating representation, retrieval, applicability, rejection, reuse, verification, belief revision, and learning from failure;
- modern CBR already owns much of the `retrieve → adapt/reuse → detect failure → revise → retain` problem under explicit case representations;
- causal transportability already owns a strong formal version of `when is source→target transfer valid, and how uncertain is approximate transfer?`;
- the remaining underoccupied frontier is therefore **open-world learned transfer validity**: integrate flexible learned relational representations with adaptation/failure control and calibrated source→target validity.

See [GAP_MAP.md](GAP_MAP.md) for the capability boundary, [ADJACENT_FIELDS.md](ADJACENT_FIELDS.md) for neighboring solutions, [CONTROL_LAYER.md](CONTROL_LAYER.md) for the controller coverage matrix, [TRANSFER_VALIDITY.md](TRANSFER_VALIDITY.md) for the refined source→target validity problem, [PROGRAM_MAP.md](PROGRAM_MAP.md) for program ownership, and [FIELD_MAP.md](FIELD_MAP.md) for the broader field map.

## Inclusion rule

A paper enters the **core** corpus when it substantially illuminates at least one of these questions:

- How is the target/source represented relationally?
- How are candidate source analogies retrieved or generated?
- How are relations abstracted and structures aligned?
- How is a retrieved source adapted/rebound for the target?
- How are plausible analogies matched, ranked, partially accepted, or rejected?
- How is structure projected into a new inference or solution?
- What enables or blocks far/OOD transfer?
- What training objective or architecture improves analogical competence?
- What causal internal mechanism implements the behavior?
- How does failure revise later retrieval, representation, or memory?
- Can analogy operate in open-ended discovery rather than a closed benchmark?

Prompting papers, metaphor work, ARC/Raven work, generic relational reasoning, RAG, case-based reasoning, and causal-transfer work are **adjacent** unless they answer one of these pipeline questions directly. Adjacent fields are intentionally tracked when they solve a component that analogy research has left implicit.

## Repository policy

This repository stores metadata, analytical notes, canonical links, and reproducibility/code links. It does not mirror copyrighted PDFs by default. The goal is a lightweight research observatory that can be updated continuously and queried by mechanism, task family, evidence type, failure mode, and source→target transfer assumptions.
