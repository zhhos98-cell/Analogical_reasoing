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
- [`CANA_CLOSE_READ.md`](CANA_CLOSE_READ.md) — close read of ADR-bench, CANA's forward/historical split and the theory's separation of structural-identification error from mechanism-transfer error.
- [`HISTORICAL_TRANSFER_BENCH.md`](HISTORICAL_TRANSFER_BENCH.md) — benchmark design for selective historical transfer: hard negatives, partial transfer, no-valid-precedent cases, competing representations, hindsight arms, dependence controls and longitudinal applicability memory.
- [`HISTORICAL_TRANSFER_BENCH_EXTENSIONS.md`](HISTORICAL_TRANSFER_BENCH_EXTENSIONS.md) — case-vs-class conflict, competing-precedent diagnosticity, salience robustness, chronological replay and incremental-value ablations.
- [`CLAIM_STRENGTH_AND_ACTION.md`](CLAIM_STRENGTH_AND_ACTION.md) — separates historical relevance/mechanism warnings, directional forecasts, numerical probabilities and action recommendations; measures claim-strength overreach.
- [`PROCESS_TRACING_FOR_HISTORICAL_ANALOGY.md`](PROCESS_TRACING_FOR_HISTORICAL_ANALOGY.md) — represents historical transfer as `mechanism × phase × critical juncture`, rather than timeless event-DAG similarity.
- [`BOUNDARY_FAILURE_TAXONOMY.md`](BOUNDARY_FAILURE_TAXONOMY.md) — typed failure credit assignment: boundary not retrieved, not represented, not applied, phase ignored, reference class stale, probability integration failure or claim-scope mismatch.
- [`BENCH_DATA_FEASIBILITY.md`](BENCH_DATA_FEASIBILITY.md) — layered data architecture using resolved forecasting corpora, event streams, deep cases and simulated worlds rather than hand-writing every benchmark item.
- [`BTF3.md`](BTF3.md) — BTF-3 as a 1,907-question frozen environment for large-scale transfer ablations, including a numeric forecast track.
- [`PATTERN_BREAK_FAILURES.md`](PATTERN_BREAK_FAILURES.md) — three resolved BTF-2 failures where the historical pattern was genuine and the blocking difference was available, but the forecast still failed to operationalize the boundary.
- [`APPLICATION_DOMAINS.md`](APPLICATION_DOMAINS.md) — foreign policy, conflict forecasting, epidemics, macro/finance, military/intelligence and technology/foresight applications.
- [`FORECASTING_ANALOGIES.md`](FORECASTING_ANALOGIES.md) — six forecasting forms: structured expert cases, statistical episodes, trajectory analogues, contextual regimes, historical-experience priors, and mechanism-level event analogies.
- [`FORECASTING_CONTROLLER.md`](FORECASTING_CONTROLLER.md) — OpenForecaster/FutureSim as evidence that calibration, proper scoring and long-horizon update behavior can be specifically trained/evaluated rather than left to generic LLM reasoning.
- [`FORECASTING_JUDGMENT_EVIDENCE.md`](FORECASTING_JUDGMENT_EVIDENCE.md) — forecasting-tournament evidence that analogy presence alone is a weak quality marker; broader reasoning discipline and rationale–forecast alignment matter more.
- [`REFERENCE_CLASS_BRIDGE.md`](REFERENCE_CLASS_BRIDGE.md) — outside-view/reference-class forecasting as a calibration neighbor to rich historical precedent reasoning.
- [`CASE_CLASS_HYBRID.md`](CASE_CLASS_HYBRID.md) — prior art showing that analogy + outside view is already an established forecasting hybrid; includes leakage-aware macro-analog actor–critic evidence and isolates the narrower foundation-model frontier.
- [`COMPETING_HYPOTHESES_BRIDGE.md`](COMPETING_HYPOTHESES_BRIDGE.md) — intelligence-analysis and Bayesian-process-tracing controls: alternative precedents, evidence diagnosticity, disconfirmation, and the warning that procedural structure without calibration can worsen judgment.
- [`COVERAGE_AND_SALIENCE_PRIORS.md`](COVERAGE_AND_SALIENCE_PRIORS.md) — tests whether canonical/high-coverage historical sources are retrieved because of parametric familiarity rather than downstream structural utility.
- [`BOUNDARY_MEMORY.md`](BOUNDARY_MEMORY.md) — OBAM/ForecastCompass/WorldReasoner prior art for learning discriminative failure boundaries and resolved-outcome memory; narrows the historical gap to relation/projection-specific applicability memory.
- [`LIVE_CRISIS_ANALOGY.md`](LIVE_CRISIS_ANALOGY.md) — post-cutoff live-crisis evidence that strong models can sometimes contextualize a supplied historical precedent when strategic conditions change.
- [`MECHANISM_VALIDATION.md`](MECHANISM_VALIDATION.md) — causal-pathway abstraction, falsification and event-causality benchmarks as a way to validate mechanism hypotheses rather than trust one generated event DAG.
- [`REPRESENTATION_LADDER.md`](REPRESENTATION_LADDER.md) — analogue representations from weighted historical observations through trajectory/regime/event schemas to causal structural roles; tracks the semantic-richness vs calibration tradeoff.
- [`TEMPORAL_VALIDATION.md`](TEMPORAL_VALIDATION.md) — hindsight-control infrastructure: CANA temporal compliance, cutoff prompting/MHEB, HindsightBench, Ranke-4B and vintage-consistent forecasting; proposes source-selection/mapping-level hindsight tests.
- [`EVIDENCE_DEPENDENCE.md`](EVIDENCE_DEPENDENCE.md) — why several precedents may not provide several independent confirmations; distinguishes institutional, diffusion, technological, source and historiographic dependence.
- [`RISK_AND_PERSUASION.md`](RISK_AND_PERSUASION.md) — evidence that historical analogy and AI-generated historical framing can increase confidence or shift attitudes; defines the untested but plausible confident-false-precedent risk.
- [`LEGAL_PRECEDENT_CONTROL.md`](LEGAL_PRECEDENT_CONTROL.md) — legal AI as an adjacent control model: analogical precedent retrieval, distinguishing, conflicting-precedent reliability/calibration, abstention and verified support paths.
- [`TECH_DEFENSE_PRECEDENT.md`](TECH_DEFENSE_PRECEDENT.md) — historical technology deployment as ML evidence plus the older military case-based planning/decision-support tradition.
- [`COMPUTATIONAL_PREHISTORY.md`](COMPUTATIONAL_PREHISTORY.md) — Mefford, Schrodt and the 1980s–90s AI/international-politics precedent line; prevents false novelty claims about computational historical analogy.
- [`../data/historical_analogy_applications.csv`](../data/historical_analogy_applications.csv) — structured application map.
- [`../data/historical_analogy_validation.csv`](../data/historical_analogy_validation.csv) — temporal-validation, calibration, source-selection and persuasion-risk evidence map.
- [`../data/historical_transfer_bench_schema.csv`](../data/historical_transfer_bench_schema.csv) — proposed structured schema for benchmark cases.
- [`../data/pattern_break_cases.csv`](../data/pattern_break_cases.csv) — machine-readable seed failures for boundary-sensitive transfer experiments.

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

