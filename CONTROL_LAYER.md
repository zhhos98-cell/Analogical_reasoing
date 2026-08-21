# Control Layer — Are We Actually Training an Analogical Policy?

This note asks a stricter question than whether models can perform individual analogy tasks:

> **Which current systems coordinate representation, source search, selection, transfer, rejection, verification, and learning as a reusable control policy?**

The answer in August 2026 is: **several systems now cover important subsets of the loop, but no general system closes it end to end across domains.** The strongest trend is a shift from one-shot analogy prompting toward multi-stage or learned control over when and how analogical information is used.

A working control loop is:

`represent target`

`→ formulate source-search query`

`→ retrieve or generate candidate sources`

`→ rank/select/reject candidates`

`→ align relevant structure`

`→ rebind source-specific variables/conditions`

`→ project a candidate procedure or inference`

`→ execute/test`

`→ verify/calibrate`

`→ store success/failure boundary`

`→ update future representation, retrieval, and control`

---

## Coverage matrix

Legend: `✓` explicit/core; `~` partial/implicit/task-specific; `—` largely absent from the reported system.

| System | representation | source search | reasoning-aware ranking | explicit mapping / applicability | reject / abstain | rebind / contextualize | execute / infer | verify | multi-turn control | learned control policy | memory update |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| **Agentic Analogical Reasoning (AAR)** | ~ | ✓ | ✓ | ~ | ~ | ✓ | ✓ | ~ | ✓ | ✓ | — |
| **RA-RFT** | — | ✓ | ✓ | ~ | — | ~ | ✓ | ✓ outcome reward | — | ✓ | — |
| **CANA / ADR** | ✓ | ✓ | ✓ mechanism fit | ✓ | ✓ hard filters / partial | ~ | ✓ | ✓ cross-analogy | ✓ reflective rounds | — / scaffolded | — |
| **Abstain-R1 / detection-control line** | ~ | — | — | — | ✓ | — | ✓ / stop | ✓ answerability | ✓ | ✓ | — |
| **QCR trajectory reuse** | — | held fixed | held fixed | ✓ applicability conditions | ~ | ✓ | ✓ | ✓ | — | — | — |
| **BDH-CQ** | ✓ latent task state | demos supplied | — | ~ operator induction | — | ✓ query-conditioned | ✓ | ~ output based | ✓ recurrent latent | ✓ via training | ~ transient recurrent memory |
| **BALAR** | ✓ dynamic Bayesian state | active information seeking | information gain | state sufficiency | ~ | ✓ state update | ✓ | posterior update | ✓ | outer-loop, no fine-tuning | ✓ online belief state |
| **WorldEvolver** | ✓ evolving world-model context | transition retrieval | confidence filter | prediction applicability | ✓ low-confidence foresight filter | ✓ mismatch-driven revision | ✓ planning | ✓ prediction–observation | ✓ | explicit controller | ✓ episodic + semantic context |

The table matters because **none of these systems has all columns**. Progress is modular and distributed across different research communities.

---

## 1. Agentic Analogical Reasoning (AAR): the closest direct attempt to train the loop

**Tianhui Ma et al., “Agentic Analogical Reasoning for Large Language Models.”** Submitted to ICLR 2026; public OpenReview submission, not treated here as an accepted conference result.  
OpenReview: https://openreview.net/forum?id=0uj9pA5MqE

AAR is important conceptually because it rejects one-shot analogical prompting. It turns analogy into a multi-turn trajectory in which the reasoner repeatedly:

`thinking → analogizing → contextualizing`.

The analogizing step can formulate analogical queries to trigger either external knowledge retrieval or internally generated analogical exemplars. The system then selectively identifies useful analogies and feeds them back into subsequent reasoning. Training uses analogical trajectory generation, re-weighted trajectory training, and a mixed training strategy intended to internalize this behavior rather than leave it as a prompt-time scaffold.

### What it actually advances

- analogy becomes a **trajectory**, not a single inference;
- source search can recur during reasoning;
- internal and external source generation are both supported;
- analogical traces become training objects;
- contextualization/adaptation is explicitly downstream of source generation.

