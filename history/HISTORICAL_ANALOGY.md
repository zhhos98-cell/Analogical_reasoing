# Historical Analogy Applications — AI Using the Past as a Source Domain

**Snapshot: 21 August 2026.**

This branch is deliberately narrow. It tracks systems that use **historical analogies themselves** as a computational object or reasoning resource: finding past events structurally analogous to a present target, using those analogies for foresight or decision support, detecting historical analogies in political reasoning, or learning from historical precedent patterns.

It excludes generic history QA, archive agents, OCR pipelines, historical-roleplay models, and broad AI-for-history work.

The key question is:

> **What can AI already do with historical analogies, and where does the reasoning break?**

---

## 1. Historical analogy acquisition — finding a past event for a present target

### Li et al. — *Past Meets Present* (ACL 2025, Outstanding Paper)

**Nianqi Li, Siyu Yuan, Jiangjie Chen, Jiaqing Liang, Feng Wei, Zujie Liang, Deqing Yang, Yanghua Xiao.**  
Canonical: https://aclanthology.org/2025.acl-long.200/

This is the clearest starting point for the modern LLM historical-analogy line. The task is explicitly **historical analogy acquisition**: given an event, retrieve or generate an analogous event from the past.

The paper compares dataset retrieval with free generation. It decomposes events into four dimensions — **topic, background, process, result** — and rewards abstract similarity while penalizing excessive literal/entity overlap. Free generation performs better than retrieval on average, and a self-reflection procedure that proposes candidates, evaluates them, and verifies existence through Wikipedia improves analogy quality and reduces stereotyped same-country/same-entity matches.

Important empirical observations:

- popular/well-known analogies are much easier than general analogies, raising contamination/memorization concerns;
- free generation beats fixed-pool retrieval by about 0.25 on the reported aggregate comparison;
- gains from candidate-set expansion plateau after roughly five candidates;
- the model often **accepts an early candidate rather than reflecting**, even when reflection is available;
- changing the description/perspective on the same current event can produce a different historical analogue.

### What it really solves

`current event → candidate historical source event`

This is primarily **source acquisition**, not full analogical inference.

### Main gap exposed

The method can produce a plausible historical analogue without establishing:

- whether the underlying causal mechanism is genuinely shared;
- which source-to-target relations are transferable;
- which differences should veto a projected lesson;
- whether the analogy improves prediction or decision quality.

So the first modern stage is strong on **candidate generation**, weak on **historical lesson licensing**.

---

## 2. Mechanism-level historical analogy for foresight

### Chen et al. — *Analogical Deep Research* / CANA (2026)

**Yongqiang Chen, Guangyi Chen, Yuewen Sun, Kun Zhang.**  
Canonical: https://arxiv.org/abs/2607.13602

This is the most advanced explicit historical-analogy reasoning system found in the current sweep.

The paper argues that useful historical analogy is not primarily a semantic-similarity problem. It is a **causal/mechanism alignment** problem. Each event receives both a descriptive representation and a mechanistic representation. The target is only partially observed at a cutoff time; the task is to retrieve historical cases that occupy corresponding structural roles and use their later trajectories to infer hidden target factors and possible futures.

The system introduces two central ideas:

1. **mechanism alignment** — search over causal/structural roles rather than surface similarity;
2. **cross-analogy confirmation** — several partial historical analogies can jointly support a hidden structural factor even when no single case covers the whole target.

The 2008 financial-crisis example is a good illustration: the Panic of 1907, Japan after 1990, and LTCM 1998 each supply different parts of a common mechanism; recurring "amplifier" roles across them are used to hypothesize a hidden amplifier in the target.

ADR-bench contains 15 targets across financial, geopolitical, and technology domains. Existing deep-research agents generally fail to proactively exploit useful historical analogies; CANA reports more than 10% improvement in historical-analogy retrieval/integration over the compared methods.

### What it really solves

`partially observed present event`

`→ structural decomposition`

`→ retrieve multiple historical events`

`→ align causal roles`

`→ infer hidden factors / trajectories`

This is a major step beyond *Past Meets Present*: historical analogy becomes an **evidential and forecasting operator**, not just a retrieved comparison.

### Main gaps exposed

