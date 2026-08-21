# Historical Analogy Branch

This branch tracks **historical analogy as a reasoning technology**, not AI-for-history generally.

Core scope:

- retrieve or generate a past event as an analogue for a present target;
- align historical cases by mechanism rather than topical similarity;
- use one or several historical analogies for foresight / decision support;
- detect historical analogies used by political actors as signals of reasoning or intent;
- evaluate when a historical precedent licenses, fails to license, or only partially licenses a target inference.

Out of scope by default:

- generic history QA or history agents;
- archival OCR / transcription / database construction;
- historical roleplay or time-locked models **unless used as validation infrastructure for analogy/foresight**;
- ordinary RAG over historical documents;
- historical research automation without source→target analogical transfer.

## Start here

- [`HISTORICAL_ANALOGY.md`](HISTORICAL_ANALOGY.md) — current direct LLM line and revised capability/gap assessment; includes the important calibration that CANA already models per-analogy limitations and difference awareness.
- [`HISTORICAL_TRANSFER_BENCH.md`](HISTORICAL_TRANSFER_BENCH.md) — benchmark design for selective historical transfer: hard negatives, partial transfer, no-valid-precedent cases, competing representations, hindsight arms, dependence controls and longitudinal applicability memory.
- [`APPLICATION_DOMAINS.md`](APPLICATION_DOMAINS.md) — foreign policy, conflict forecasting, epidemics, macro/finance, military/intelligence and technology/foresight applications.
- [`FORECASTING_ANALOGIES.md`](FORECASTING_ANALOGIES.md) — six forecasting forms: structured expert cases, statistical episodes, trajectory analogues, contextual regimes, historical-experience priors, and mechanism-level event analogies.
- [`REFERENCE_CLASS_BRIDGE.md`](REFERENCE_CLASS_BRIDGE.md) — outside-view/reference-class forecasting as a calibration neighbor to rich historical precedent reasoning.
- [`CASE_CLASS_HYBRID.md`](CASE_CLASS_HYBRID.md) — prior art showing that analogy + outside view is already an established forecasting hybrid; includes leakage-aware macro-analog actor–critic evidence and isolates the narrower foundation-model frontier.
- [`COMPETING_HYPOTHESES_BRIDGE.md`](COMPETING_HYPOTHESES_BRIDGE.md) — intelligence-analysis and Bayesian-process-tracing controls: alternative precedents, evidence diagnosticity, disconfirmation, and the warning that procedural structure without calibration can worsen judgment.
- [`REPRESENTATION_LADDER.md`](REPRESENTATION_LADDER.md) — analogue representations from weighted historical observations through trajectory/regime/event schemas to causal structural roles; tracks the semantic-richness vs calibration tradeoff.
- [`TEMPORAL_VALIDATION.md`](TEMPORAL_VALIDATION.md) — hindsight-control infrastructure: CANA temporal compliance, cutoff prompting/MHEB, HindsightBench, Ranke-4B and vintage-consistent forecasting; proposes source-selection/mapping-level hindsight tests.
- [`EVIDENCE_DEPENDENCE.md`](EVIDENCE_DEPENDENCE.md) — why several precedents may not provide several independent confirmations; distinguishes institutional, diffusion, technological, source and historiographic dependence.
- [`RISK_AND_PERSUASION.md`](RISK_AND_PERSUASION.md) — evidence that historical analogy and AI-generated historical framing can increase confidence or shift attitudes; defines the untested but plausible confident-false-precedent risk.
- [`LEGAL_PRECEDENT_CONTROL.md`](LEGAL_PRECEDENT_CONTROL.md) — legal AI as an adjacent control model: analogical precedent retrieval, distinguishing, conflicting-precedent reliability/calibration, abstention and verified support paths.
- [`TECH_DEFENSE_PRECEDENT.md`](TECH_DEFENSE_PRECEDENT.md) — historical technology deployment as ML evidence plus the older military case-based planning/decision-support tradition.
- [`COMPUTATIONAL_PREHISTORY.md`](COMPUTATIONAL_PREHISTORY.md) — Mefford, Schrodt and the 1980s–90s AI/international-politics precedent line; prevents false novelty claims about computational historical analogy.
- [`../data/historical_analogy_applications.csv`](../data/historical_analogy_applications.csv) — structured application map.
- [`../data/historical_analogy_validation.csv`](../data/historical_analogy_validation.csv) — temporal-validation and persuasion-risk evidence map.
- [`../data/historical_transfer_bench_schema.csv`](../data/historical_transfer_bench_schema.csv) — proposed structured schema for benchmark cases.