### What remains weak or unclear

The public paper reports strong downstream improvements across seven reasoning-intensive datasets, but the present evidence does not establish a calibrated `no useful analogy` policy, open-world validation, persistent memory of failed analogies, or domain-general source applicability criteria. Final-task performance can reward a trajectory that happens to work without proving that the analogy was epistemically well selected.

**Assessment:** the clearest direct evidence that the field is moving toward an **analogical control policy**, but still primarily a reasoning-performance system rather than a complete epistemic control architecture.

---

## 2. RA-RFT: retrieval utility becomes trainable

**Xiao et al., “Learning to Reason by Analogy via Retrieval-Augmented Reinforcement Fine-Tuning,” 2026.**  
Canonical: https://arxiv.org/abs/2606.13680

RA-RFT attacks one column very directly: **which source examples should enter the reasoning process?** Its retriever is trained to estimate expected reasoning benefit rather than lexical or semantic overlap. The policy is then reinforcement-fine-tuned with retrieved analogous demonstrations under verifiable outcome rewards.

On AIME 2025, the paper reports average@32 gains of +7.1 and +2.8 over GRPO for Qwen3-1.7B and Qwen3-4B respectively.

### What it actually advances

- source relevance is operationalized by downstream reasoning utility;
- retrieval and policy post-training are coupled;
- retrieved examples can provide complementary reasoning strategies rather than merely similar content.

### What it does not solve

- candidate analogy rejection as a calibrated action;
- explicit real-world structural mapping;
- open-ended source search across heterogeneous domains;
- adaptation/applicability conditions after retrieval;
- memory update from failed transfers.

**Assessment:** a strong solution to one important control variable, `what should I retrieve for reasoning?`, rather than the whole analogy loop.

---

## 3. CANA: the most explicit scaffolded selection / verification pipeline

**Chen et al., “Analogical Deep Research: Retrieving and Integrating Historical Analogies for Foresight Analysis,” 2026.**  
Canonical: https://arxiv.org/abs/2607.13602

CANA is notable because its algorithm exposes much more of the control logic than ordinary LLM-agent papers. It constructs descriptive and mechanistic representations, abstracts a target pattern and structural positions, generates candidate analogies, filters invalid candidates, extracts source mechanisms, scores position-level alignments, carries promising candidates across reflective rounds, and aggregates evidence.

The paper explicitly includes hard rejection rules for candidates such as aliases, sub-events/supersets, generic descriptors, and scope-class mismatches. It also uses **cross-analogy confirmation** rather than trusting a single source.

### What it actually advances

- representation and retrieval are connected through mechanism-level structure;
- candidate filtering/rejection is explicit;
- alignment evidence records both matches and residual gaps;
- multi-source confirmation is part of validation;
- retrieval is iterative and reflective rather than one-shot.

### A crucial condition on cross-analogy confirmation

CANA's Bayesian confirmation theorem explicitly assumes that confirmation signals are **conditionally independent across analogies given the latent structural position**. Under that assumption, independent confirming analogies multiply the posterior odds; in the paper's calibration, two independent confirmations suffice for the chosen threshold.

This turns an apparent downstream detail into a new control problem: a practical system must judge whether two retrieved analogies are genuinely independent enough to count as separate evidence. Shared data lineage, common causal templates, copied narratives, or one historical event downstream of another can create correlated confirmations.

### What remains weak or task-specific

- most control logic is scaffolded in the framework rather than learned as a generic policy;
- rejection rules are tailored to the ADR setting and are not a general analogical veto criterion;
- the theorem makes independence an explicit condition, while domain-general operational estimation of analogy dependence remains open;
- no persistent learning from successful/failed transfers is demonstrated.

**Assessment:** probably the richest current **explicit control pipeline**, but not yet a learned domain-general analogical controller.

---

## 4. Abstention systems: selection must terminate reasoning sometimes

The abstention/selective-prediction literature contributes a control primitive that analogy systems largely lack: **recognition that a candidate inference should not be executed**.

