# Universal vs Local Analogy Control — An Architecture Question, Not Just a Philosophical Dispute

**Snapshot: 21 August 2026.**

Contemporary philosophy of analogy contains a live dispute that can be translated almost directly into an AI architecture comparison.

## 1. Three positions

### A. Universal model

A single sufficiently rich model should state general conditions under which analogical inference is good or bad.

Votsis's discussion of `one-size-fits-all` analogical reasoning treats this as still potentially defensible if universal models are supplemented by criteria such as **relevant conceptual uniformity**.

Engineering form:

```text
one global transfer controller
shared parameters
same relevance/applicability function across domains.
```

### B. Localist model

The material/localist position emphasizes that analogical warrant depends on domain-specific facts and practices. No content-free universal similarity rule can determine which properties matter.

Engineering form:

```text
domain-specific transfer heads / policies
field-specific evidence and relevance rules.
```

### C. Shared inference grammar + local meta-rules

Zwirn & Zwirn offer a useful intermediate structure. General inference schemes can remain stable while the **meta-rules** that make one dimension relevant to another are domain/background dependent.

Engineering form:

```text
shared controller state machine
+
learned/retrieved domain-local relevance rules.
```

This is currently the most attractive compromise to test.

---

# 2. Why a universal scalar analogy score is especially suspect

Suppose the model learns:

```text
score(S,T) ∈ [0,1].
```

The same score must somehow summarize:

- structural similarity;
- causal relevance;
- source reliability;
- target-side evidence;
- projection type;
- domain-specific standards;
- uncertainty;
- known exceptions.

That compression is likely to destroy precisely the information needed for selective transfer.

The problem is not merely interpretability. Two sources can deserve the same global score while licensing different projections.

---

# 3. But fully local systems have costs

A separate controller for every scientific field risks:

- poor transfer to new domains;
- high annotation cost;
- duplicated reasoning machinery;
- brittle domain boundaries;
- inability to exploit analogies precisely because domains are siloed.

Scientific analogies often matter because they cross fields. A controller that cannot carry any warrant structure across domains defeats part of the purpose.

---

# 4. Candidate modular architecture

A middle architecture:

```text
GLOBAL GRAMMAR
  representation alternatives
  source candidates
  mapping
  projection
  bridge rule
  evidence positive/negative
  LICENSED / CONDITIONAL / VETOED / UNKNOWN
  uncertainty
  falsifier
  validation state
  revision target

LOCAL WARRANT MODULE
  what counts as mechanism evidence?
  which variables/relations matter?
  what are standard confounders?
  what evidence threshold is acceptable?
  what intervention/observation can validate transfer?
```

The global grammar defines **what questions must be answered**. The local module defines **what answers count as evidence**.

---

# 5. Domain-local modules need not be handcrafted

Possible implementations:

### Retrieval-based

Retrieve domain methodology, causal knowledge, experimental standards and known failure conditions.

### Learned expert heads

Fine-tune small heads/adapters on field-specific transfer judgments.

### Tool-based

Use different validators:

```text
physics → equations/simulation/perturbation tests
biomedicine → causal pathways/intervention datasets
forecasting → proper scoring / frozen timelines
history → provenance/chronology/institutional dependence
```

### Meta-learned

Infer a local warrant policy from a few labeled examples in a new scientific domain.

---

# 6. Direct architecture experiment

Use several domains with structurally parallel transfer tasks.

Train/compare:

```text
U: universal controller only
L: separate local controller per domain
G+L: shared grammar + local warrant module
META: shared controller that meta-learns local warrant rules
```

Evaluate:

- in-domain projection F1;
- calibration;
- hard-negative rejection;
- cross-domain zero-shot transfer;
- few-shot adaptation to a new field;
- robustness to changed representation/metric;
- sample efficiency;
- explanatory fidelity of stated evidence conditions.

## Prediction

A plausible hypothesis is:

```text
U wins portability but loses local calibration;
L wins in-domain precision but loses transfer;
G+L / META may dominate the Pareto frontier.
```

This is a hypothesis to test, not a philosophical conclusion.

---

# 7. Relevant conceptual uniformity as a learnable quantity

Votsis's universalist rescue strategy points to **relevant conceptual uniformity**: transfer is more plausible when the concepts involved behave uniformly in the respects relevant to the inference.

A computational version could ask whether a relation/concept has stable predictive consequences across source instances:

```text
uniformity(f → g, domain D)
= stability of P(g | f, D) under relevant perturbations.
```

This converts a philosophical criterion into an empirical representation diagnostic.

If `f → g` changes radically across contexts, the model should lower confidence in universal transfer and rely more strongly on local evidence.

---

# 8. Connection to current AI

Modern systems already show the ingredients:

- RA-RFT learns reasoning relevance rather than lexical similarity;
- YARN varies abstraction levels;
- CANA imposes mechanism-oriented representations;
- agent systems call domain-specific tools;
- forecasting systems train specialized calibration behavior.

What has not emerged as a standard architecture is an explicit separation between:

```text
universal transfer-control grammar
and
domain-local epistemic warrant.
```

---

# 9. Falsification criterion

The modular/localism hypothesis should be rejected if:

- a sufficiently scaled universal controller matches local calibration across heterogeneous domains;
- local warrant modules add complexity without measurable OOD/rejection/calibration gains;
- domain boundaries are too unstable for local policies to help;
- end-to-end outcome training implicitly learns the same distinctions more efficiently.

## Bottom line

The universal/local philosophy dispute can be turned into a straightforward architecture competition:

> **Should analogical intelligence learn one universal transfer function, many domain-specific functions, or one shared control grammar whose relevance/evidence rules are local and revisable?**

That question is experimentally answerable.