## Current calibration

The direct modern LLM core remains small but clear:

`Past Meets Present (ACL 2025)`

`→ historical analogue acquisition`

`→ Analogical Deep Research / CANA (2026)`

`→ mechanism-aligned retrieval + explicit per-analogy limitations + differentiated multi-precedent integration`.

Surrounding applications are technically more mature in narrower representations: conflict and epidemic trajectory matching, macroeconomic episode decomposition, temporal knowledge-graph replay, macro-contextual precedent retrieval, and ML over historical technology deployments. A separate macroeconomic line shows that history can also enter as a **prior over which past regimes deserve weight**, without any named precedent being explicitly retrieved.

The sharpest remaining frontier is **not simply disanalogy detection**. CANA already scores where an analogy breaks and includes per-analogy limitations in its Structural Analogy Brief, while ARN shows that near/far analogies and disanalogies can be benchmarked systematically in narrative tasks. The harder unresolved step is to turn a historical difference into **projection-level transfer control**:

`p1 licensed / p2 conditional / p3 vetoed / p4 requires evidence`,

with calibrated uncertainty, competing mechanism representations, dependence-aware multi-precedent evidence and persistent applicability memory. A targeted negative search in this branch has not yet found a general open-event system that makes this projection-level license/veto object explicit; treat that as a **high-confidence open frontier, not a proof of absence**.

A second high-level result is the current **representation/calibration frontier**: narrow historical analogues (past observations, trajectories, macro regimes) can be tested rigorously out of sample, while semantically rich event/mechanism analogies are much harder to calibrate. The interesting engineering target is to move the former's empirical discipline upward without flattening the latter's historical structure.

A third result is historical continuity in the engineering problem itself. 1980s–2000s foreign-policy and military AI already explored precedent-based logic, case reuse/adaptation and difference-aware decision support. Foundation models reverse the old bottleneck: representation/search is dramatically more flexible, while explicit applicability control remains comparatively underdeveloped.

A fourth result is that **temporal validity must be treated as part of analogy validity**. A report can obey an explicit cutoff while source selection and mapping are still influenced by parametric knowledge of the target's realized future. Historical-analogy evaluation therefore needs temporal controls at more than the final-text layer: prompt-level cutoff tests, black-box hindsight audits, and where possible hard time-locked or vintage-consistent baselines.

A fifth result is that **multi-precedent confirmation needs dependence control**. CANA already filters obvious identity/sibling-trivial cases and its theory explicitly requires conditional independence. The unresolved part is subtler historical dependence: policy diffusion, institutional genealogy, technological lineage, common shocks, shared source datasets and historiographic inheritance can make several analogies behave like fewer independent observations.

A sixth result is that **case analogy + outside view is not itself a new hybrid**. Lovallo, Clarke & Camerer (2012) already showed that a reference class of analogies can outperform a few familiar analogies and introduced similarity-based forecasting as a case-based/reference-class hybrid. Modern ML/RCF and 2026 DoD AI–RCF work further automate class construction and probability calibration. Leakage-aware macro-analog work in 2026 adds an LLM critic that compresses historical analogs into tactical rules, but a simple kNN analog baseline recovers a comparable median signal. The genuinely open problem is therefore to demonstrate incremental value from mechanism-rich LLM precedent reasoning over strong, time-safe analogue/reference-class baselines.

A seventh result is that **competing-hypothesis machinery is a useful control neighbor but not a free cure**. Intelligence-analysis experiments and reviews find weak or sometimes harmful aggregate effects from formal ACH procedures, while 2026 Bayesian-process-tracing benchmarks show frontier LLMs can be internally coherent yet systematically over-weight evidence. Historical analogy therefore needs diagnosticity and disconfirmation controls that are themselves empirically calibrated, not merely more elaborate reasoning prose.

Finally, historical analogies are not rhetorically neutral. Experimental political-science evidence shows analogy-based justifications can increase confidence in leaders' decisions, while separate 2026 experiments show factually accurate LLM-generated historical framing can shift opinions. No direct study found here yet establishes the full chain from **AI-generated historical analogy to human decision change**, but the combined evidence makes precision/calibration a deployment-safety issue rather than a benchmark detail.
