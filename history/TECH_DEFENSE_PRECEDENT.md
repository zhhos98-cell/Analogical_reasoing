# Technology and Defense — Historical Precedent Beyond Generic LLM Agents

**Snapshot: 21 August 2026.**

Two application domains complicate the simple story that historical-analogy AI began with LLMs: technology foresight and military decision support. Both have older precedent-based methods, while 2026 machine learning is beginning to scale historical-technology comparisons.

---

# 1. Technology foresight: historical analogues as deployment evidence

## SHARD — a disciplined human methodology

**Systematized Historical Analogue Research for Decision-making (SHARD).**  
Canonical: https://doi.org/10.1016/j.erss.2022.102890

SHARD was developed for low-carbon transition decisions. It provides a transparent procedure to:

1. define a target innovation;
2. identify strategically similar historical technologies;
3. select an analogue through explicit criteria;
4. reconstruct the historical transition;
5. derive findings with attention to external validity and present-day applicability.

Its pilot example uses **margarine** as an analogue for **plant-based meat**.

SHARD is not an AI system. It matters as a benchmark for what serious technology-analogue reasoning should control: source selection is not enough; analogue choice and lesson extraction must be explicit and auditable.

---

## Li et al. 2026 — ML over 44 historical technology deployments

**Xiyu Li, Yixin Sun, Yun Tang, Houcheng Peng, Hongbo Duan, “Machine learning reveals insufficient carbon capture storage deployment to meet climate goals,” Global Environmental Change 98 (2026), 103157.**  
Canonical: https://doi.org/10.1016/j.gloenvcha.2026.103157

The study trains a machine-learning model on **44 historical technology datasets from 1900–2024** and integrates the resulting CCS deployment forecast with an integrated assessment model.

The model uses:

- historical CCS deployment;
- deployment trajectories of reference technologies;
- patent indicators associated with those technologies.

This is a genuine modern computational use of **historical analogue technologies** for an emerging target technology, although the analogue relation is learned statistically rather than expressed as source→target causal mapping.

### Why it matters

Technology forecasting is a domain in which historical analogue reasoning can be validated against quantitative deployment histories. It therefore offers an intermediate testbed between narrow trajectory analogy and rich geopolitical event analogy.

### Gap

The model learns across a pool of historical technologies; it does not expose a historian/analyst-style transfer contract stating which specific historical technology contributes which mechanism or where a precedent ceases to apply.

---

## An important warning from older technology forecasting

**_Forecasting the future of technology by analogy—An evaluation of two prominent cases from the 20th century_ (Technology in Society, 2009).**  
Canonical: https://doi.org/10.1016/j.techsoc.2009.03.012

Retrospective evaluation of two long-running technology analogies found that analogy could **misdirect** demand forecasts rather than improve them.

This is a useful negative benchmark: historical analogy should be scored by downstream calibration, not by how persuasive the parallel sounds.

---

# 2. Military decision support: precedent reasoning has an engineering prehistory

The current public foundation-model literature contains relatively little explicit `historical event → current military situation` analogy control. But military AI has a substantial older **case-based planning** tradition.

## SOCAP — crisis action planning, 1995

**System for Operations Crisis Action Planning (SOCAP).**

SOCAP applied SIPE-2 generative planning to joint crisis-action operations planning and integrated it with complementary technologies including a **case-based reasoner**, temporal reasoning and scheduling/capacity analysis.

This is not historical analogy in the rich applied-history sense, but it establishes the old architecture:

`new operational situation → reuse prior plan/case → adapt → generate operation plan`.

---

## Liao 2000 — case-based military command and control

**Shu-hsien Liao, “Case-based decision support system: Architecture for simulating military command and control,” European Journal of Operational Research 123(3), 558–567.**  
Canonical: https://doi.org/10.1016/S0377-2217(99)00109-5

The paper explicitly asks why experience from training, exercises and real combat should not be reused during new military command-and-control problems and why new operational knowledge should not be retained as cases after action.

The proposed architecture combines CBR and decision support for planning at strategic and tactical levels.

The control cycle is close to modern continual analogical reasoning:

`past operational experience → retrieve → adapt → plan/execute → retain new case`.

---

## Navy / NRL NaCoDAE — precedent-based decision aids

The U.S. Naval Research Laboratory's Navy Center for Applied Research in AI developed the **Navy Conversational Decision Aids Environment (NaCoDAE)**, a CBR decision-aid shell. Navy applications included retrieval over prior equipment-failure histories and ranked useful solutions based on current problem descriptions.

Again, the cases are operational rather than historiographical, but the system demonstrates practical precedent retrieval inside naval knowledge management.

---

## Operational-simulation case transfer — National Defense University, 2022

A 2022 study from China's National Defense University / Joint Operations College proposes **compromised case-based reasoning** to transfer knowledge about experimental-scope selection from historical operational-simulation experiments to new cases.

Canonical: https://www.china-simulation.com/CN/Y2022/V34/I7/1568

This shows that precedent transfer remains an active engineering pattern in military simulation even before current foundation-model agents.

---

# 3. Current state: the defense gap is an interface gap, not an absence of precedent reasoning

The older defense systems are strong in one respect that current open-domain LLM analogy often lacks: they have an explicit **reuse/adaptation loop** over cases.

But their representations are narrow and engineered:

- equipment failures;
- SOPs;
- plans;
- simulation configurations;
- structured operational situations.

Modern foundation models have the opposite advantage: they can read doctrine, diplomatic history, after-action reports, intelligence reporting and open-ended narratives, but they lack a standard mechanism for saying exactly which precedent is applicable and which lesson should be vetoed.

The real defense frontier is therefore:

`open heterogeneous operational/historical evidence`

`→ learned situation representation`

`→ retrieve several precedents`

`→ distinguish mechanism from superficial resemblance`

`→ adapt plan/lesson`

`→ explicitly identify disanalogies`

`→ license/veto individual projected consequences`

`→ simulate/test`

`→ retain applicability boundaries`.

No public general-purpose foundation-model system found in this sweep demonstrates that full loop.

---

# 4. A cross-domain opportunity

Technology foresight and military planning provide complementary validation environments:

- **technology deployment** offers long quantitative histories and measurable diffusion outcomes;
- **military planning** offers structured case reuse, simulation and adaptation traditions;
- **event-level historical analogy** offers richer semantics and causal interpretation.

A convincing new historical-analogy architecture should probably be tested across more than one of these regimes. Otherwise it is difficult to distinguish a general precedent controller from a domain-specific retrieval trick.
