# Model Transfer in Science — What Exactly Is Being Moved?

**Snapshot: 21 August 2026.**

The philosophy-of-science literature on **model transfer** is a useful neighboring program because it studies a phenomenon broader than ordinary analogy: the same model form, method or representational framework migrates across scientific domains.

Catherine Herfeld's 2024 survey emphasizes that model transfer raises several separate questions:

- what exactly is transferred;
- why the transferred object is useful in a new target;
- whether success depends on structural/dynamical similarity or deeper ontology;
- what modifications/adaptations occur during transfer;
- how transfer affects scientific progress and domain formation.

These questions map directly onto modern analogical AI.

---

## 1. Transfer object is not always a conclusion

In ordinary analogy benchmarks the transferred object is usually an answer or relation:

```text
source relation → target relation
```

Scientific model transfer can move:

- mathematical form;
- modelling strategy;
- variable structure;
- mechanism template;
- idealization;
- solution technique;
- explanatory schema;
- inferential practice.

This suggests that an analogical system should explicitly identify its **transfer object type**.

```yaml
transfer_object:
  type: relation | mechanism | model-form | operator | parameterization | heuristic | procedure | prediction
  source_scope:
  target_scope:
  adaptation_required:
```

A system can otherwise confuse evidence that a formalism transfers with evidence that a specific substantive conclusion transfers.

---

## 2. Transfer success is not one epistemic property

A model may transfer successfully because it is:

- predictively useful;
- heuristically useful;
- mathematically tractable;
- explanatory;
- structurally revealing;
- a convenient common language;
- institutionally entrenched.

These are not equivalent.

### AI implication

A retrieved analogue can be useful without licensing the target prediction.

For example:

```text
source S helps construct target representation R  → useful
source S suggests candidate mechanism M          → useful
source S licenses outcome projection p            → not yet established
```

Benchmark labels should therefore distinguish **representational / heuristic utility** from **projective validity**.

---

## 3. Adaptation is part of transfer

Model transfer across disciplines is rarely copy-paste. Variables are reinterpreted, parameter meanings change, assumptions are relaxed or added, and the transferred model may become a new object.

This is highly relevant to analogical reasoning.

A mature controller needs:

```text
map
→ adapt/rebind
→ record which source assumptions were preserved
→ record which were altered
→ re-evaluate what projections remain licensed
```

The adaptation itself can destroy the evidential connection that motivated the transfer.

Thus:

```text
successful adaptation
≠
source confirmation transferred intact.
```

---

## 4. Model transfer and representation discovery

A transferred model can change how scientists conceptualize the target domain. This means representation is sometimes **downstream of analogy/transfer**, not simply its input.

Engineering consequence:

```text
source retrieval
↔
target representation
```

should be iterative.

A source model may expose latent target variables or relations; the new representation then changes which sources look relevant.

This supports a loop:

```text
initial target representation R0
→ retrieve source model S
→ adapt S to target
→ induce revised representation R1
→ rerun source search / mapping
```

---

## 5. Domain success does not prove ontology

The same mathematical model can work in unrelated fields without showing that the target systems share one deep ontology.

This matters for LLM analogy because a highly reusable abstract pattern can become seductive:

```text
same formal structure
→ model assumes same causal mechanism
```

That inference is unsafe.

A controller should explicitly separate:

```text
formal transfer validity
causal/mechanistic transfer validity
predictive transfer validity
```

and permit different answers.

Example:

```yaml
formal_structure: LICENSED
mechanism_identity: UNKNOWN
prediction_p: CONDITIONAL
```

---

## 6. Transfer history can create false evidence of universality

Once a model is widely reused, later domains may inherit its variable vocabulary, measurement conventions and problem framing. Cross-domain agreement can then partly result from the **shared modelling template**, not independent discovery of the same underlying structure.

For multi-analogue AI this creates a dependence problem:

```text
source A and source B use the same imported model family
→ their agreement is not automatically two independent confirmations
```

This should be recorded as representational genealogy / model-lineage dependence.

---

## 7. Translation to a transfer-control schema

For each candidate analogue/model source:

```yaml
source:
target:
transfer_object_type:
source_representation:
target_representation_before:
adaptation_operations:
target_representation_after:
formal_correspondence:
mechanistic_correspondence:
empirical_target_support:
projection_specific_status:
model_lineage_dependence:
```

The key distinction is:

> **A successful model transfer can be epistemically productive even when no particular source outcome should be copied to the target.**

That protects analogical intelligence from collapsing discovery/representation utility into prediction confidence.

---

## 8. Relation to current AI research

Current analogical AI work already spans different transfer objects without always distinguishing them:

- SAL transfers reasoning schemas;
- relational architectures transfer relation-processing inductive bias;
- YARN transfers abstract narrative structure;
- historical-analogy systems transfer mechanisms/trajectories;
- CBR systems transfer and adapt prior solutions;
- latent-space analogy methods transfer geometric transformations.

A unified field map should therefore index **what is transferred**, not only which task is solved.

---

## Core references

- Catherine Herfeld, “Model Transfer in Science,” in *The Routledge Handbook of Philosophy of Scientific Modeling* (2024). DOI: https://doi.org/10.4324/9781003205647-24
- Catherine Herfeld, “Model Transfer in the Recent History of Economics: The Case of Rational Choice Models,” *Perspectives on Science* 33(5), 2025.
- Nappo & Valente, *Analogical Reasoning in Science* (Cambridge Elements, 2026), which includes model transfer in the contemporary analogy landscape.