The BTF pattern-break cases make the failure more concrete: the model can possess both the recurring source pattern and evidence of the target-side boundary, yet still fail to make the difference change its forecast. But not every bad pattern forecast fails at that stage. Resolved traces now support a typed diagnosis: some agents never retrieve the critical boundary; others retrieve/represent it but fail to execute a veto; others derive useful evidence correctly and only fail during probability integration. Transfer learning therefore needs **pipeline-level failure credit assignment** before applicability memory is updated.

Historical time matters internally to the analogy, not only as a knowledge cutoff. The same mechanism can imply different outcomes at different process phases. The current extension represents transfer as `(mechanism, phase, critical juncture, projection)`: a source may be useful before a terminal state/election/institutional transition but invalid across it.

A further calibration is **claim strength**. A precedent may strongly license `mechanism X is relevant` while weakly licensing `outcome probability is 0.70`, and not license a policy action at all. Historical systems therefore need a maximum-licensed-claim-strength state as well as a transfer label; otherwise useful qualitative warnings are either discarded or inflated into false numerical/action certainty.

The remaining conclusions are detailed in the linked notes: representation/calibration tradeoffs, temporal validity, dependence control, outside-view baselines, forecasting-specific calibration, salience stress tests, applicability memory, CANA's `δ_s` vs `α_s^tr` distinction, mechanism falsification and persuasion risk.