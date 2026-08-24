# Competing Hypotheses as a Control Neighbor for Historical Analogy

**Snapshot: 21 August 2026.**

Historical analogy is vulnerable to a specific form of confirmation: once a vivid precedent is selected, later evidence can be interpreted through that precedent's frame. Intelligence analysis and Bayesian process tracing offer an adjacent control tradition built around a different discipline:

> **do not ask only whether evidence fits the favored historical analogy; ask how diagnostic the same evidence is across competing explanations / precedents.**

This is not a solved control layer. The intelligence literature also contains strong evidence that formal procedures can add complexity without improving judgment. The useful lesson is therefore architectural, not doctrinal.

---

## 1. Analysis of Competing Hypotheses (ACH)

ACH requires analysts to:

- enumerate alternative hypotheses rather than commit early to one;
- evaluate each item of evidence against every hypothesis;
- focus on **inconsistency / diagnosticity**, not merely supporting evidence;
- identify future indicators that could disconfirm or confirm alternatives.

A historical-analogy translation would be:

```text
candidate precedent A
candidate precedent B
candidate precedent C
no-useful-precedent / target-is-structurally-novel

for each target observation e:
  how expected is e under each precedent-derived mechanism?
  which precedent does e actually discriminate between?
```

This is stronger than listing `alternative analogies` in prose because every piece of evidence must be evaluated comparatively.

---

## 2. But ACH itself is not a proven cure

### Dhami et al. 2019 — experimental test

**Mandeep K. Dhami et al., “The ‘analysis of competing hypotheses’ in intelligence analysis,” Applied Cognitive Psychology (2019).**  
Canonical: https://doi.org/10.1002/acp.3550

An experiment with intelligence analysts found mixed evidence for ACH's intended benefits. Analysts did not consistently follow all procedural steps, and ACH did not cleanly eliminate judgment error.

### Wilcox & Mandel 2024 — critical review

**John Wilcox & David R. Mandel, “Critical review of the Analysis of Competing Hypotheses technique: lessons for the intelligence community,” Intelligence and National Security 39(6), 941–962.**  
Canonical: https://doi.org/10.1080/02684527.2024.2304934

Reviewing six experiments, the authors conclude that ACH as a whole shows little or no overall benefit to judgment quality and may sometimes harm it.

### Historical-analogy lesson

A future AI system should not simply bolt on a large hypothesis matrix and assume rigor has increased. A control layer needs measurable calibration and downstream decision accuracy.

---

## 3. Bayesian process tracing provides a more explicit evidence-weighting target

Bayesian process tracing asks how likely a piece of evidence would be under competing causal hypotheses. This creates a natural quantity for analogy control:

```text
P(evidence e | mechanism implied by precedent S_i)
```

rather than:

```text
semantic plausibility(e, S_i)
```

The distinction matters because evidence that is equally compatible with every precedent is not diagnostic, however vivid it sounds.

---

## 4. Paci 2026 — current LLMs are coherent but poorly calibrated evidence judges

**Simone Paci, “Is Research Safe in the AI Revolution? LLMs Fall Short of Expert Benchmarks in Scientific Evidence Evaluation,” Chinese Political Science Review (2026).**  
Canonical DOI: https://doi.org/10.1007/s41111-026-00335-4

Paci benchmarks GPT-family models against expert Bayesian-process-tracing likelihood judgments across **289 evidence–hypothesis pairs** from ten published studies, then extends the analysis to **1,390 pairs** extracted from 200 political-science papers.

The result is directly relevant to historical precedent control:

- average model–expert distance in the BPT benchmark is roughly **30–40%**;
- much of the error is a systematic **20–30% upward bias**;
- models frequently treat evidence as more supportive/diagnostic than experts do;
- this changes posterior rankings of competing hypotheses;
- stronger models can be internally coherent and run-stable while still being miscalibrated.

This looks very similar to the analogy-selection problem already observed elsewhere:

> **coherent reasoning is not the same as calibrated evidential discrimination.**

A historical-analogy system could therefore produce a polished mechanism comparison while systematically overestimating how much each matching fact confirms the chosen precedent.

---

## 5. The right historical-analogy translation

The useful control primitive is not `run ACH`. It is:

### A. force explicit alternatives

At minimum include:

- best mechanism analogue;
- best counter-analogue / conflicting precedent;
- broader reference-class baseline;
- `no useful precedent / novel mechanism` option.

### B. score diagnostic evidence, not raw overlap

For each target observation:

```text
which candidate mechanisms predict this observation?
which candidates would also predict it, making it non-diagnostic?
what observation would sharply separate A from B?
```

### C. calibrate confidence against realized outcomes / expert judgments

Do not let fluent likelihood language count as calibration.

### D. preserve contradiction

If two precedents imply different trajectories and current evidence cannot discriminate them, the output should remain unresolved rather than merge both into one synthetic story.

---

## 6. Benchmark implication

Historical Transfer Bench should add a **competing-precedent evidence track**.

A case can provide:

- source precedent A → mechanism M_A → projection p_A;
- source precedent B → mechanism M_B → projection p_B;
- evidence items e1...en with known/elicited diagnosticity;
- several non-diagnostic facts that fit both A and B;
- one or two genuinely discriminating observations;
- a `no precedent` alternative.

Metrics should include:

- ranking of competing precedents;
- calibration of evidence likelihood / confidence;
- ability to recognize non-diagnostic overlap;
- sensitivity to disconfirming evidence;
- willingness to remain unresolved;
- forecast accuracy / Brier score where target outcomes are available.

---

## 7. How this connects to the reference-class bridge

The three control views now form a useful triangle:

```text
rich historical precedent
    → mechanism / explanation

reference class
    → base-rate / distributional calibration

competing hypotheses
    → diagnosticity / disconfirmation discipline
```

A mature controller should use all three:

1. retrieve rich historical analogues;
2. compare their mechanism claims against alternatives;
3. estimate the broader historical base rate;
4. state what evidence would justify deviating from both the outside view and competing analogues.

---

## Bottom line

Historical analogy's next control layer should not be designed as a more verbose reasoning template. Intelligence-analysis evidence warns that procedural complexity can fail to improve judgment, and current LLM evidence-weighting research shows that internal coherence can coexist with systematic overconfidence.

The engineering target is therefore:

> **alternative precedents + diagnostic evidence + outside-view base rates + empirically calibrated transfer confidence.**
