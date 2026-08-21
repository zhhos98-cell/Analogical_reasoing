# Risk and Persuasion — Historical Analogies Are Not Epistemically Neutral Outputs

**Snapshot: 21 August 2026.**

Historical analogies have a special deployment risk: they are not merely candidate facts. A well-chosen analogy can make a decision feel more coherent, justified and historically grounded. A badly chosen analogy can do the same.

This means that retrieval/matching precision is linked to **persuasion and overconfidence**, especially in policy-facing systems.

The evidence currently comes from three adjacent literatures. No direct experiment found in this sweep yet tests the full chain `AI-generated historical analogy → human decision change`, so the risk should be stated as a convergence of evidence rather than a settled causal finding.

---

## 1. Historical analogies increase confidence in foreign-policy decisions

### Blair, Lendway & Schwartz — Journal of Conflict Resolution 2026

**_Historical Analogies and Public Support for Foreign Policy Action_.**  
Canonical: https://doi.org/10.1177/00220027251399905

Across a comprehensive experimental study of U.S. public foreign-policy attitudes, historical-analogy appeals increase **mass confidence in leaders' foreign-policy decision making**.

The authors also find:

- analogies outperform an explicitly intuitive / “gut” justification;
- analogical appeals are not uniquely persuasive relative to other rational-seeming justifications such as expert appeals;
- part of their effect is therefore the broader legitimating force of providing an intelligible reason for action.

### Implication for AI historical analogy

A precedent can affect a user at two levels:

1. **epistemic content** — what evidence/mechanism does the past case contribute?
2. **justificatory form** — does the existence of a precedent make the decision feel reasoned and competent?

A historical-analogy assistant can therefore increase confidence even when its source→target mapping is weak.

---

## 2. Historical analogy can move attitudes across audiences, though effects are conditional

### Menon, Abramson, Dulay & Jones — Security Studies, 2025

**_The Effect of Historical Analogies on Foreign Policy Attitudes_.**

Using Zelensky's historically tailored rhetoric after Russia's 2022 invasion, preregistered survey experiments were conducted simultaneously in Germany, Israel, the UK and the US.

Historical analogies reliably generated emotional reactions, but policy-attitude effects were more conditional; clear support shifts were not uniform across countries.

### Why this matters

The lesson is not `analogy always persuades`. It is:

`historical memory + audience context + analogy choice → variable rhetorical effect`.

A personalized AI precedent system could in principle choose analogies not only for structural fit but also for audience salience. That would create a dangerous objective-function ambiguity:

`best analogy for reasoning`

vs

`most persuasive analogy for this user`.

These should be explicitly separated.

---

## 3. LLM-generated historical narratives can shift opinions even when factually accurate

### Shu, Karell, Okura & Davidson — PNAS Nexus 2026

**_How latent and prompting biases in AI-generated historical narratives influence opinions_.**

Canonical: https://doi.org/10.1093/pnasnexus/pgag022

In a preregistered experiment with **N=1,912**, participants read Wikipedia or GPT-4o summaries of historical events. The AI summaries remained factually accurate but differed in framing.

The study reports opinion shifts aligned with the ideological framing of the generated historical account; even default AI summaries differed systematically from Wikipedia in their downstream attitudinal effects.

### Why it matters for analogy

Historical analogy requires more interpretive freedom than summary. The system chooses:

- which source event to foreground;
- which properties are “the same”;
- which differences are salient;
- which causal story makes the source relevant;
- which outcome is projected.

If factual historical summaries can already influence attitudes through framing, source-selection and mapping choices in an analogy system should be treated as potentially consequential **framing interventions**, not neutral retrieval operations.

---

## 4. The low-precision problem makes this more serious

### Sen, Workiewicz & Puranam — Strategy Science 2026

Canonical: https://doi.org/10.1287/stsc.2025.0426

LLMs can have very high recall for candidate analogies but lower precision than humans in deciding which source genuinely matches the target. Some model errors are internally coherent causal schemas rather than crude surface matches.

Combine this with the persuasion evidence and a specific risk appears:

`high-recall source generator`

`+ low-precision adjudication`

`+ coherent explanatory prose`

`+ historical justification effect`

`→ confident false precedent`.

Again, the entire causal chain has not yet been experimentally demonstrated in one study. It is a testable risk hypothesis supported by independent components.

---

# 5. Historical-analogy systems need an epistemic/rhetorical separation

A useful system should separate two scores that current products could easily conflate:

### Epistemic value

- mechanism fit;
- source quality/provenance;
- difference awareness;
- claim-level transfer validity;
- calibration/out-of-sample evidence;
- independence from other precedents.

### Rhetorical/salience value

- familiarity;
- memorability;
- emotional resonance;
- narrative clarity;
- audience relevance.

The second set can be useful for communication **after** the first is established. It should not determine precedent ranking in the analytical stage.

A system optimized for “helpfulness” or “convincing explanation” may otherwise select the most narratively satisfying precedent rather than the most epistemically useful one.

---

# 6. Minimum interface safeguards for policy-facing historical analogy

The UI/output should resist the single-story effect. At minimum it should expose:

1. **several candidate precedents**, not one authoritative past;
2. **why each was retrieved**;
3. **where each analogy breaks**;
4. **which individual projections are licensed / conditional / vetoed**;
5. **an explicit no-useful-precedent option**;
6. **source provenance and temporal cutoff**;
7. **confidence/calibration separate from narrative fluency**;
8. **counter-analogies or historical cases pointing in the opposite direction**;
9. **what evidence would change the ranking or invalidate the lesson**.

The design target should be:

`make historical analogy auditable before making it persuasive`.

---

# 7. Missing experiment: AI-generated historical analogy persuasion

A direct experiment has not been identified in this sweep. It would be highly informative to randomize users between:

- decision recommendation only;
- recommendation + valid historical analogy;
- recommendation + seductive but transfer-invalid analogy;
- recommendation + valid analogy with explicit limitations;
- recommendation + several competing precedents;
- recommendation + calibrated no-analogy conclusion.

Measure separately:

- perceived decision quality;
- confidence;
- willingness to act;
- factual/structural understanding;
- ability to identify the analogy's limitations;
- calibration to actual decision accuracy.

This would directly test whether **analogy quality and analogy persuasiveness dissociate** in AI-assisted decisions.
