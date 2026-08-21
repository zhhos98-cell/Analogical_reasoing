# AI Representation Change — From Scientific Concept Revision to Neural Feature Revision

**Snapshot: 21 August 2026.**

A recurring problem in analogical reasoning is that the correct source–target correspondence may not exist under the model's initial representation. The system may need to **change the representation before a useful analogy becomes visible**.

This is not only a cognitive-science idea. Contemporary philosophy-of-science / philosophy-of-AI work is beginning to compare scientific conceptual change directly with representation/feature change in deep neural networks.

---

## 1. Votsis 2025 — scientific concepts and DNN features as changeable representational units

Ioannis Votsis, **“Concept and Feature Change in Scientific and Deep Neural Net Representations”**, CogSci 2025.

The paper argues that scientific representations and DNN representations both undergo changes to their constituent representational elements:

```text
scientific theory/model:
  concepts + relations

DNN model:
  features/variables + parameters + functional relations
```

The paper explicitly asks whether methodological practices for handling scientific conceptual change can cross-pollinate with methods for feature change in machine learning, and vice versa.

Canonical open version: https://escholarship.org/uc/item/13t3k5v6

### Why this matters for analogy

Current analogy pipelines often assume:

```text
encode source
encode target
→ map
```

But if source and target are encoded at incompatible levels of abstraction, the correct operation may be:

```text
encode
→ attempt mapping
→ diagnose mismatch
→ revise features/concepts
→ remap
```

The ability to change the representational vocabulary is therefore part of analogical reasoning, not merely a preprocessing step.

---

## 2. Representation failure needs a typed response

A failed analogy can arise because:

```text
A. source is wrong
B. target source mapping is wrong
C. projected relation is not transferable
D. target representation is wrong
E. source representation is wrong
F. abstraction level is wrong
```

Most present systems treat these failures similarly: try another prompt/source or produce another answer.

A representation-aware controller should have a specific action:

```text
REREPRESENT
```

alongside:

```text
RETRIEVE_AGAIN
REMAP
VETO_PROJECTION
ACQUIRE_EVIDENCE
ABSTAIN
```

---

## 3. What counts as representation revision?

For modern AI, rerepresentation may mean:

- splitting one entity into several roles;
- merging entities into a higher-level functional unit;
- changing temporal granularity;
- replacing attribute similarity with relational structure;
- introducing a latent mediator;
- changing causal direction;
- replacing a domain-specific predicate with a functional/structural one;
- shifting from instance representation to process representation;
- changing which variables are treated as state vs context;
- discovering a new operator or transformation.

The key is that the mapping space itself changes.

---

## 4. Analogy as a test of representation

True Gibson's 2025 analysis of Darwin shows that an analogy's epistemic role can reverse after conceptual revision. The broad source–target comparison remains recognizable, but changes in the surrounding concepts alter what the analogy supports.

This suggests a useful AI principle:

> **A failed or contradictory analogy is evidence about the adequacy of the representation, not only evidence about the source.**

Training data should therefore include cases where the correct action is:

```text
mapping fails under R0
→ revise to R1
→ same source becomes useful
```

and the converse:

```text
mapping seems strong under R0
→ target evidence forces R1
→ source loses projective relevance
```

---

## 5. Dynamic contexts / belief revision

Recent formal work on analogy and context update models source context, target context and reasoning context as changeable belief sets rather than fixed inputs. Analogy can trigger expansion, contraction and revision.

That suggests the analogical controller should track state explicitly:

```yaml
source_context_version:
target_context_version:
reasoning_context_version:
revision_trigger:
revision_operation:
changed_relations:
mappings_invalidated:
mappings_created:
```

This makes representation change auditable rather than hiding it inside a long chain of thought.

---

## 6. A benchmark for representation revision

Construct pairs where the same surface observations admit two representations:

```text
R0: obvious / familiar / misleading
R1: less obvious / structurally predictive
```

Example task structure:

```text
1. give target observations
2. request source analogue + mapping
3. provide evidence inconsistent with the initial projection
4. measure whether the system:
   a. merely lowers confidence
   b. retrieves a new source
   c. changes representation
5. test new predictions under the revised representation
```

Metrics:

- representation-revision rate when revision is needed;
- unnecessary-revision rate;
- post-revision mapping accuracy;
- held-out predictive gain;
- ability to recover previously unusable sources;
- representation stability after irrelevant evidence.

---

## 7. Relation to modern AI results

Several contemporary findings make this especially timely:

- YARN finds no single abstraction level is optimal across narrative analogies;
- concept-vector work finds abstract relational concepts may lack stable linear representations;
- multimodal analogy benchmarks show reasoning compute cannot repair a bad initial decomposition;
- object-centric/neuro-symbolic systems often outperform generic reasoning models when perceptual factorization matters;
- active-reasoning work already allows latent-state expansion/revision when existing state is insufficient.

The missing integration is:

```text
analogical failure
→ diagnose representation mismatch
→ targeted rerepresentation
→ remapping
→ transfer re-evaluation
```

---

## 8. Scientific-reasoning interpretation

If AI is intended to support scientific discovery, representation revision is central because novel science often changes the objects and relations being compared.

A system that only searches over sources under a fixed ontology may be excellent at analogy retrieval while remaining weak at **analogical discovery**.

The stronger target is:

```text
analogy helps discover a new representation
and the new representation changes what analogies are possible.
```

That feedback loop is one of the clearest PoS/AI frontier problems in this repository.

---

## References

- Ioannis Votsis, “Concept and Feature Change in Scientific and Deep Neural Net Representations,” CogSci 2025. https://escholarship.org/uc/item/13t3k5v6
- True Gibson, “Conceptual revision: how Darwin's analogy supported his theory,” *Biology & Philosophy* 40 (2025), article 16.
- Votsis's current Science & AI program also explicitly links analogical reasoning, neuro-symbolic scientific discovery and representation change: https://www.votsis.org/science_ai.html
