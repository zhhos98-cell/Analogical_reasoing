# Historical Analogies for Forecasting — Four Computational Forms

Historical analogy already has a forecasting tradition outside modern LLM work. The useful comparison is not old vs new, but **what counts as the analogue**.

## 1. Structured expert analogy — cases named and judged by humans

**Green & Armstrong, “Structured analogies for forecasting,” International Journal of Forecasting 23 (2007), 365–376.**  
Canonical: https://doi.org/10.1016/j.ijforecast.2007.05.005

Experts list relevant past cases, rate their similarity to the target, and map historical outcomes onto possible target outcomes. Across eight conflict situations, unaided expert forecasts were 32% accurate; structured analogies reached 46%; when experts produced at least two analogies and had direct experience with the closest one, accuracy reached 60%.

This is the clean pre-LLM baseline for modern historical-analogy systems:

`human source generation → explicit similarity judgment → outcome mapping → forecast`.

Its weakness is source-search bandwidth and human availability/surface bias. Its strength is that the human owns applicability judgment.

---

## 2. Statistical historical episodes — the model prediction as a portfolio of past periods

**Goulet Coulombe, Göbel & Klieber, “Dual Interpretation of Machine Learning Forecasts,” OeNB Working Paper 265 (2025); presented at AEA 2026.**  
Canonical: https://www.oenb.at/en/Publications/Economics/Working-Papers/2025/working-paper-265.html

A broad class of ML forecasts can be rewritten as weighted combinations of training observations. In macroeconomic time series, those weights become interpretable proximity scores between current conditions and past economic episodes. The authors apply the method to post-pandemic inflation, GDP growth and recession probabilities.

`current macro state → model-implied proximity weights over historical periods → weighted historical outcomes → forecast`.

This makes “historical analogy” mathematically inspectable inside standard ML models. It is strong on quantification and weak on historical mechanism: proximity in predictor space need not mean causal or structural analogy.

---

## 3. Historical trajectory analogy — retrieve a similar past shape

**Zhang & Ji, “HAL-Net: A Historical Analogy Learning Network for Adaptive and Interpretable Pandemic Forecasting,” Expert Systems with Applications 299 (2026), 130038.**  
Canonical: https://doi.org/10.1016/j.eswa.2025.130038

HAL-Net uses Dynamic Time Warping to identify analogous historical epidemic trajectories and feeds them into a deep forecasting architecture. Across COVID-19 data for ten countries, it reports average MAE improvements above 28% and RMSE improvements above 32% over its strongest baseline.

`current trajectory → analogous past trajectory/lag → neural forecast`.

The analogue is richer than a single timestamp but still primarily geometric/temporal, not an interpreted historical event.

---

## 4. Mechanism-level event analogy — retrieve several past causal structures

**Chen et al., “Analogical Deep Research,” 2026.**  
Canonical: https://arxiv.org/abs/2607.13602

CANA treats historical forecasting as a structural/causal problem. It decomposes events into preconditions, temporal chains, mechanisms and outcomes, retrieves several partial historical analogies, and uses repeated structural roles across cases to infer hidden factors and possible future trajectories.

`partially observed event → causal/structural representation → multiple historical cases → role alignment → cross-case hidden factor → foresight`.

This is the closest current system to the old structured-analogy forecasting ideal, but with machine source search and explicit mechanism representations.

---

# The progression

These systems can be ordered by the **representation of historical similarity**:

`named case similarity`

→ `statistical proximity`

→ `trajectory-shape similarity`

→ `mechanism / causal-role alignment`.

This is useful because the models solve different problems. HAL-Net can be extremely effective without understanding “history” in a human sense; CANA attempts historical event reasoning but inherits much harder questions about contested causality, source independence and transfer validity.

# The remaining forecasting gap

The frontier is not simply better analogue retrieval. A serious event-level system must separate:

- **source fit** — does this historical case share the relevant mechanism?
- **transferable claim** — which outcome/relationship from the source is actually licensed in the target?
- **disanalogy** — what changed enough to block the historical lesson?
- **independence** — are multiple precedents genuinely independent evidence?
- **temporal information hygiene** — is the forecast contaminated by knowing how the target eventually ended?

Modern historical-analogy forecasting has moved decisively from `history repeats itself` as rhetoric toward explicit computational representations, but claim-level transfer control remains weak.