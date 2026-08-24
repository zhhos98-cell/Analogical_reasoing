# Historical Analogies for Forecasting — Six Computational Forms

Historical analogy already has a forecasting tradition outside modern LLM work. The useful comparison is not old vs new, but **what counts as the analogue and how history enters the forecast**.

---

## 1. Structured expert analogy — humans name and adjudicate cases

**Green & Armstrong, “Structured analogies for forecasting,” International Journal of Forecasting 23 (2007), 365–376.**  
Canonical: https://doi.org/10.1016/j.ijforecast.2007.05.005

Experts list relevant past cases, rate similarity to the target, and map historical outcomes onto possible target outcomes. Across eight conflict situations, unaided expert forecasts were 32% accurate; structured analogies reached 46%; when experts produced at least two analogies and had direct experience with the closest one, accuracy reached 60%.

`human source generation → explicit similarity judgment → outcome mapping → forecast`.

This is the clean pre-LLM baseline. Its main weakness is source-search bandwidth; its strength is explicit human applicability judgment.

---

## 2. Statistical historical episodes — predictions as portfolios of past periods

**Goulet Coulombe, Göbel & Klieber, “Dual Interpretation of Machine Learning Forecasts,” 2025/26.**  
Canonical: https://arxiv.org/abs/2412.13076

A broad class of ML forecasts can be rewritten as weighted combinations of training observations. In macroeconomic forecasting the weights become interpretable proximity measures between the target and past economic periods.

`current macro state → model-implied historical weights → weighted historical outcomes → forecast`.

This makes historical analogy mathematically inspectable. It is strong on quantification and weak on mechanism: predictor-space proximity need not imply causal equivalence.

---

## 3. Historical trajectory analogy — retrieve a similar past shape

### Conflict: Shape Finder / PaCE

**Schincariol, Frank & Chadefaux, Journal of Peace Research, 2025.**  
Canonical: https://doi.org/10.1177/00223433251330790

Past UCDP fatality sequences are retrieved through Dynamic Time Warping; their realized futures are aggregated into a predictive distribution.

`current conflict trajectory → similar historical trajectories → realized futures → forecast + intervals`.

The method is especially interesting because historical analogues generate uncertainty directly through dispersion among precedent futures.

### Epidemics: HAL-Net

**Zhang & Ji, Expert Systems with Applications 299 (2026), 130038.**  
Canonical: https://doi.org/10.1016/j.eswa.2025.130038

HAL-Net learns analogous epidemic trajectories and injects them into a deep forecasting architecture. It reports sizeable MAE/RMSE improvements across ten-country COVID data.

The analogue in both systems is temporal/geometric rather than an interpreted event mechanism.

---

## 4. Contextual regime analogy — retrieve a historically similar state

### History Rhymes

**Khanna et al., “History Rhymes: Macro-Contextual Retrieval for Robust Financial Forecasting,” IEEE Big Data 2025.**  
Canonical: https://arxiv.org/abs/2511.09754

The system jointly embeds financial-news text and macro variables and retrieves only earlier periods with similar macroeconomic context.

`current text + macro regime → earlier comparable regime → context-conditioned forecast`.

This is richer than trajectory shape because several contextual dimensions define the precedent. It is still weaker than mechanism analogy because proximity is learned rather than causally licensed.

---

## 5. Historical experience as a prior — history changes what the model attends to

### Stevanovic 2026 — Who Saw It Coming?

**Dalibor Stevanovic, “Who Saw It Coming? Historical Experience and the 2021 Inflation Forecast Failure.”**  
Canonical: https://arxiv.org/abs/2604.14467

This paper adds a distinct historical-analogy mechanism. The key issue is not retrieval of a named precedent but **how strongly different historical regimes are weighted when forming expectations**.

The 2021 inflation miss is attributed primarily to sample composition: Great Moderation-dominated samples underweight supply-shock regimes. Three historically informed adjustments — an intercept correction, similarity re-estimation using 1970s data, and kernel weighting — substantially shrink the forecast gap and generalize to eight additional U.S. price indices.

The human evidence is parallel: respondents over 60, whose lived experience includes 1970s inflation, formed higher early-2021 inflation expectations than younger cohorts.

A controlled LLM experiment then conditions models on “experienced” vs “young” professional-economist personas while holding the presented data/context fixed. The resulting forecasts differ systematically; the paper concludes that **the source of the prior matters more than model sophistication** across its three exercises.

This gives a different computational form:

`historical experience / sample composition → prior over relevant regimes → current forecast`.

### Why it matters

Historical analogy need not appear as an explicit sentence of the form “2021 is like the 1970s.” The same epistemic effect can arise through **differential weighting of historical regimes** before a precedent is consciously named.

For AI systems, this raises a new control question: should precedent selection be understood only as retrieval, or also as learned/induced **attention over historical experience**?

---

## 6. Mechanism-level event analogy — retrieve several past causal structures

### CANA / Analogical Deep Research

**Chen et al., 2026.**  
Canonical: https://arxiv.org/abs/2607.13602

CANA decomposes events into preconditions, temporal chains, mechanisms and outcomes, retrieves several partial historical analogies, records each analogy's limitations, and uses repeated structural roles across cases to infer hidden factors and possible target trajectories.

`partially observed event → causal/structural representation → multiple historical sources → role alignment + limitations → hidden-factor inference → foresight`.

This is the richest current explicit historical-analogy forecasting system in the branch.

An important calibration is that CANA already includes **difference awareness** and analogy differentiation. The unsolved step is no longer simply “identify disanalogies,” but to use those differences as executable controls over individual projected claims.

---

# Two axes, not one progression

The six forms cannot be placed on a single scale. They differ along at least two axes:

### A. Semantic richness

`observation → trajectory → regime/context → event → mechanism`.

### B. How history enters inference

`explicit retrieved source`

vs

`implicit weighted historical experience/prior`.

This distinction matters. Stevanovic's experienced-forecaster experiment can change a forecast without selecting a single named analogue, while CANA explicitly names and compares precedents.

---

# The representation–calibration frontier

Narrow historical analogue systems have an empirical advantage:

- they can be scored out of sample;
- source selection can be tested against realized outcomes;
- analogue dispersion can become uncertainty intervals;
- historical contamination is easier to police.

Rich event/mechanism systems have a semantic advantage:

- they can represent institutions, actors and causal roles;
- they can explain why a precedent matters;
- they can combine partial analogues;
- they can surface historical differences.

But they are harder to validate because there is rarely one uncontested oracle historical mechanism.

The engineering target is therefore not simply “make CANA more causal” or “make trajectory models use LLMs.” It is:

> **move calibration, uncertainty and transfer-control discipline upward into semantically rich historical event representations.**

---

# Remaining forecasting gaps

A serious event-level historical-analogy forecaster needs to separate:

- **source fit** — does the historical case share the relevant mechanism?
- **source weight** — how much should this precedent influence the target relative to other history?
- **transferable claim** — exactly which outcome/relation is licensed?
- **disanalogy effect** — which projected claim is weakened or blocked by each difference?
- **source dependence** — are several precedents genuinely independent evidence?
- **forecast uncertainty** — can the precedent set yield calibrated bounds rather than prose confidence?
- **temporal hygiene** — is later knowledge of the target leaking into source selection or evaluation?

Current systems each solve subsets. None found in this sweep unifies all of them for open-ended historical events.
