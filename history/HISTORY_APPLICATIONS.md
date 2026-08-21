# History Applications — Beyond “History Agents”

**Snapshot: 21 August 2026.**

This branch asks a narrow question:

> **Where is contemporary AI already changing historical research itself, especially through cross-case representation, analogy, causal/mechanistic comparison, temporally bounded reconstruction, and evidence-intensive reasoning?**

It deliberately excludes generic historical QA bots, museum chatbots, RAG front-ends, and “agent” systems whose main contribution is tool orchestration around OCR/search/translation.

The history branch distinguishes two layers:

1. **Historical substrate** — turning difficult primary sources into structured, reproducible data at scales previously impossible for a historian.
2. **Historical inference** — using those representations to compare cases, identify mechanisms, detect analogical framing, reconstruct historically available solution spaces, or make evidence-constrained claims.

The second layer is the main target of this repository.

---

# 1. Historical substrate: source → structured representation

These projects are not analogical reasoning by themselves, but they matter because serious historical analogy cannot operate over raw pages without a representation layer.

## 1.1 Multimodal archival extraction at economic-history scale

### Griesshaber & Streb — German patents, 1877–1918

**Niclas Griesshaber & Jochen Streb, “Multimodal LLMs for Historical Dataset Construction from Archival Image Scans: German Patents (1877–1918),” 2025/26.**  
Canonical: https://arxiv.org/abs/2512.19675

The project constructs **306,070 patent records from 9,562 archival image scans** with Gemini-2.5-Pro / Flash-Lite. The source pages combine Gothic/Roman type, double-column layout, and roughly 20–50 entries per page. The authors benchmark against research-assistant transcription and report substantially higher throughput and lower cost, while explicitly checking hallucination against a corrected benchmark.

**Why it matters here.** It demonstrates that a foundation model can turn heterogeneous visual primary sources directly into a structured case base at a scale suitable for later relational or comparative analysis. The historical contribution is not “AI reads handwriting”; it changes the feasible population of cases that can enter an empirical historical argument.

**Limit.** Extraction correctness does not imply historically meaningful representation. The five extracted variables are fixed by the researcher; the model is not deciding which relational dimensions matter for a historical comparison.

---

## 1.2 Event-based historical databases from narrative biographies

### Knutsen 2026 — fine-tuned Llama + Actoz/Fichoz

**Gunnar W. Knutsen, “Fine-tuning LLAMA models for historical databases: methods, challenges, and long-term implications,” Digital Scholarship in the Humanities, 2026.**  
Canonical: https://doi.org/10.1093/llc/fqag057

The project transforms thousands of Danish/Norwegian biographical entries into an **event/action–actor representation** compatible with Actoz/Fichoz. Roughly 6,000 relevant biographies yielded about 100,000 event lines; the model handles dated actions, places, offices, marriages, migrations, education, translations across historical languages, approximate dates, and variant names.

Crucially, the paper shows the bottleneck moves rather than disappears: model inference takes days, but historical validation, entity linking, chronology, and interpretive consistency still take months.

**Why it matters here.** This is a serious representation architecture for history. It converts narrative sources into relational units that can later support prosopography, institutional comparison, migration trajectories, or source retrieval by historical structure.

**Limit.** The action–actor ontology is supplied by historical database practice. The system does not yet learn a representation because it proved useful for a particular comparison or analogy.

---

## 1.3 Historical OCR as epistemic representation, not clerical preprocessing

### Greif, Griesshaber & Greif 2025; Levchenko 2025

Multimodal LLM work on German city directories shows OCR/post-correction/NER can be unified and reach very low character error rates; parallel work on 18th-century Russian books shows the opposite risk: models can produce **epistemic anachronism**, silently regularizing historical orthography or interpreting unfamiliar forms through modern language priors.

**Why it matters here.** An analogical system inherits whatever distinctions the transcription layer destroys. If a model normalizes away historically meaningful spelling, terminology, category boundaries, or layout, downstream “structural similarity” may be an artefact of modernized representation.

**History-specific lesson:** source representation has to preserve historically salient difference, not merely maximize OCR accuracy.

---

# 2. Structured comparative history: AI as a coding instrument for historical comparison

## 2.1 Griesshaber & Ogilvie — institutional transplantation

**Niclas Griesshaber & Sheilagh Ogilvie, “Transplanting Craft Guilds to Colonial Latin America: A Large Language Model Analysis,” CEPR DP20556, 2025.**  
Canonical: https://cepr.org/publications/dp20556

This is one of the strongest current examples of an LLM entering an actual historical argument rather than merely preparing data. The authors use LLMs to digitize and quantitatively code **colonial guild ordinances**, then compare institutional features across colonial Mexico and Peru. They report long-run continuities alongside significant differences in human-capital and product-quality regulation, including patterns they argue were difficult to see with standard economic-history methods.

**Historical operation:**