AbstentionBench (NeurIPS 2025) shows that reasoning fine-tuning can actually worsen abstention. AAAI 2026 work on unanswerable questions finds models may detect a flaw internally yet fail to convert that detection into the external action `stop / abstain`. Abstain-R1 shows this action can be explicitly trained with a clarification-aware RLVR objective.

### Analogical implication

An analogy system needs two distinct variables:

`mismatch detected?`

and

`therefore veto transfer?`

A powerful reasoner may improve the first while worsening the second by constructing a more elaborate rationalization for continuing.

**Assessment:** this neighboring field already has machinery for a missing analogical-control primitive, but analogy-specific hard-negative transfer tests are still absent.

---

## 5. Query-conditioned reuse (QCR): after retrieval comes applicability and rebinding

**Li et al., “Beyond Retrieval: Query-Conditioned Reuse of Long-Horizon Agent Trajectories,” 13 Aug 2026.**  
Canonical: https://arxiv.org/abs/2608.12847

QCR holds retrieval fixed and asks what an agent should receive from a past trajectory. Its target-bound reusable note records:

- reusable procedure;
- bindings that must be recovered or changed;
- applicability conditions;
- verification requirements.

Across 2,391 target instances, QCR reports 62.3% average success, +10.7 points over direct full-trajectory injection, with 48.9% fewer online tokens.

### Why this is almost an analogy-transfer module

It directly operationalizes the difference between:

`I found a relevant past case`

and

`I know which parts of that case can be reused here, what must be rebound, and how to check the transfer.`

This is one of the clearest adjacent-field demonstrations that **post-retrieval reuse is a distinct capability**.

**Assessment:** highly relevant to analogical projection/applicability even though the paper is framed as agent memory.

---

## 6. BDH-CQ: transient in-context operator schemas

**Engdahl et al., “BDH-CQ: In-Context Learning with Recurrent Latent Reasoning,” 10 Aug 2026.**  
Canonical: https://arxiv.org/abs/2608.09888

BDH-CQ is a compact 150M recurrent latent-reasoning model whose recurrent memory is conditioned by task demonstrations. The paper interprets the resulting state as a demonstration-conditioned operator schema: the current examples configure the model to apply a reusable visual transformation to new queries without changing model weights at inference time.

It reports 29.5% ARC-AGI-1 pass@2 at a computed cost of $0.00070/task, while still exposing significant failures on difficult composition and conditional structure.

### Why it matters for the control layer

It provides a candidate mechanism for **temporary analogical working state**: demonstrations configure a latent operator that is reused across query items. What it lacks is source search, rejection, persistent memory, and epistemic validation.

**Assessment:** promising substrate for operator induction, not a controller by itself.

---

## 7. Failure-driven agent learning: negative memory exists next door

A correction to the strongest version of the `negative memory is empty` claim is necessary. The broader agent field now contains serious work that learns from failed trajectories rather than discarding them.

- **AgentDebug / AgentErrorBench (2025)** diagnoses root-cause failures across memory, planning, reflection, action and system operations, then supplies targeted corrective feedback. The paper reports +24% all-correct accuracy, +17% step accuracy on error diagnosis, and up to 26% relative task-success improvement through iterative recovery.
- **Learning from Failure (2026)** turns failed computer-use trajectories into diagnosed failure modes and inference-time code patches, raising OpenCUA-72B on OSWorld from 42.3% to 48.9% without additional model training.
- **FORGE (2026)** compresses failed trajectories into reusable natural-language Rules and Examples and propagates high-performing memory across an agent population.
- **Mistake Notebook Learning (2026)** clusters repeated failures and distills them into structured mistake notes intended to prevent recurrence.

### What remains analogy-specific

These systems mostly store action/policy failures such as bad plans, tool errors, or recurrent mistakes. A genuinely analogical negative memory needs a more relational artifact:

`source S appeared applicable to target T`

`→ mapping/projection failed specifically because condition X did not transfer`

`→ future targets with X should down-weight S or this transfer pattern`.

That is not merely remembering that an action failed. It is learning an **applicability boundary on a source–target relation**.

