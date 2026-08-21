# Analogical Reasoning Observatory

A living map of analogical reasoning research at the boundary of AI, cognitive science, and the history of theories of reasoning.

The repository tracks **mechanisms**, not merely analogy benchmarks: how models form relational representations, retrieve and align analogues, select abstraction levels, transfer structure, reject misleading analogies, and use analogy in open-ended discovery.

## Latest watchlist — August 2026

| Date | Paper | Why it matters | Category |
|---|---|---|---|
| 2026-08-04 | [Shen et al., *On the Diversity of Analogy Making in Large Language Models*](papers/05_generalization-and-failure.md#shen-2026) | Shows strong domain homogeneity and a diversity–quality trade-off; adds a neglected **candidate-generation / search-space** problem. | Generalization & failure |
| 2026-07-15 | [Chen et al., *Analogical Deep Research*](papers/06_discovery-and-causal-analogy.md#chen-2026) | Treats historical analogy as a **causal mechanism-alignment** problem and adds cross-analogy confirmation. | Discovery & causal analogy |
| 2026 | [Petersen et al., *Modelling Analogies and Analogical Reasoning*](papers/01_cognitive-science-bridge.md#petersen-2026) | Directly connects cognitive-science theories of analogy to current NLP. Best current orientation paper for this repo. | Cognitive-science bridge |
| 2026 | [Stevenson et al., *Can Large Language Models Generalize Analogy Solving Like Children Can?*](papers/05_generalization-and-failure.md#stevenson-2026) | Children and adults transfer analogy procedures to unfamiliar symbol systems much more robustly than LLMs. | Generalization & failure |
| 2026-03-31 | [Khojasteh et al., *Enhancing Structural Mapping with LLM-derived Abstractions...* (YARN)](papers/04_structure-mapping-and-neurosymbolic.md#khojasteh-2026) | Hybridizes LLM representation formation with explicit structural mapping; exposes abstraction-level selection as a remaining bottleneck. | Structure mapping / neuro-symbolic |

## Research map

1. [Cognitive-science bridge](papers/01_cognitive-science-bridge.md) — theories and modern AI/NLP translations.
2. [Architectures & training](papers/02_architectures-and-training.md) — relational bottlenecks, explicit relational attention, analogical supervision, latent-space constraints.
3. [Mechanisms & interpretability](papers/03_mechanisms-and-interpretability.md) — where relations, alignment, and abstraction live inside models.
4. [Structure mapping & neuro-symbolic systems](papers/04_structure-mapping-and-neurosymbolic.md) — explicit mapping engines combined with learned representations.
5. [Generalization, adjudication & failure](papers/05_generalization-and-failure.md) — far transfer, over-analogy, diversity collapse, invalid transfer.
6. [Discovery & causal analogy](papers/06_discovery-and-causal-analogy.md) — analogy as a tool for scientific/strategic discovery rather than closed-form analogy solving.

Structured metadata: [`data/papers.csv`](data/papers.csv)

## Historical constraint map

The historical side is treated as a source of computational constraints, not as decorative intellectual genealogy.

| Historical line | Computational question to watch |
|---|---|
| **Whewell** | representation selection; construction of conceptions; prediction; consilience; anti-ad-hoc theory growth |
| **Hesse** | positive/negative/neutral analogy; causal relevance; veto conditions on transfer |
| **Gentner / SME** | structural alignment; systematicity; candidate inference |
| **Holyoak–Thagard / ACME, LISA** | multi-constraint mapping; goal sensitivity; role binding; working-memory limits |
| **Hofstadter / Copycat** | representation plasticity; conceptual slippage; analogy and perception co-determine one another |

A useful working decomposition is:

`representation formation → source retrieval → relational abstraction → structural alignment → transfer licensing → negative-analogy veto → prediction → cross-domain validation`

## Inclusion rule

A paper enters the core list when it does at least one of the following:

- changes the **training objective** or data-generation principle for analogical transfer;
- introduces an **architectural inductive bias** for relational abstraction;
- identifies a **causal/mechanistic internal process** rather than reporting benchmark accuracy alone;
- implements explicit **structure mapping / constraint satisfaction** with learned representations;
- isolates a failure mode relevant to **far transfer, analogy selection, rejection, or theory discovery**;
- makes a serious bridge between cognitive theories of analogy and modern AI.

Prompt-only analogy tricks and generic historical-QA agents are tracked only when they reveal a mechanism useful to the above map.

## Repository policy

This repository stores metadata, analytical notes, and links to canonical papers/code. It does not mirror copyrighted PDFs by default. The aim is to stay lightweight enough for continuous updates and eventual contact with researchers working on specific mechanism gaps.
