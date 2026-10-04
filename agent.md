# Shared Writing and Research Rules

Project-specific instructions override this file when more specific. These rules apply most strongly to historical, humanities, HPS, and research prose. For code/data/slides, preserve the same source and attribution discipline without forcing prose structures onto technical work.

## 1. Object before abstraction
Build from concrete objects, actions, texts, manipulations, observations, and actor wording. Preferred sequence: `object/text/action -> reported alteration or claim -> actor inference -> reconstructed bridge -> local test/alternative -> bounded result -> historiographical/conceptual payoff`. Abstract terms may summarize only after object-level work is visible. Close reading is primary; theory should sharpen a source-level problem, not replace one.

## 2. One auditable operation per sentence
Treat each sentence as `S_n : state_n -> state_(n+1)`. Normally perform one principal operation: first-order fact; actor/date/work relation; manipulation/result; wording-sensitive quotation; actor inference; necessary reconstructed premise; local test; limitation; historically available alternative; or forward question. Avoid combining independently auditable facts, historiography, and thesis in one sentence. Synthesis may combine already-established states. Sentence ledgers are analytical tools, never prose quotas.

## 3. Source hierarchy
`L1 first-order body/manipulation/wording/date -> L2 actor inference -> L3 source-near reconstruction -> L4 local limit -> L5 historiography -> L6 conceptual payoff`. No L5/L6 may replace missing L1-L3. Always distinguish what the actor says, what the source permits us to reconstruct, and what the article adds.

## 4. Source ceiling and modal force
Never write more strongly than the controlled source permits. Track whether a claim is explicit, implied, reconstructed, possible but unproven, or absent. Preserve modal force (`may`, `seems`, `probable`, `more probable`, `could`). Do not turn probability into demonstration, compatibility into proof, sequence into causation, correlation into mechanism, or a proposed experiment into a completed one. Do not infer borrowing, influence, intention, consensus, novelty, or causal dependence merely from proximity. Prefer narrower relations such as predates, parallels, repeats an operative sequence, shares a repertoire, or supplies a precedent. Avoid mental-state claims such as `judgment`, `confusion`, or `failure to understand` unless warranted.

## 5. Paragraphs and first-order density
A paragraph should be an inferential event. Historical/reconstruction paragraphs usually contain 5-10 sentence operations; 1-2 sentence paragraphs are exceptional. Use `FO_share = (first-order facts + wording-sensitive quotations) / sentences` only diagnostically. Roughly 60-85% FO is often healthy in historical reconstruction. Low FO can signal analysis arriving too early; extremely high FO can signal fact-listing without inference. Analytic paragraphs may have low/zero FO only when preceding material is source-rich, the paragraph stays compact, and it creates a new distinction or forward problem. Do not force uniform paragraph lengths.

## 6. Benchmark imitation
Imitate model articles at the level of operations, not wording, syntax, sentence length, or surface organization. The benchmark is a density ruler, not a template. Reproduce an equivalent move only if the present sources require it. Do not manufacture extra scholars, archive material, or objections for symmetry.

## 7. Historiography at hinges
Historical reconstruction should normally be historiography-poor. For every historiographical sentence H require: `PRE(H)` = source/case state before it; `JOB(H)` = exact operation performed; `POST(H)` = new question/distinction/reconstruction made possible. If POST is only `this supports our interpretation`, delete or demote H. Useful jobs include prior/competing explanation, classification, narrow conceptual distinction, textual/lexical control, or precise article delta. Return quickly to primary material. Frameworks normally enter after the historical reasoning they clarify has been reconstructed.

## 8. Repetition and recurrence
The same fact may recur only when its inferential role changes: `object -> actor premise -> opponent target -> conceptual test -> bounded conclusion`. If the role is unchanged, cut or paraphrase. Exact wording should recur only when it carries new work.

## 9. Defensive sentences
Distinguish `N_source` from `N_defense`. Retain negative statements that are genuine source limits: no provenance, proposed but uncompleted trial, unresolved mechanism, explicit epistemic restriction. Rewrite defensive constructions that merely anticipate an overclaim. Prefer `X bears on B / leaves A open` to `X does not prove A; it only shows B`. Do not add analyst-generated escape routes against every imaginable objection. Avoid repetitive `not X but Y`, `not merely`, `does not mean`, and disclaimer-style prose when the positive state can be stated directly.

## 10. Analyst vocabulary
Use `A1 actor/source wording`, `A2 source-near reconstruction`, `A3 analyst shorthand`. Public prose should prefer A1-A2. Translate shorthand back into source operations where possible: `ranking -> more probable/more credible`; `prediction -> process should produce a consequence`; `discrimination -> outcome E1 counts for C1, E2 for C2`; `compatibility -> same sequence fits two histories`; `cost -> a consequence gives reason to prefer another cause`; `cumulative -> several arguments make different alterations bear on one account`. Do not let control vocabulary become actor attribution.

## 11. Quotations and formalization
Quote only when wording matters: modal force, technical term, lexical ambiguity, consequential phrase, or exact inferential formulation. Short quotation + explanation is usually stronger than long quotation. A quotation cannot replace reconstructed reasoning. Formal symbols are checking devices, not a theory section; public prose should return quickly to bodies, words, actors, and actions.

## 12. Citation placement
Cite at the smallest sentence completing the source-dependent proposition. Avoid paragraph-end omnibus notes. A source-near inference after a fully cited fact may not need a new note if it adds no new historical proposition. Cite all relevant source bundles when a synthesis combines them. Never invent pages, sections, archival references, or exact quotations; mark unresolved locators as gaps until hardened.

## 13. Reader orientation and style
Identify historical persons on first meaningful appearance when needed. Do not assume specialist background unnecessarily. Use dates and sequence to make relations auditable. First person is allowed when it clarifies an argumentative decision, source limit, or route.

Prefer continuous argument over modular note-like prose. Avoid A-B-C-D-E-F inventories when an inferential sequence works better; repeated thesis restatements; generic claims that something is `complex`, `material`, `entangled`, or `contextual` without specifying the relation; strings of abstract nouns after the object disappears; inflated novelty claims; defensive throat-clearing; and meta-commentary that says a point is important instead of showing why. Section endings should compare, limit, or hand off to the next unresolved question rather than inventory completed operations.

## 14. Conclusions
Synthesize only what the body has earned. Do not introduce new archive material, new secondary literature, or larger theoretical vocabulary at the end. Return to the concrete object, actor, practice, or textual problem. State a bounded result and remaining limit. Prefer a precise local contribution to a universal claim.

## 15. Self-correction loop
Repeatedly ask: Is this first-order fact still needed? Is this inference actor-level or ours? Does this sentence perform a new state transition? Does the paragraph contain enough material before analysis? Has a repeated fact changed role? Does historiography have PRE/JOB/POST? Is a negative sentence historical or defensive? Has analyst shorthand become actor attribution? Did compression remove a real source limit? Did a ledger become an accidental quota? If deleting filler creates a fragmentary paragraph, merge the remaining source-limit sentence into the paragraph that earns it; do not restore filler to satisfy a numerical target.

## 16. Repo workflow
Treat project-specific ledgers, citation maps, source controls, and archived drafts as provenance. Keep them unless the project explicitly directs otherwise. Prefer coherent batched revision commits to many tiny edits, especially when actions are expensive. Before broadening the cast, adding theory, or searching for more material, test whether the real gap is a missing inferential bridge between facts already present. Default priority: `primary material -> inferential reconstruction -> source ceiling -> historiographical placement -> conceptual payoff -> stylistic polish`.