- the causal graph/event decomposition is still generated under a fairly strong scaffold;
- cross-analogy confirmation assumes sufficiently independent confirming sources;
- transfer validity is stated at structural-role level but is not yet a calibrated claim-by-claim veto mechanism;
- the benchmark remains small (15 target events);
- open-world historical events contain contested causal interpretations, not a single oracle mechanism.

This is currently the most important system to track if the branch is about historical analogy rather than historical AI generally.

---

## 3. Historical analogies as signals of policy reasoning

### Tsvetkova — *Historical analogies as markers of decisions* (2026)

**Natalia Tsvetkova.** *Humanities and Social Sciences Communications* 13, 547 (2026).  
Canonical: https://doi.org/10.1057/s41599-026-06930-9

This uses AI differently. The model does not generate the analogy for a decision-maker. It detects **historical analogies already being used by political actors** and treats their appearance/repetition as a possible observable signal of policy direction.

An LLM screens roughly 1,100 official documents from Bill Clinton, Vladimir Putin, and Xi Jinping. All candidate analogies are manually verified and classified as cognitive, rhetorical, or signaling. The study then places validated analogies chronologically against later policy trajectories.

### What it really solves

`large political corpus → detect explicit past→present mappings → classify function → use analogy as an intelligence signal`

This is computational historical-analogy **detection**, not analogical reasoning by the model.

### Why it matters to this branch

It shows a second real-world application: historical analogy can be a **feature to detect in decision processes**. Instead of asking “what history should we compare with?”, the system asks “which historical comparison is this actor already using?”

### Main gap

The method finds a correlative signal. It does not establish that the analogy caused the decision, nor does it test whether the actor's analogy was structurally valid.

---

## 4. Analogical decision support under uncertainty

### Sen, Workiewicz & Puranam — *Can LLMs Aid Analogical Reasoning for Strategic Decisions?* (Strategy Science, 2026)

**Prothit Sen, Maciej Workiewicz, Phanish Puranam.**  
Canonical: https://doi.org/10.1287/stsc.2025.0426

This is not restricted to historical events, so it belongs in the branch as an **adjacent application** rather than a core historical-analogy paper. But it directly tests the decision-support use case that historical analogy is supposed to serve.

Across business-style source/target problems, humans and LLMs show opposite error profiles:

- humans: lower recall, higher precision;
- LLMs: very high recall, lower precision, including internally coherent but spurious matches.

The authors therefore propose a plausible near-term division of labour:

`LLM = expansive source/precedent generator`

`human = causal/contextual adjudicator`.

### Why it matters for historical analogy

Historical decision support is likely to fail in exactly this way: the danger is not lack of historical precedents but **too many plausible precedents**. This paper gives strong evidence that retrieval/generation and matching/adjudication should be treated as separate capabilities.

---

## 5. Historical analogy as a forecasting primitive over temporal patterns

### Zhang & Ji — HAL-Net (Expert Systems with Applications, 2026)

**Chengying Zhang, Donghong Ji.**  
Canonical: https://doi.org/10.1016/j.eswa.2025.130038

HAL-Net uses “historical analogy” in a narrower statistical sense. It searches past epidemic trajectories for analogous patterns using Dynamic Time Warping, selects a historical lag, and incorporates those precedents into long-range COVID forecasting across ten countries.

The paper reports average improvements above 28% MAE and 32% RMSE relative to the strongest baseline used in the study, with historical precedent paths also serving as an interpretability device.

### What it really solves

`current time-series segment → analogous historical pattern → future trajectory forecast`.

### Why it is adjacent rather than central

The analogue is a **shape/pattern precedent**, not a historically interpreted event with actors, institutions, mechanisms, and contested causal structure. Still, it demonstrates that “retrieve an analogous past trajectory and condition prediction on it” can be an effective engineering primitive.

This is useful as a lower-bound comparison for event-level historical analogy: time-series analogy works partly because the representation and transfer target are much more constrained.

---

## 6. Historical counterfactuals as a testbed for analogical problem solving

### Larraz & Corma — FCC rediscovery (Nature Communications, 2026)

**Rafael Larraz, Avelino Corma.**  
Canonical: https://doi.org/10.1038/s41467-026-70873-7

This is another adjacent case. The analogue sources are cross-domain technical knowledge rather than historical events, but the experiment is explicitly historical: the model is restricted to pre-1936 literature and asked to reproduce a technical solution developed later, fluid catalytic cracking.

