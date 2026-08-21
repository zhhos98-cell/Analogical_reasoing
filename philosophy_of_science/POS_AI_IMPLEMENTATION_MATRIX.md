# PoS × AI Implementation Matrix — What Exists and What Is Still Missing?

**Snapshot: 21 August 2026.**

This matrix prevents two symmetric mistakes:

1. claiming a philosophy-of-science distinction is a novel AI idea when modern systems already implement it under another name;
2. assuming a modern analogy module satisfies an epistemic constraint merely because its output is fluent or structurally aligned.

## Matrix

| PoS control problem | Contemporary formulation | Closest current AI implementation | What the AI work has actually achieved | Remaining interface |
|---|---|---|---|---|
| **representation formation** | source/target descriptions and metrics are non-unique | YARN; relational abstraction architectures; LLM abstraction | raw narratives can be decomposed/abstracted before structural mapping; abstraction improves mapping | select/revise abstraction based on downstream epistemic performance rather than fixed levels/prompts |
| **dynamic context / rerepresentation** | source, target and reasoning context change during analogy | AAR iterative `thinking → analogizing → contextualizing`; general agent belief/state revision | iterative analogue trajectories and contextualization exist | typed revision of source vs target vs relevance context after transfer failure; detect destructive abstraction/contraction |
| **source relevance** | similarity is not inferential relevance | RA-RFT reasoning-aware retriever | retriever learns expected downstream reasoning benefit rather than semantic overlap | relevance is mostly source/task-level; need projection-specific relevance and target-context conditions |
| **mapping** | structural correspondence is necessary but not sufficient | YARN; SME/FAME hybrids; mechanistic transformer probes | explicit structural mapping can be improved by learned abstractions | preserve uncertainty over competing mappings/representations; mapping success must not imply transfer license |
| **bridge / meta-rule** | mapped feature `f` supports projection `g` only via background relevance relation | no clear general direct implementation; CANA mechanism role is partial analogue | some systems align mechanisms/roles and use them for projection | explicit learned `f → g` relevance operator with exception/context conditions and separate evidence support |
| **comparability evidence** | logical transfer premise needs independent evidential warrant | causal transportability / transferability estimation in structured domains; CANA grounded mechanism claims | structured domains can estimate transportability; open-event agents can cite source/target evidence | separate model-generated comparability premise from independent evidence that premise holds; circularity control |
| **projection-level selective transfer** | good analogy for X/Y does not automatically license inferred property Z | legal precedent distinguishing; CBR adaptation; historical CANA limitations | systems can reject/adapt sources and describe limitations | general open-representation `LICENSED / CONDITIONAL / VETOED / UNKNOWN` for each projected claim |
| **uncertainty / practical commitment** | uncertain extrapolation assumptions require managed confidence/action thresholds | forecasting-trained LMs; abstention/selective prediction; causal bounds | probability calibration and abstention can be trained | uncertainty tied to specific bridge assumptions/projections rather than only final answer confidence |
| **counter-hypotheses / analogical abduction** | analogy proposes explanatory hypothesis to be compared against rivals | agentic search; CANA multi-source; research agents | systems can retrieve/generate several candidate sources/hypotheses | active search for discriminating counter-analogues and evidence, not just additional support |
| **robustness** | agreement under varied auxiliaries may identify invariant core but is not automatically empirical confirmation | CANA cross-analogy confirmation; diverse retrieval; ensemble reasoning | multiple analogues can reinforce a structural role | vary assumptions intentionally; estimate redundancy; distinguish model-level robustness from target confirmation |
| **external validation** | successful source/model becomes stronger evidence only after model-external/target validation | scientific-discovery experiments; outcome resolution; mechanism falsification tools | source-derived hypotheses can sometimes be tested against target outcomes | explicit validation-state memory and projection-specific upgrade/downgrade of source families |
| **localism / domain warrant** | same transfer grammar may require field-specific evidential norms | modular tool/agent architectures | general controllers can call domain tools | no established shared analogy controller whose warrant predicates/falsifiers are learned or specified locally by scientific domain |
| **representation revision after failure** | failed analogy can rationally change concepts/feature space | general failure-memory/state-revision agents; DNN feature learning | agents can diagnose/repair steps and update memory | attribute failure to representation vs relevance vs applicability, revise the correct layer, and show held-out benefit |

