# Computational Prehistory — Historical Analogy in AI Before LLMs

**Scope:** computational work on precedent/analogy in international decision-making, not the intellectual history of analogy itself.

Modern LLM papers should not be described as the first attempt to computationalize historical analogy. A small but striking AI/international-relations line already existed in the 1980s and early 1990s.

---

## 1. Mefford — historical analogy as a foreign-policy representation problem

### 1984

**Dwain Mefford, “Formulating Foreign Policy on the Basis of Historical Analogies: An Application of Developments in Artificial Intelligence.”** Paper presented at the International Studies Association, Atlanta.

The paper is repeatedly cited in contemporary 1980s AI/political-modeling literature as an explicit attempt to formulate foreign-policy reasoning through historical analogies.

### 1987

**Dwain Mefford, “Analogical Reasoning and the Definition of the Situation: Back to Snyder for Concepts and Forward to Artificial Intelligence for Method,” in _New Directions in the Study of Foreign Policy_.**

The key problem is familiar today: actors do not merely respond to an objective situation; they **construct a situation** by selecting which past incidents make the present intelligible. Historical analogy is therefore part of representation formation, not just an after-the-fact rhetorical comparison.

A case study of Soviet involvement in Czechoslovakia is used to explore computer-readable coding of international events/sequences.

---

## 2. Schrodt — Adaptive Precedent-Based Logic

**Philip A. Schrodt, “Adaptive Precedent-Based Logic and Rational Choice: A Comparison of Two Approaches to the Modeling of International Behavior,” in _Dynamic Models of International Conflict_ (1985/86), pp. 371–400.**

The chapter appears in a section explicitly titled **Artificial Intelligence Approaches**, alongside Mefford's logic-programming work on changes in foreign policy across time.

Schrodt's broader program compared precedent/pattern-based models with rational-choice or statistical approaches and later developed pattern matching over international event sequences.

The important computational intuition is:

`current situation → match against stored precedents/event patterns → use precedent consequences to constrain prediction/choice`.

That architecture is recognizably related to modern retrieval/replay systems even though its representation technology was radically weaker.

---

## 3. AI as a safeguard against bad historical analogy

A later Naval Postgraduate School study, **_Artificial Intelligence and Foreign Policy Decision-Making_**, articulates a design goal that is unexpectedly close to the 2026 frontier.

It treats historical analogy as both useful and dangerous: decision-makers can lock onto apparently corresponding historical events and ignore the current situation's differences. The proposed AI response is to:

1. survey and present analogous historical examples;
2. analyze the differences between past and present contexts;
3. simulate scenarios incorporating those changed conditions;
4. prevent commitment to an incorrect historical paradigm.

This is notable because modern systems are rediscovering the same control problem with much stronger representation models.

---

# Old problem, inverted technical strengths

The contrast between the two eras is unusually clean:

### 1980s–90s

`explicit precedent logic`

`+ explicit concern with applicability/differences`

`+ structured event representations`

`− weak natural-language representation`

`− tiny case bases / expensive hand coding`

`− weak retrieval/generalization`

### 2020s

`powerful natural-language representation`

`+ huge implicit case memory`

`+ generative source search`

`+ web/deep-research tooling`

`− source-selection precision`

`− calibrated transfer validity`

`− explicit persistent applicability boundaries`.

The modern problem is therefore not simply that LLMs have finally made historical analogy computationally possible. They have reversed the bottleneck.

Earlier systems had explicit control but weak representation; current models have flexible representation/search but weaker disciplined control over what a precedent licenses.

---

# Why this matters for novelty claims

A modern historical-analogy paper can still be novel in architecture, scale, representation learning, open-world search or evaluation. But claims such as “AI has not previously treated historical precedent computationally” should be checked against at least:

- Mefford (1984, 1987);
- Schrodt's Adaptive Precedent-Based Logic (1985/86);
- early AI/pattern-recognition work on international event sequences;
- 1990s expert-system / intelligence situation-assessment work citing historical-precedent methods.

The useful contemporary genealogy is computational rather than philosophical:

`hand-coded precedent reasoning`

`→ event-sequence pattern recognition`

`→ statistical/trajectory analogue retrieval`

`→ foundation-model historical source acquisition`

`→ mechanism-aligned multi-precedent reasoning`.

The missing link is still a general learned system that combines open representation with the old ambition of **difference-aware precedent control**.