`qualitative ordinances → comparable institutional dimensions → cross-case quantitative comparison → argument about institutional transplantation/adaptation`.

This is already close to analogical reasoning at the research-design level: the historian defines a common relational vocabulary, asks which institutional structures survive transplantation, and identifies dimensions that change under a new context.

**Why it is more important than a history agent.** The LLM changes the *comparability* of sources. It creates a systematic representation across corpora that were previously too costly to code at scale.

**Limit.** The historically consequential relational dimensions are still researcher-designed. It is not yet an autonomous system for discovering the comparison schema.

---

# 3. Historical analogy acquisition: present target → candidate historical sources

## 3.1 Li et al. — *Past Meets Present*

**Nianqi Li et al., “Past Meets Present: Creating Historical Analogy with Large Language Models,” ACL 2025, Outstanding Paper.**  
Canonical: https://aclanthology.org/2025.acl-long.200/

This paper makes **historical analogy acquisition** an explicit task: given an event, retrieve or generate a historical event that can serve as an analogue. The dataset distinguishes well-known analogies from more open-ended cases and evaluates analogy quality along multiple dimensions. A self-reflection step is introduced to reduce hallucinated or stereotyped analogies.

The important transition is:

`historical event retrieval by topic`

→ `historical event retrieval by analogous structure`.

**What it establishes.** General LLMs can generate plausible historical analogues at useful quality, and explicit reflection improves them.

**What it does not establish.** A plausible analogue is not yet a historian-grade comparison. The task largely evaluates candidate-event quality; it does not require source criticism, mechanism-level transfer validity, systematic counter-analogy, or proof that a projected claim is licensed by the historical record.

**History-specific gap exposed.** The model can find “a past that looks useful” before it can explain exactly **which historical proposition is allowed to transfer from that past**.

---

# 4. Mechanism-based historical comparison and foresight

## 4.1 Chen et al. — Analogical Deep Research / CANA

**Yongqiang Chen, Guangyi Chen, Yuewen Sun & Kun Zhang, “Analogical Deep Research: Retrieving and Integrating Historical Analogies for Foresight Analysis,” 15 July 2026.**  
Canonical: https://arxiv.org/abs/2607.13602

This is currently the most technically ambitious historical-analogy system found in the sweep. It argues that historical analogy is fundamentally a **causal/mechanism alignment problem**, not a semantic-similarity problem.

CANA represents events through preconditions, temporal chains, mechanisms, and outcomes; retrieves analogies through these structural decompositions; iterates search to cover missing positions; and uses **cross-analogy confirmation** to infer hidden factors that no single historical case supplies.

The paper’s 2008 financial-crisis example is especially revealing: the Panic of 1907, Japan 1990, and LTCM 1998 contribute different partial positions in a common pattern; their union is used to hypothesize a hidden amplifier in the target.

**Historical operation:**

`current/incomplete event`

→ `structural decomposition`

→ `retrieve several distant past events`

→ `align mechanisms/positions`

→ `infer hidden target factor`

→ `foresight claim`.

**Why this matters.** It moves historical analogy from illustration to **distributed evidence integration**. One historical case need not be a complete template.

**Major limit.** This is still applied-history/foresight rather than historical explanation of the past itself. Its cross-analogy confirmation also depends on assumptions about evidential independence; correlated analogies can create false confirmation.

---

# 5. Historical analogies as evidence inside the archive

## 5.1 Tsvetkova 2026 — analogy detection as a marker of decision formation

**Natalia Tsvetkova, “Historical analogies as markers of decisions: an LLM-assisted analysis in foreign policy,” Humanities and Social Sciences Communications 13 (2026).**  
Canonical: https://doi.org/10.1057/s41599-026-06930-9

This is methodologically distinct from the previous work. The LLM is **not asked to invent a useful historical parallel**. It screens a corpus for analogies already articulated by historical/political actors, after which the researcher validates and interprets them.

The study screens roughly **1,100 official documents** across Clinton, Putin and Xi corpora, manually verifies every extracted candidate, and then analyzes a small set of positive cases. The claim is that repeated historical analogies may act as observable markers of policy direction before formal decisions become visible.

**Historical operation:**

`large corpus of actor-produced documents`

→ `LLM candidate detection`

→ `manual validation/coding`

→ `chronological placement relative to later decision`

→ `interpret analogy as evidence of actor framing / emerging preference`.

This is one of the clearest examples of a non-agent LLM acting as a **high-recall archival screening instrument** inside a conventional historical argument.

**Strength.** The interpretation remains anchored to actor-authored documents, chronology, manual validation and subsequent events.

**Limit.** Detecting an analogy in discourse does not establish that it causally produced the decision. The method is strongest as evidence discovery / signaling analysis, weaker as causal attribution.

---

# 6. Historical counterfactuals as controlled tests of reasoning

## 6.1 Larraz & Corma — FCC 1942 with a pre-1936 knowledge boundary

