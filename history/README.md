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
- historical roleplay or time-locked models unless they directly test historical analogy;
- ordinary RAG over historical documents;
- historical research automation without source→target analogical transfer.

## Start here

- [`HISTORICAL_ANALOGY.md`](HISTORICAL_ANALOGY.md) — current direct LLM line and revised capability/gap assessment; includes the important calibration that CANA already models per-analogy limitations and difference awareness.
- [`APPLICATION_DOMAINS.md`](APPLICATION_DOMAINS.md) — foreign policy, conflict forecasting, epidemics, macro/finance, military/intelligence and technology/foresight applications.
- [`FORECASTING_ANALOGIES.md`](FORECASTING_ANALOGIES.md) — lineage from structured expert analogy to statistical episodes, trajectory matching and mechanism-level event analogy.
- [`REPRESENTATION_LADDER.md`](REPRESENTATION_LADDER.md) — analogue representations from weighted historical observations through trajectory/regime/event schemas to causal structural roles; tracks the semantic-richness vs calibration tradeoff.
- [`COMPUTATIONAL_PREHISTORY.md`](COMPUTATIONAL_PREHISTORY.md) — Mefford, Schrodt and the 1980s–90s AI/international-politics precedent line; prevents false novelty claims about computational historical analogy.
- [`../data/historical_analogy_applications.csv`](../data/historical_analogy_applications.csv) — structured application map.

## Current calibration

The direct modern LLM core remains small but clear:

`Past Meets Present (ACL 2025)`

`→ historical analogue acquisition`

`→ Analogical Deep Research / CANA (2026)`

`→ mechanism-aligned retrieval + explicit per-analogy limitations + differentiated multi-precedent integration`.

Surrounding applications are technically more mature in narrower representations: conflict and epidemic trajectory matching, macroeconomic episode decomposition, temporal knowledge-graph replay, and macro-contextual precedent retrieval.

The sharpest remaining frontier is **not simply disanalogy detection**. CANA already scores where an analogy breaks and includes per-analogy limitations in its Structural Analogy Brief. The harder unresolved step is to turn those limitations into **projection-level transfer control**:

`p1 licensed / p2 conditional / p3 vetoed / p4 requires evidence`,

with calibrated uncertainty, competing mechanism representations, dependence-aware multi-precedent evidence and persistent applicability memory.

A second high-level result is the current **representation/calibration frontier**: narrow historical analogues (past observations, trajectories, macro regimes) can be tested rigorously out of sample, while semantically rich event/mechanism analogies are much harder to calibrate. The interesting engineering target is to move the former's empirical discipline upward without flattening the latter's historical structure.
