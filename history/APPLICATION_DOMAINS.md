# Application Domains — Where Historical Analogy Is Actually Being Computed

**Snapshot: 21 August 2026.**

This note scans application domains that routinely reason from precedent and asks a stricter question than “does AI appear here?”:

> **Is a past episode being represented, retrieved, matched, or propagated as an analogue for a present target?**

The scan reveals three distinct computational forms. They should not be collapsed because they solve different problems and expose different gaps.

---

## 1. Event / mechanism analogies — foreign policy and foresight

### Past Meets Present — historical source acquisition

**Li et al., ACL 2025 Outstanding Paper.**  
Canonical: https://aclanthology.org/2025.acl-long.200/

The system retrieves or generates past historical events for a target event and evaluates analogy quality along multiple dimensions. Self-reflection is used to reduce hallucination and stereotyped parallels.

**Application role:** enlarge the analyst's candidate-precedent set.

**What is computationalized:** source acquisition.

**What remains human-like and weak:** deciding what lesson, if any, the retrieved case licenses.

---

### CANA / Analogical Deep Research — mechanism-level foresight

**Chen et al., 2026.**  
Canonical: https://arxiv.org/abs/2607.13602

CANA decomposes historical and target events into preconditions, temporal chains, mechanisms, outcomes and structural roles. It searches for multiple partial analogues and combines repeated roles across cases to infer hidden target factors and conditional trajectories.

The benchmark includes financial, geopolitical and technology events and deliberately withholds mention of historical analogy from the natural task prompt: agents must choose to exploit history through their architecture rather than because the prompt tells them to.

**Application role:** foresight under partial observability.

**What is computationalized:** mechanism-oriented source retrieval, structural alignment, multi-case integration.

**Main frontier:** source mechanisms are themselves uncertain/contestable; claim-level transfer licensing and dependence-aware confirmation remain weak.

---

### Tsvetkova — historical analogy as an intelligence signal

**Natalia Tsvetkova, Humanities and Social Sciences Communications, 2026.**  
Canonical: https://doi.org/10.1057/s41599-026-06930-9

An LLM screens roughly 1,100 presidential documents and detects past→present analogies already articulated by leaders. Every candidate is manually reviewed and coded as cognitive, rhetorical, or signaling. The system is therefore not inventing a policy analogy: it is identifying when a decision-maker appears to have adopted one.

**Application role:** open-source indicator of emerging policy orientation.

**What is computationalized:** high-recall detection of actor-used historical mappings in large textual corpora.

**Main frontier:** analogy occurrence is a correlative signal rather than proof of causal influence; a usable warning system needs calibrated base rates and negative cases.

---

## 2. Historical trajectory analogies — conflict and epidemic early warning

This line is computationally more mature than event-level LLM analogy, but its representation is narrower: a historical case is primarily a **trajectory shape**.

### Shape Finder / PaCE — armed-conflict forecasting

**Thomas Schincariol, Hannah Frank & Thomas Chadefaux, Journal of Peace Research 62(6), 2025.**  
Canonical: https://doi.org/10.1177/00223433251330790  
Current methodology: https://forecastlab.org/methodology/

The system partitions historical UCDP fatality series into windows, uses Dynamic Time Warping to retrieve analogous historical sequences across countries/periods, follows each match forward, then aggregates their realized futures into a forecast. The PaCE implementation provides empirical predictive distributions and uncertainty intervals.

`current conflict trajectory → nearest historical shapes → realized historical futures → predictive mixture`.

The 2025 paper shows the method can preserve overall forecast accuracy while better capturing sudden surges and declines than conservative baseline models; it performs especially well for high-intensity, high-variability cases. PaCE reports tests across country, region and period boundaries.

**Application role:** conflict escalation/de-escalation early warning.

**What is computationalized:** analogue retrieval, future propagation, uncertainty from analogue dispersion.

**Main limitation:** predictive, not causal. A similar fatality shape can arise from different strategic mechanisms. The method can say “this trajectory resembles these past trajectories,” not yet “the underlying political mechanism is the same.”

