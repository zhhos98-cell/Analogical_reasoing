# Philosophy of Science — Analogy, Extrapolation and Transfer

**Snapshot: 21 August 2026.**

This branch maps contemporary philosophy of science as a technical neighbor of modern AI analogical reasoning. It is not a history-of-ideas branch and is not organized by canonical thinkers.

The central question is:

> **What does contemporary philosophy of science say must be true before evidence, mechanisms or outcomes observed in a source can legitimately support a claim about a target?**

That question is very close to the current AI frontier around open-world source→target transfer validity.

## Start here

- [`CURRENT_MAP.md`](CURRENT_MAP.md) — eight-part decomposition of the current epistemology of analogy/transfer.
- [`FORMAL_CONFIRMATION.md`](FORMAL_CONFIRMATION.md) — Bayesian confirmation, formal analogical inference and why similarity is not itself confirmation.
- [`TRANSFER_AND_EXTRAPOLATION.md`](TRANSFER_AND_EXTRAPOLATION.md) — external validity, the logical/evidential/practical problems of extrapolation, uncertainty and target-side evidence.
- [`REPRESENTATION_AND_SIMILARITY.md`](REPRESENTATION_AND_SIMILARITY.md) — source/target non-uniqueness, metric dependence, inferred properties and conceptual revision.
- [`../data/philosophy_of_science_analogy.csv`](../data/philosophy_of_science_analogy.csv) — structured literature map.

## Current high-level result

Contemporary philosophy of science does **not** treat analogical inference as a scalar function of source–target resemblance.

The literature repeatedly separates at least four questions:

```text
1. Representation:
   what exactly are source and target, under which description?

2. Logical transfer:
   if certain comparability premises hold, what conclusion follows?

3. Evidential support:
   what target/source evidence actually warrants those comparability premises?

4. Practical commitment:
   given uncertainty, when should we act, forecast, extrapolate or abstain?
```

A major engineering implication is that an AI analogue controller should not output only:

```text
analogy_score(S,T) = 0.84
```

but something closer to:

```text
representation R
projection p
comparability assumptions A
supporting evidence E+
blocking evidence E-
transfer status: LICENSED / CONDITIONAL / VETOED / UNKNOWN
uncertainty
falsifier / target-side test
```

## Why the field is active now

Francesco Nappo and Giovanni Valente's **_Analogical Reasoning in Science_** appeared in Cambridge Elements in the Philosophy of Science in June 2026. Its stated premise is that the exact epistemological role of analogy in science remains an outstanding contemporary problem despite its importance in scientific discovery and inference.

Canonical: https://doi.org/10.1017/9781009526494

Recent work also develops Bayesian confirmation models, competing formal structures of analogical inference, philosophy of climate analogues, extrapolation under uncertainty, analogical abduction, biomedical similarity and representation revision.

## Working bridge to AI

The current AI and philosophy-of-science maps appear to meet at the following interface:

```text
AI strength:
open representation + large-scale source search + flexible mapping

PoS strength:
comparability premises + evidential relevance + uncertainty + external validity + falsification discipline
```

The research opportunity is not to insert philosophical vocabulary into an LLM prompt. It is to determine whether these normative distinctions can become **training targets, control states, benchmark labels or validation constraints** for analogical systems.