**Rafael Larraz & Avelino Corma, “Human analogical guidance amplifies LLM performance through cross-domain knowledge activation,” Nature Communications 17 (2026), 4822.**  
Canonical: https://doi.org/10.1038/s41467-026-70873-7

This is not conventional historical scholarship, but it uses history in a technically sophisticated way. The authors reconstruct the pre-discovery knowledge environment for fluid catalytic cracking (FCC), constrain retrieval to **pre-1936 literature**, and ask whether a model can generate the later technical solution without receiving post-discovery knowledge. Human analogical guidance increases success dramatically.

History supplies three things that ordinary AI benchmarks lack:

1. a **sharp epistemic cutoff** — what information was available at time *t*;
2. a **known later outcome** — what was eventually discovered;
3. a **documentable distributed evidence base** — whether the necessary ingredients existed before the breakthrough.

This turns historical counterfactual reconstruction into an experimental design for analogical reasoning.

**History-specific importance.** The same method could be inverted for historians: ask not “could an AI rediscover FCC?” but “given only sources available to actor X at date t, what inferential paths were historically available, which were visible, and which require hindsight?”

**Limit.** The model itself was pretrained on later knowledge, so temporally bounded RAG constrains accessible context but cannot perfectly erase latent memorized knowledge. Historical counterfactual validity therefore requires contamination controls beyond retrieval cutoff.

---

# 7. Benchmarks that expose specifically historical failure modes

These are not applications by themselves, but they tell us what a serious history-facing analogical system must survive.

## 7.1 ProHist-Bench — evidentiary reasoning

**Gao et al., ACL 2026, “Can LLMs Act as Historians?”** evaluates 18 models on 400 expert-curated questions around the Chinese imperial-examination system with **10,891 fine-grained rubrics**. The explicit target is professional historical reasoning rather than factual recall. The paper finds a large gap on higher-order evidentiary tasks.

**Use for this repo:** historical analogy should eventually be scored as an evidentiary argument, not merely as semantic similarity or a final-answer benchmark.

## 7.2 *Lost in Historical Time?* — source decontextualization and temporal disorientation

A 2026 Polish Matura benchmark reports two recurrent errors despite high aggregate performance:

- **source decontextualization** — models reason *from* what a source says instead of treating the source itself as a historically situated object of analysis;
- **temporal disorientation** — responses place claims, concepts or context in the wrong historical frame.

These are directly relevant to analogy. A source that is propositionally similar may be historically inapplicable because of genre, audience, institutional setting or temporal semantics.

## 7.3 Temporal reframing

*If I Could Turn Back Time* asks models to answer a 1940 Norwegian question book **as if it were 1940**. The setup is simple, but it isolates presentism: models must distinguish present-day truth from historically available truth.

## 7.4 Historical-context annotation

LREC 2026 work on contentious terminology in Dutch historical corpora finds near-human performance on explicit cases but large divergences when **semantic shift or historical context** determines the label. This is another warning against assuming that an LLM’s contemporary semantic representation is adequate for source-era meaning.

---

# 8. The emerging map of AI-for-history that matters here

| Historical operation | Current best examples | Current maturity | Analogy relevance |
|---|---|---|---|
| source digitization / extraction | German patents; historical OCR | **high, rapidly improving** | builds candidate case base |
| event / actor representation | Knutsen + Actoz/Fichoz | **medium–high** | relational substrate |
| institutional feature coding | Griesshaber–Ogilvie guilds | **real research use** | comparative representation |
| candidate historical analogy retrieval | *Past Meets Present* | **moderate** | direct source search |
| mechanism-level multi-case analogy | CANA / ADR | **early but substantial** | direct structural integration |
| detecting analogies made by historical actors | Tsvetkova | **real corpus application** | analogy as historical evidence |
| temporally bounded counterfactual reconstruction | Larraz–Corma | **strong experimental method** | tests historical availability of inferential paths |
| historian-grade evidentiary reasoning | ProHist-Bench / HistBench benchmarks | **weak in current models** | downstream validity criterion |
| source contextualization / temporal orientation | Polish Matura; temporal reframing | **persistent failure** | guards against anachronistic transfer |

---

# 9. Where the history-specific frontier actually is

The history branch should not ask whether an LLM can “answer history questions.” A more serious target is:

`primary sources`

→ `historically faithful representations`

→ `retrieve structurally relevant past cases`

→ `preserve source provenance and chronology`

→ `map similarities AND historically consequential differences`

→ `project only licensed claims`

→ `seek counterevidence / alternative analogies`

→ `distinguish actor knowledge at time t from later historian knowledge`

→ `write an auditable evidentiary chain`.

The current literature has convincing pieces of this pipeline. It does **not** yet have a general system that closes it.

For the history branch, the most promising research question is therefore not “AI historian?” but:

> **Can analogical AI become an instrument of comparative historical inference without collapsing historical specificity into a shared machine-generated schema?**

That is the tension to track.