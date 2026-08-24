# Reference Classes and Historical Analogies — From One Precedent to a Distribution of Pasts

**Snapshot: 21 August 2026.**

Historical analogy usually foregrounds one or several specific precedents. **Reference Class Forecasting (RCF)** asks a deliberately different question:

> Instead of choosing one vivid past case, what happens if we define a class of comparable past cases and use the distribution of their realized outcomes?

RCF is therefore not identical to historical analogy, but it is a crucial calibration neighbor. It supplies a disciplined “outside view” against which rich precedent narratives can be checked.

---

# 1. The basic contrast

## Case-based historical analogy

```text
target T
→ retrieve source S
→ map structure/mechanism
→ adapt lesson/outcome to T
```

Strength:

- rich mechanism/context;
- interpretable individual precedent;
- can represent unique causal structure.

Risk:

- vivid-case capture;
- source cherry-picking;
- seductive but unrepresentative precedent;
- uncertain outcome transfer.

## Reference-class forecasting

```text
target T
→ define comparable class C = {S1...Sn}
→ estimate historical outcome distribution P(Y|C)
→ place/adjust T within that distribution
```

Strength:

- distributional calibration;
- explicit base rates;
- less dependence on one canonical story.

Risk:

- the **reference class problem**: what counts as genuinely comparable?
- heterogeneous cases can flatten mechanism differences;
- choice of class can determine the result.

Historical analogy and RCF therefore share an upstream problem — **representation and source selection** — but impose different downstream discipline.

---

# 2. RCF remains an active 2026 methodology, not a historical footnote

### Cantarelli, Davis, Pinto & Turner, 2026

**_Reference class forecasting: promises, problems, and a research agenda moving forward_.**  
Production Planning & Control 37(7), 691–709.  
Canonical: https://doi.org/10.1080/09537287.2025.2578708

The 2026 systematic review describes RCF as increasingly institutionalized in project planning and public policy. It emphasizes both its ability to counter optimism/uniqueness bias and continuing questions about validity, applicability and reference-class construction.

The field's central difficulty is directly relevant to historical analogy:

`which past cases belong in the comparison set?`

A class that is too broad gains sample size but loses structural comparability. A class that is too narrow gains similarity but loses distributional evidence.

---

# 3. AI/ML can automate dynamic reference-class selection

### Queensland TMR / ARRB / NACOE, 2019–20 project report

**_Exploring the use of artificial intelligence (AI) solutions to improve the accuracy of project delivery forecasts_.**  
Report page: https://nacoe.com.au/reports/o18-exploring-the-use-of-artificial-intelligence-ai-solutions-to-improve-the-accuracy-of-project-delivery-forecasts-2019-20

The project explores ML over historical infrastructure-project data to improve cost and duration forecasting. The assessed system uses **dynamic reference class forecasting**: machine learning identifies predictive patterns across historical project records and constructs forecast-relevant comparisons rather than relying on a manually fixed class.

This is a useful older applied-AI precedent for the historical-analogy project:

`historical case archive → learned reference-class membership / predictive patterns → calibrated project forecast`.

It is much narrower than event-level historical analogy, but demonstrates that **machine-selected historical comparability can be operationalized and tested against outcomes**.

---

# 4. Distributional reference-class selection is itself a learnable problem

### Theising 2024 — corporate sales growth

**_Distributional Reference Class Forecasting of Corporate Sales Growth With Multiple Reference Variables_.**  
Canonical: https://arxiv.org/abs/2405.03402

The method selects reference classes using several covariates and evaluates the resulting predictive distributions on 21,808 U.S. firms over 1950–2019.

This makes the reference-class problem quantitative:

- choose variables defining comparability;
- choose class size/rank selection method;
- generate a distribution rather than a single-point precedent prediction;
- backtest against realized outcomes.

### Historical-analogy lesson

A future event-level system could treat `precedent retrieval` as two linked outputs:

1. a few **rich source analogues** for mechanism reasoning;
2. a broader **reference class** for base-rate calibration.

The two sets need not be identical.

---

# 5. Why reference classes matter for CANA-style multi-precedent reasoning

CANA integrates several historical analogies through structural roles. This is richer than RCF, but its multi-precedent output can benefit from a distributional outside view.

A possible hybrid pipeline:

```text
T
→ rich representation / candidate mechanism hypotheses
→ retrieve structurally informative precedents S1...Sk
→ construct wider reference class C under the same representation
→ estimate historical outcome/base-rate distribution in C
→ compare analogy-derived projection with outside-view distribution
→ flag large divergence for review/evidence acquisition
```

Example output:

```text
Mechanism analogies suggest escalation risk: 0.70
Reference-class base rate under broader comparable cases: 0.32

Divergence reason proposed:
  target contains amplifier X absent in most class members

Required evidence:
  establish whether X is active before overriding base rate
```

This is stronger than either approach alone. A rich analogy can explain why the target might legitimately deviate from a base rate; the reference class forces that exceptionalism claim to be explicit.

---

# 6. Reference classes can reduce the “vivid precedent” problem

Historical policy reasoning is frequently captured by canonical cases — Munich, Vietnam, 1914, 1929, 1970s inflation, etc.

A reference-class layer changes the question from:

`Which famous case does this remind us of?`

into:

`Among all cases satisfying our stated comparability criteria, what outcomes actually occurred?`

This is particularly valuable for AI because LLM source generation is itself shaped by frequency and cultural salience in training data.

A benchmark should therefore include **famous-but-unrepresentative precedents** and score whether a system can resist them when the broader historical distribution points elsewhere.

---

# 7. But RCF does not solve historical analogy

The outside view can also erase the very differences that make historical reasoning useful.

A broad reference class may conceal:

- regime changes;
- institutional discontinuities;
- technological transformations;
- strategic interaction;
- causal mechanisms unique to a target;
- path dependence.

Historical analogy's contribution is precisely the ability to say:

`the target should deviate from the base rate because structural condition X is different`.

The challenge is to require evidence for that move rather than allowing narrative exceptionalism.

---

# 8. Benchmark implication: score both case and class reasoning

Historical Transfer Bench should eventually add an optional **outside-view track**.

For suitable target domains, provide:

- candidate rich precedents;
- a larger reference-class database with realized outcomes;
- multiple plausible class definitions.

Test whether systems can:

1. choose a defensible reference class;
2. estimate/report its outcome distribution;
3. retrieve rich mechanistic precedents;
4. identify when the rich analogy agrees/disagrees with the outside view;
5. justify deviations from base rates using target-specific evidence;
6. calibrate confidence when class and case reasoning conflict.

This creates a particularly useful tension:

`inside/mechanism view`

vs

`outside/reference-class view`.

A mature historical-analogy controller should be able to use both rather than treating one vivid precedent as a substitute for a distribution of historical experience.