**Assessment:** `negative memory` is an active adjacent field; **negative analogical memory** remains open.

---

## 8. Active reasoning and world-model revision: representation revision also exists next door

The broader active-reasoning field shows that state revision itself is becoming an explicit controller operation.

- **BALAR (2026)** maintains a structured Bayesian belief over latent states, selects questions by expected mutual information, and **dynamically expands its state representation when the current state space is insufficient**.
- **Information Self-Locking (ICLR 2026)** decomposes active reasoning into Action Selection and Belief Tracking and shows that weakness in either creates a feedback loop that traps RL agents in low-information regimes. Directional critiques help escape this self-locking and bring reported gains of up to 60% across seven datasets.
- **WorldEvolver (2026)** revises deployment-time world-model context from prediction–observation mismatches: episodic memory stores real transitions, semantic memory distills persistent heuristic rules, and selective foresight filters low-confidence predictions.

### What remains analogy-specific

These systems revise a belief state or world model when new observations contradict predictions. The still-underoccupied analogical problem is attribution and rerepresentation:

`analogical transfer failed`

`→ was the source bad, the alignment bad, the projected relation invalid, or the target representation itself wrong?`

`→ if representation was wrong, revise the relational decomposition and repeat source search/mapping.`

That requires failure credit assignment across the analogy pipeline rather than generic replanning or belief update.

**Assessment:** generic representation/belief revision is active; **mapping-failure-triggered relational rerepresentation** remains open.

---

# What is actually still empty?

Putting these systems together makes the remaining holes much sharper.

## Empty column 1 — learned rejection of a *plausible analogy*

CANA has explicit task-specific filters; abstention models can reject unanswerable questions. We still lack a broadly trained policy for:

`candidate is coherent + partially structurally aligned + nevertheless unsafe/invalid to transfer`.

This remains the cleanest underoccupied gap.

## Empty column 2 — analogy-specific applicability memory

Generic agent systems now learn from failed trajectories. The underoccupied problem is storing **why a source–target transfer failed** as a reusable applicability boundary, and using that boundary to improve later source ranking and rejection precision.

Without this, memory expansion can increase recall while leaving precision unchanged or worse.

## Empty column 3 — dependence-aware cross-analogy integration

CANA makes the condition unusually explicit: its confirmation theorem assumes analogies are conditionally independent given the latent mechanism. A general system therefore needs to estimate dependence among sources rather than merely count agreeing cases.

Five analogies derived from the same hidden template or evidence lineage should not count as five independent confirmations.

## Empty column 4 — analogy-triggered relational rerepresentation

Generic belief/state revision is now an active field. The narrower unresolved loop is:

`transfer/mapping failure → localize the failure to representation vs retrieval vs mapping vs projection → revise the relational representation if needed → re-run source search and alignment`.

Current analogy systems iterate retrieval and reflection, but there is little evidence of a learned, domain-general credit-assignment mechanism that uses transfer failure to revise the relational ontology/decomposition itself.

## Empty column 5 — execution-grounded epistemic update

Open-world science systems can generate and sometimes test candidates, but the full loop from experimental/tool outcome back into future analogical search, applicability estimates, and memory remains early.

---

# Current best synthesis

By August 2026, the field is no longer missing all the ingredients. It has:

- relation/mapping machinery;
- reasoning-aware retrieval;
- trajectory-level analogical training;
- explicit mechanism-matching pipelines;
- generic abstention policies;
- post-retrieval applicability/rebinding representations;
- in-context operator schemas;
- failure-driven agent memory;
- active belief/state revision;
- tool- or outcome-based verification in selected domains.

What it lacks is **integration under a learned policy with epistemic discipline and pipeline-level credit assignment**.

The frontier therefore looks less like inventing one new `analogy module` and more like learning a controller over existing capabilities:

`when to represent differently`

`when to search`

`what to retrieve`

`what to reuse`

`when to reject`

`what to test`

`what to remember from failure`

`whether multiple confirming analogies are actually independent`

`which stage caused a failed transfer`

`when that failure should alter future representations and retrieval`.

That is the strongest current formulation of the remaining engineering problem.