---

# 1. Where contemporary AI is already ahead of a simplistic philosophy import

Several PoS slogans would be too weak as engineering contributions.

### `Use structural similarity instead of surface similarity`

Already implemented/attacked by YARN, relational architectures, CANA, reasoning-aware retrieval and classical structure-mapping hybrids.

### `Use multiple analogies`

Already implemented by CANA and many retrieval/ensemble systems. The unresolved question is dependence/robustness, not multiplicity itself.

### `Use context`

AAR and many modern agents contextualize analogies iteratively. The stronger issue is whether context is a **revisable epistemic state with typed failure attribution**.

### `Learn from failure`

Agent memory, CBR, ForecastCompass/OBAM and related systems already learn from resolved mistakes. The remaining problem is projection/relation-specific applicability boundary memory.

---

# 2. Where philosophy of science still seems to add a genuinely missing type

The strongest candidates are not full architectures; they are **state variables / labels** absent from standard analogy pipelines.

## A. Bridge/relevance object

```text
mapping:
  f(S) ≈ f(T)

bridge/meta-rule:
  sameness/difference on f is relevant to projected g under C

projection:
  infer candidate g(T)
```

Most systems collapse the second and third lines.

## B. Comparability-evidence object

```text
assumption A: source and target share mechanism m
support E_A: independent evidence for A
```

Most systems can state A; fewer distinguish `A is useful if true` from `we have evidence A is true`.

## C. Validation state

```text
candidate analogy
→ plausibility-supported
→ bridge-evidence-supported
→ target-validated
```

Current systems usually return one confidence score rather than remembering what kind of epistemic support a source family has earned.

## D. Typed revision target

```text
SOURCE_REPRESENTATION
TARGET_REPRESENTATION
RELEVANCE_RULE
MAPPING
APPLICABILITY
EXECUTION
```

Current failure repair is increasingly sophisticated but rarely tied to this analogue-specific credit assignment.

---

# 3. A minimal architecture hypothesis

A first prototype need not redesign a foundation model.

Use an existing LLM/retriever/mapping system and add an explicit controller state:

```yaml
source:
target:
source_representation:
target_representation:
mapping:
projection:
bridge_rule:
bridge_evidence_positive:
bridge_evidence_negative:
critical_difference:
transfer_state: LICENSED | CONDITIONAL | VETOED | UNKNOWN
probability:
counter_analogue:
falsifier_or_target_test:
validation_state:
revision_target_if_failure:
```

Then compare:

```text
baseline mapping system
vs
+ relevance state
vs
+ evidential state
vs
+ robustness/counter-source state
vs
+ validation/revision state.
```

This directly tests whether the PoS decomposition adds value.

---

# 4. Strongest near-term experiment

Use tasks with verifiable outcomes and controlled source-target differences.

Conditions:

```text
1. structural mapping is genuinely correct;
2. one mapped relation is relevant to projection p;
3. another mapped relation is real but irrelevant to p;
4. one target-side difference defeats p;
5. independent evidence for the bridge is either present or absent;
6. counter-analogue isolates the moderator.
```

Test whether the controller:

- preserves correct mapping;
- identifies relevant vs irrelevant shared structure;
- changes probability only for the affected projection;
- asks for evidence when bridge support is absent;
- uses the counter-analogue diagnostically;
- revises the correct state after outcome feedback.

Simulated worlds can establish causal ground truth; historical/scientific cases can test external validity.

---

# 5. Falsification criterion

The PoS layer is not justified by interpretability alone.

It must beat simpler systems on at least one hard dimension:

```text
far transfer
hard-negative precision
projection calibration
no-valid-analogy abstention
boundary response
counter-analogue retrieval
sample efficiency / evidence efficiency
failure recovery
```

If outcome-only RL + sufficiently large data learns the same behavior more efficiently, keep the PoS map as explanation/diagnosis rather than claim it as an architecture contribution.

## Bottom line

The current gap is no longer `AI needs philosophy to know that analogies have limits`.

The sharper research hypothesis is:

> **Modern AI already supplies representation, retrieval, mapping and iterative search. Contemporary philosophy of science may contribute a missing typed control layer between mapping and epistemic commitment: relevance, independent comparability evidence, selective transfer, robustness status, external validation and typed revision.**

Whether that layer deserves to exist is an empirical question.