### VIEWS conflict signatures — current exploratory bridge

At ISA 2026, VIEWS reported exploratory work on `conflict signatures`: structured trajectory profiles using level, trend, acceleration, volatility and persistence, explicitly motivated by practitioners who reason in terms of situations and comparisons rather than point forecasts. The project notes potential convergence with PaCE-style historical matching.

Canonical: https://viewsforecasting.org/news/p-von-der-maase-presents-new-work-on-conflict-signatures-at-isa-2026/

This is worth watching because it pushes trajectory analogy toward a richer interpretable representation without yet claiming causal event analogy.

---

### HAL-Net — pandemic forecasting

**Chengying Zhang & Donghong Ji, Expert Systems with Applications 299 (2026), 130038.**  
Canonical: https://doi.org/10.1016/j.eswa.2025.130038

HAL-Net uses Dynamic Time Warping to learn a historical analogue lag and integrates it into a deep forecasting architecture. On COVID-19 data from ten countries, the authors report average MAE reductions above 28% and RMSE reductions above 32% relative to their strongest baseline.

**Application role:** interpretable epidemic trend forecasting under non-stationarity.

**What is computationalized:** historical trajectory matching inside the forecasting architecture.

**Limit:** the analogue remains a temporal pattern rather than an interpreted event/mechanism.

---

## 3. Macro-regime / historical-episode analogies — economics and finance

This line is especially important because it makes historical analogy mathematically inspectable rather than a narrative afterthought.

### Dual Interpretation of Machine Learning Forecasts

**Philippe Goulet Coulombe, Maximilian Göbel & Karin Klieber, OeNB Working Paper 265; AEA 2026 presentation.**  
Canonical: https://arxiv.org/abs/2412.13076

For ridge regression, random forests, boosted trees and neural networks, an out-of-sample forecast can be rewritten as a linear combination of historical target values. The weights become pairwise proximity measures between current conditions and past economic periods.

`current macro conditions → model-implied historical proximity portfolio → forecast`.

Applications include post-pandemic inflation, GDP growth and recession probabilities. The historical analogy is not separately bolted onto the model; it is excavated from the model's dual representation.

**Application role:** explain black-box macro forecasts to analysts/policymakers through specific past episodes.

**What is computationalized:** graded similarity/dissimilarity to the whole historical sample and exact contribution of each past period.

**Main limitation:** model proximity is not necessarily historical mechanism equivalence.

---

### History Rhymes — macro-contextual retrieval for OOD financial forecasting

**Khanna et al., IEEE Big Data 2025; public summary June 2026.**  
Canonical preprint: https://arxiv.org/abs/2511.09754

The system jointly embeds financial-news text and macroeconomic indicators such as CPI, unemployment, yield spread and GDP growth, then retrieves earlier periods with comparable macro contexts during inference. Retrieval is causal in the temporal sense: only earlier periods can be used.

Trained on S&P 500 data from 2007–2023 and evaluated OOD on AAPL and XOM in 2024, the authors report that macro-conditioned retrieval was the only tested approach with positive out-of-sample trading outcomes on both assets (AAPL PF 1.18, Sharpe 0.95; XOM PF 1.16, Sharpe 0.61).

**Application role:** regime-shift robustness and interpretable financial precedent retrieval.

**What is computationalized:** multimodal precedent search under macro constraints.

**Main limitation:** “causal retrieval” here primarily means time-safe retrieval; the joint embedding still does not establish causal/mechanistic equivalence of regimes.

---

## 4. Strategic / military / intelligence use — demand is clearer than implementation

The national-security community is unusually explicit that historical analogy is a core decision technology. Harvard's Applied History Project defines applied history itself as illuminating current challenges by analyzing historical precedents and analogues, and its recommended workflow is essentially:

`define target → generate many candidate precedents → list similarities + differences → infer bounded lessons`.

Canonical framework: https://www.belfercenter.org/programs/applied-history-project/about-applied-history-project

A 2026 Belfer analysis of U.S. military practice argues that professional military education, staff rides, wargaming and historical cases are used to cultivate judgment rather than to extract deterministic lessons.