Human analogical guidance increases model success dramatically. The study shows that historical reconstruction can provide a clean experimental structure:

`knowledge available before t`

`+ cross-domain analogy`

`→ later solution`.

### Relevance

It demonstrates a concrete downstream use of analogy under a historical knowledge boundary: **rediscovery / invention from historically available sources**.

It is not historical-analogy retrieval in the Khong/applied-history sense, so it stays adjacent.

---

# Current application taxonomy

| Application | Representative work | Source analogue | Output | Maturity |
|---|---|---|---|---|
| **historical analogue acquisition** | *Past Meets Present* | past event | ranked/generated historical case | established benchmark task |
| **mechanism-based foresight** | ADR / CANA | multiple past events | hidden factor + future trajectory analysis | frontier / early system |
| **analogy detection in political reasoning** | Tsvetkova | actor-invoked past event | policy-intent signal | real applied workflow |
| **strategic precedent support** | Sen et al. | prior problem/case | candidate strategy / match | strong adjacent evidence |
| **pattern precedent forecasting** | HAL-Net | past time-series trajectory | quantitative forecast | mature narrow-domain method |
| **historically bounded rediscovery** | Larraz & Corma | cross-domain historical knowledge | technical solution | strong adjacent experiment |

---

# What has actually been achieved?

The field has moved through three visible stages:

### Stage 1 — retrieve or generate a historical parallel

*Past Meets Present* establishes that LLMs can generate useful historical candidates and can be pushed away from obvious same-entity stereotypes.

### Stage 2 — distinguish surface resemblance from mechanism similarity

ADR/CANA shows that generic deep-research agents still fail here. It makes causal/structural representation and multiple partial analogies explicit.

### Stage 3 — use analogies as evidence rather than illustration

CANA uses several historical cases to infer a hidden factor; Tsvetkova uses actor-articulated analogies as signals; HAL-Net conditions quantitative forecasts on historical precedent patterns.

This third stage is only beginning.

---

# The historical-analogy-specific gaps

## HA1 — source acquisition is ahead of source adjudication

Models can propose many plausible historical parallels. They remain weaker at deciding which one has the **right causal structure** for the target.

## HA2 — historical difference is not yet a first-class computational object

Most systems optimize similarity/alignment. Serious historical analogy needs an explicit representation of **disanalogy**: which institutional, temporal, technological, demographic, ideological, or geopolitical difference breaks a proposed lesson.

## HA3 — claim-level transfer is missing

A historical case should not be accepted or rejected wholesale. A system should be able to say:

`analogy S supports claim p1`

`supports p2 only after rebinding/contextualization`

`does not support p3 because condition X differs`

`p4 remains uncertain`.

Current historical-analogy systems are not yet strong at this granularity.

## HA4 — causal structures in history are contested

CANA can work with a mechanism graph, but historical events typically admit multiple causal decompositions. A mature system needs **mechanism uncertainty / competing historical interpretations**, not a single canonical event graph.

## HA5 — analogy independence is difficult

Cross-analogy confirmation is powerful only when several analogies provide genuinely independent support. Historical cases often share source traditions, institutional families, diffusion chains, or the same retrospective narrative.

`three similar historical examples ≠ three independent pieces of evidence`.

## HA6 — presentism and hindsight remain latent

Historical analogy for foresight is especially vulnerable to models knowing how source and target events eventually unfolded. Evaluation needs strict temporal cutoffs and contamination controls.

## HA7 — no mature analogical decision interface

The near-term useful system probably should not emit one authoritative “best historical analogy.” It should expose:

- candidate sources;
- structural correspondences;
- disanalogies;
- projected lessons;
- vetoed lessons;
- uncertainty;
- source provenance;
- what additional evidence would discriminate between competing analogies.

That interface is not yet standard.

---

# Bottom line

The modern historical-analogy line is **small but real**. It is not yet a large field. The clearest direct genealogy is:

`Past Meets Present (2025): find historical analogues`

`→ ADR / CANA (2026): find mechanism-aligned analogues and integrate several of them for foresight`.

Around that core are two important application directions:

- **detecting historical analogies humans are already using** in policy reasoning;
- **using precedent analogies to improve decisions/forecasts** in strategy and structured time-series domains.

The most consequential remaining problem is not generating historical comparisons. It is **controlling what can legitimately be inferred from them**.