Canonical: https://www.belfercenter.org/research-analysis/martial-approach-applied-history-how-us-military-turns-history-judgment

### The notable negative result

Despite strong institutional demand, this scan found **fewer public modern AI systems that operationalize historical precedents for military/intelligence decision support** than in finance, conflict forecasting or general foresight. Public defense AI work is rich in wargaming, COA generation, intelligence fusion and simulation, but usually does not expose a historical-analogy retrieval/adjudication layer.

This absence is itself useful. National-security historical analogy remains largely a human applied-history practice even as the surrounding decision pipeline becomes AI-enabled.

---

# 5. Computational prehistory: this problem existed in 1980s AI

The apparent 2025–26 novelty has a forgotten precursor in international-relations AI.

- **Dwain Mefford, 1984:** *Formulating Foreign Policy on the Basis of Historical Analogies: An Application of Developments in Artificial Intelligence*.
- **Philip A. Schrodt, 1985:** *Adaptive Precedent-Based Logic and Rational Choice: A Comparison of Two Approaches to the Modeling of International Behavior*.
- Later Schrodt work developed pattern recognition over international event sequences, explicitly treating precedent/analogy as an alternative to purely statistical or rational-choice models.

The 1985 volume *Dynamic Models of International Conflict* placed `Adaptive Precedent-Based Logic` and logic-programming analyses of changing foreign policy under a dedicated **Artificial Intelligence Approaches** section.

This line matters because modern LLM work may be **re-entering a previously abandoned engineering problem**: how to represent a current international situation, search historical cases, adapt a precedent, and avoid being captured by a vivid but misleading analogy.

The contrast is striking:

`1980s: structured cases + symbolic/precedent logic + weak representation learning`

`2020s: powerful representation/search + weak transfer/adjudication discipline`.

A dedicated computational-prehistory note should reconstruct this lineage before making novelty claims about modern historical-analogy systems.

---

# 6. Cross-domain maturity map

| Application form | Analogue unit | Current maturity | Strongest capability | Main unresolved issue |
|---|---|---:|---|---|
| Historical event acquisition | named past event | medium | candidate generation/search | useful precedent vs seductive parallel |
| Mechanism-level foresight | causal/structural roles across events | early but technically serious | multi-case mechanism coverage | contested mechanisms; transfer validity |
| Actor-analogy detection | explicit past→present mapping in discourse | real deployed research workflow | high-recall corpus screening | causal meaning/base rates |
| Conflict trajectory forecasting | fatality sequence / conflict signature | high predictive maturity | retrieval + calibrated future mixture | trajectory similarity ≠ mechanism similarity |
| Epidemic trajectory forecasting | epidemic time-series shape | medium–high | adaptive analogue learning | limited event semantics/causality |
| Macro forecast interpretation | weighted past economic periods | high mathematical maturity | exact historical contribution decomposition | proximity ≠ mechanism |
| Financial regime retrieval | text + macro regime | emerging applied ML | OOD precedent retrieval | structural/causal validity |
| Military/intelligence applied history | rich historical cases | high human-practice maturity; low public AI maturity | disciplined similarity/difference analysis | computationalization without false confidence |

---

# 7. The convergence to watch

The most interesting future system would combine what these application areas currently keep separate:

- **event-level semantics** from LLM historical analogy;
- **out-of-sample calibration** from forecasting;
- **explicit uncertainty** from analogue ensembles;
- **multiple precedent competition** rather than one vivid source;
- **similarity AND dissimilarity accounting** from applied-history practice;
- **mechanism-level alignment** from CANA;
- **temporal hygiene** from causal/forecasting retrieval;
- **claim-level transfer contracts** from the broader transfer-validity gap map.

The key design target is not a system that confidently says “today resembles 1914.” It is one that can say:

`these three past cases are relevant for different reasons; these structural claims recur; these differences block two tempting projections; the remaining forecast has this uncertainty; here is the evidence that would make us abandon the analogy.`

That remains substantially ahead of the public systems found in this scan.
