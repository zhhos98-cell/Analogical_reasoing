# AGENTS.md — Unified Research, Writing, and Editing Protocol

Updated: 2026-10-12

This is the cross-repository writing protocol. It governs research prose, historical reconstruction, summaries, notes, reports, article drafts, assignment prose, and other text-bearing scholarly outputs. For code, data, configuration, tests, tables, or slide mechanics, preserve the source/attribution rules without forcing prose architecture onto technical structures.

Current explicit user instructions outrank this file. Repository-specific rules elsewhere remain binding when they concern named canonical files, source objects, fixed project structure, permissions, frozen areas, archive masters, repository workflow, or project-specific factual/argument constraints. This file supersedes older generic prose, style, compression, benchmark, and editing heuristics wherever they conflict.

## 1. Protected baseline / 底本

- When the user designates a prose, transcription, control, assignment, presentation text, or other text-bearing state as a **baseline / 底本**, record the exact canonical file and commit/version before the next substantive pass.
- From that point, deletion is user-consent-gated. Without explicit current-session authorization to remove an identifiable sentence, paragraph, passage, section, source item, quotation, qualification, transcription unit, or other protected part, do not delete, silently omit, demote away, or replace it away for concision, elegance, flow, architecture, benchmark matching, cleanup, or compression.
- The baseline protects content and evidentiary pins, not wording. Rewriting, merging/splitting sentences, subordinate syntax, paragraph boundaries, transitions, and local regrouping are allowed only while facts, source ownership, quotations, qualifications, chronology, provenance, counterevidence, and inferential hinges remain recoverable.
- Work from the latest descendant of the protected baseline. Older drafts, controls, summaries, benchmark notes, OCR layers, and model memory are diagnostic only unless the user explicitly restores one.
- After a substantial pass, compare with the immediately previous state and, where deletion risk exists, with the protected baseline. Restore any protected item lost without authorization.
- Generic deletion/compression tests never override a protected baseline or a repository-specific preservation lock.

## 2. Canonical state and editing method

- Work in the canonical live draft when one exists. Do not create parallel rewrites, restart files, substitute drafts, or independent companions unless the user asks.
- Prefer **surgical patching over regeneration**. Preserve surrounding text unless the requested change genuinely requires local restructuring.
- Treat user annotations as local instructions; do not use one annotation as permission to regenerate unrelated prose.
- A bilingual/read-along companion mirrors the canonical text and should be synchronized only after the canonical passage is stable.
- Before any repository write, use the current file/blob state; sequential writes to the same path must use the latest state.
- After a whole-file replacement, inspect the diff for unrelated changes to titles, quotations, citations, links, notes, punctuation, status lines, typography, metadata, or protected text and undo accidental transport changes.

## 3. First-order factual layer

- Keep prose recoverable to controlled actors, actions, institutions, instruments, specimens, texts, documents, objects, dates, places, or source wording. Interpretation may compress facts after they appear; it must not replace them.
- Let the material happen before naming it. Establish the action, comparison, classification, sequence, manipulation, or source problem before introducing an abstract noun that summarizes it.
- Prefer source/actor vocabulary and concrete verbs. Use nouns to carry already-established fact packages; use verbs to carry historical action and argument.
- Interrogate abstract or general words with: **who? what exactly was said or done? which text/object/institution? when? where? from whom or where did it come? which historiography? what original wording?** Use the concrete answer when source-locked and analytically equivalent.
- Do not force false precision. Keep a bounded general formulation when the evidence is uncertain, specificity would imply a stronger relation, or extra detail does not change the live argument.
- After substantive drafting, run a first-order/every-word audit: replace unsupported abstractions with source language or concrete facts where possible, then confirm no actor, sequence, provenance, evidentiary ceiling, or inferential hinge disappeared.

## 4. Source hierarchy, ownership, and evidentiary ceiling

- Factual expansion is source-locked. Dates, places, people, actions, quotations, bibliographic claims, causal links, and correspondence sequences must come from controlled repository material or newly verified research recorded in the repository.
- Never fill a historical gap from model memory, general knowledge, plausibility, stylistic completion, or a likely reconstruction.
- Keep evidence layers distinct: first-order witness/action/wording; actor inference; source-near reconstruction; local limit/counterevidence; historiography; conceptual payoff. A later layer cannot substitute for a missing earlier layer.
- Track claim force: explicit, implied, reconstructed, possible but unproven, or absent. Preserve modal force such as `may`, `seems`, `probable`, `more probable`, and `could`.
- Do not convert probability into demonstration, compatibility into proof, sequence into causation, correlation into mechanism, a proposed experiment into a completed one, contemporaneity into connection, or proximity into borrowing/influence/intention/consensus/novelty.
- Absence from one catalogue, inventory, OCR layer, index, or witness does not by itself invalidate independently controlled evidence. Record the discrepancy and the support ceiling.
- When sources conflict, preserve the conflict and state what each source can support; do not normalize anomalies silently.
- Keep source ownership explicit. In notebooks, lecture notes, marginalia, compilations, and working files, distinguish source/lecturer propositions, copied examples or bibliography, and the writer's own questions/reclassifications. Handwriting, possession, or copying alone does not establish proposition authorship.
- Do not collapse distinct witnesses, source layers, variants, or reconstructions merely for fluency.
- External research should answer a concrete sentence-level/source-level gap. Once a corpus is calibrated, do not reopen generic discovery merely to broaden the cast.

## 5. Structural benchmark: strict sentence-by-sentence method

- When the user designates an external text as a structural benchmark, use the actual controlled full text, not memory, a summary, or an old alignment.
- Proceed in order: **one benchmark sentence → one project sentence-function decision**. Settle the live sentence before advancing.
- Identify the benchmark sentence's operation and load: fact, background, qualification, contrast, cause, source limit, retrospective qualification, transition, restatement, inference, or another auditable move.
- Move **function, load, and progression**, not substantive content or wording. Preserve the project's evidence order, chronology, actors, objects, and source ownership; do not pull later project material forward simply to fill an earlier benchmark slot.
- Strict correspondence does not mean copying surface syntax, sentence length, diction, or paragraph shape. Reproduce an equivalent move only when the project's evidence requires and supports it.
- Paragraph boundaries follow event/inferential completion. A short or long benchmark paragraph is only a cue when the project's own historical action performs the corresponding work.
- Match sentence load rather than length: if a benchmark sentence carries fact plus concession, cause, source limit, or retrospective qualification, test whether the project's already-existing qualification belongs in that same sentence.
- Benchmark matching never authorizes deletion of protected baseline material or fabrication of extra scholars, sources, objections, or archive material for symmetry.

## 6. Sentence operations and syntactic packing

- A body sentence should perform at least one auditable function: establish fact/event; show what a source does; state actor inference; supply a necessary reconstructed premise; preserve a limit/counterexample; advance an inference; alter a historiographical reading; or create the next question.
- Normally give a sentence one principal operation. Synthesis may combine already-established states, and several short facts/fragments may share a sentence when they jointly perform the same historical or argumentative work.
- If sentence B is really a modifier, premise, qualification, example, attribution, or brief flashback for sentence A, test merging it into A. Split when compression obscures a distinct actor, action, chronology, source owner, or independently auditable claim.
- When A, B, and C perform the same historical work, interleave them rather than narrating each as a miniature beginning-middle-end. Preserve separate narration when chronology or difference itself carries the argument.
- Vary syntax with the historical action: apposition, subordination, parataxis, relative clauses, embedded quotations, brief returns, and sentence-length variation are tools, not goals.
- Remove functional duplication before cutting first-order evidence. Ask what exact factual or inferential step breaks if a sentence or clause disappears.
- Avoid mechanical `fact → verdict → fact → verdict`. Two to four adjacent pieces of evidence doing the same work may accumulate before one interpretation.

## 7. Quotations, formalization, and citation placement

- Quote when wording itself carries evidence: modal force, technical term, lexical ambiguity, consequential phrase, relation, qualification, refusal, instruction, or a speech act.
- Cut quotation by evidentiary unit: **word/phrase** for a label or concept; **relation/clause** for contrast, causation, sequence, modality, or logical relation; **speech-act/sentence** when the utterance or intact syntax is the historical action.
- Do not make quotation perform the article's interpretation. The quotation establishes lexical/relational/speech-act evidence; attribution, consequence, and inference belong in the author's syntax.
- Preserve full wording when completeness carries evidence. Ellipsis, clipping, paraphrase, or nominal compression must never remove a qualifier, negation, modality, referent, or contextual condition that changes force.
- Formal symbols, ledgers, operation labels, and source-level taxonomies are checking devices, not public theory sections; return public prose to bodies, words, actors, texts, and actions.
- Cite at the smallest sentence that completes the source-dependent proposition. Avoid paragraph-end omnibus notes; when a synthesis combines sources, cite the relevant bundle.
- Never invent pages, sections, shelfmarks, archival references, or exact quotations. Keep unresolved locators explicitly unresolved until controlled.

## 8. Historical reconstruction, chronology, and relation control

- Prefer completed event chains where the material supports them: **date/place/action → document/request → reply/response → consequence**.
- Restore antecedents, consequences, and time anchors only when they materially change the reader's grasp of sequence, duration, density, or inference.
- Keep actors visible. The event must finish happening; it does not have to be explained to exhaustion.
- Mundane direct traces—sending, reading, lending, correcting, speaking, carrying a letter, using a book, handling an object—may be argument-bearing and should not be removed merely because they are small.
- Keep relations distinct when evidence distinguishes them: temporal sequence, logical/classificatory relation, semantic equivalence, causal function, transmission/genealogy, source ownership, practical/institutional mediation, and cross-context identity.
- Shared vocabulary does not establish shared definition, evidence, method, authority, borrowing, or genealogy.
- An organizing thread is not automatically a causal mechanism. Later reuse is not automatically transmission; recurrence is not automatically influence.
- Avoid clean conversion stories and teleologies. Persistence with changed use, unresolved coexistence, or a narrowed relation may fit the surviving evidence better.

## 9. Conceptual history and historiography

- Keep one conceptual center at a time. Supporting concepts should clarify the live problem rather than become parallel themes.
- Do not establish conceptual history by word frequency alone. Ask what a term allowed an actor to classify, infer, compare, authorize, reject, or withhold in a particular setting.
- Correspondence is evidence, not a default narrative engine or endpoint. Keep a letter in the body when its message performs the historical action; when useful, open it to the books, lectures, notes, manuscripts, objects, and institutional records that give its language work.
- Every secondary source in the body must do a precise job: inherit, correct, refute, converge, narrow, redirect, provide an alternative reconstruction, control a term, show an afterlife, or expose a gap.
- Historiography belongs at a hinge where it changes the reading of a live event/claim. State the case before it, the exact job it performs, and the new distinction/question it makes possible; if it only says “this supports our interpretation,” demote or remove it.
- Do not let secondary literature substitute for primary reconstruction when primary material exists, and do not rehearse a scholar's whole argument when one proposition performs the needed work.
- A near-contemporary parallel is not influence without transmission evidence. Current scholarship may establish afterlife or technical relevance without proving an intellectual genealogy.
- Outside scholars should feel sparse but functional: one strong comparison that changes pressure on the claim is better than a name cluster.

## 10. Paragraph architecture and density

- A paragraph should normally let one historical or inferential action finish and make one compressible argumentative advance.
- If the paragraph's advance cannot be stated in one sentence without an A/B/C list or several independent claims, split, redistribute, compress, or move material rather than making the topic sentence heavier.
- The opening should govern the paragraph's work without becoming an abstract thesis wrapper. Historical action may lead, but the reader should know what problem or relation the paragraph is advancing.
- Read only paragraph openings, then separately the one-sentence argumentative summaries. Both sequences should form a cumulative chain in which each paragraph advances, complicates, limits, pressures, or converts the unresolved problem from the previous one.
- The next paragraph should arise as continuation, complication, consequence, contrast, or counterpressure—not merely because chronology or a transition word says “next.”
- Prevent module hardening. Do not discharge historiography, background, method, institutions, counterevidence, and source practice as separate memo-like packets when they belong inside a live event or claim.
- Avoid ABCD inventories, repeated triads, parallel noun strings, symmetrical X/Y/Z summaries, conjunction piles, and semicolon chains used to force heterogeneous material into apparent coherence.
- Density is relational, not additive. Combine facts, relations, quotations, and textual moves that change the same problem; do not add names/examples simply to raise density.
- Numeric density tests are diagnostic only: roughly 5–10 sentence operations or 6–9 interrelated information points may indicate a developed historical paragraph, and roughly 60–85% first-order facts/wording can be useful in reconstruction. Never pad, cut, or fragment prose to meet a quota.
- One- or two-sentence paragraphs are exceptional when adjacent sentences perform the same action; equally, do not merge distinct events merely to make a paragraph longer.
- Counterevidence belongs where it presses on a live claim and changes the next step, not in a decorative “balance” paragraph. A real counterexample should narrow, redirect, or reshape the claim.
- Parallel strands need a hinge before the conclusion: locate the historical or conceptual point where one begins to change the reading of the other.

## 11. Reader orientation and public language

- Do not make the reader supply an argument-bearing factual premise. At first meaningful appearances of people, texts, institutions, disputes, dates, technical terms, acronyms, or retrospective labels, add the minimum source-controlled identification needed.
- Read as an intelligent historian outside the immediate subfield. Repair specialist-background gaps at the smallest locus; do not expand them into encyclopedia biography or standalone background sections.
- Prefer continuous historical argument over modular note-like prose, roadmap sentences, repeated thesis restatements, and meta-commentary about method.
- Keep architecture backstage. Translate workbench terms such as `control`, `carrier`, `scale`, `reaggregation`, `proof burden`, or repo-invented labels into the actual source relation or historical action unless established scholarship or actor language genuinely requires the term.
- Keep defensive temperature low. Replace reviewer-management formulas (`not X but Y`, `this does not mean`, `does not prove`, `rather`) with positive source-state descriptions where possible, while preserving genuine uncertainty, contradiction, negative evidence, and source limits.
- Avoid mental-state claims such as `judgment`, `confusion`, `failure to understand`, intention, or belief unless the sources warrant them.
- Do not tell the reader a point is important, central, key, striking, complex, material, entangled, or contextual when the object-level relation can show what matters.
- Proper names must do work. Keep name-density under control and identify people when the reader needs the identity to follow the inference.
- First person is allowed when it clarifies an argumentative decision, source limit, or route.
- After dense stretches, source-grounded descriptive breathing may show a person reading, writing, travelling, meeting, teaching, corresponding, handling an object, or encountering an institutional constraint; it must not invent atmosphere or open a new research branch.

## 12. Repetition, callbacks, openings, and conclusions

- A fact may recur only when its inferential role changes. Exact wording should recur only when it carries new work.
- When the article has a concrete historical object and a methodological/historiographical problem, keep both visible at low frequency through source-bearing callbacks rather than slogans.
- Seed a strand only to the evidentiary level available at that point; never write a later formulation backward into an earlier archive.
- The opening two or three paragraphs should normally give the reader an event/object/scene, the problem it generates, and the stakes; literature review or bibliographic metadata should not precede the historical action unless they are themselves the scene.
- A section or paragraph ending should compare, limit, complicate, or hand off to the next unresolved problem rather than inventory completed operations or introduce an unrelated new task.
- The conclusion must synthesize only what the body earned. Do not introduce new archive material, secondary literature, comparison, or larger theory merely to broaden the ending.
- Return the conclusion to the concrete object, actor, practice, or textual problem; state a bounded contribution and the remaining evidentiary limit rather than a universal claim.

## 13. Compression and recovery

- Compression is not deletion-first. Prefer: merge repeated qualifications; interleave evidence doing the same work; put comparable names/cases into rapid form; move provenance or non-argumentative background to notes; then remove material that adds no event, inference, historiographical change, or necessary source limit.
- Repeated explanation is expendable; argument-bearing friction is not. Keep a short hinge when it makes a non-obvious relation explicit or enables the next paragraph, even if the evidence partly implies it.
- Secure or interesting evidence is not automatically entitled to body space. Outside a protected baseline, keep it in the body only when it changes the event, inference, governing claim, or necessary source limit; otherwise move it to a note/control or omit it.
- After substantial shortening, compare with the prior controlled state and classify losses as repetition/background, nonessential detail, or accidental removal of an argument-bearing pin. Restore accidental pins in the shortest source-controlled form.
- If compression cuts too deeply, restore evidence, historical consequence, source language, or a needed inferential hinge—not old scaffolding, roadmaps, generic theory, repeated closure, or workbench vocabulary.
- Notes are part of compression: retain exact locators and evidence ceilings, compress repeated provenance, remove orphan notes, and do not let notes re-explain an inference already made in the body.
- Under a protected baseline, all of the above operates by **repacking** protected material unless the user explicitly authorizes deletion.

## 14. Notes and source limits

- Use notes for concise background, chronology, translation choices, provenance, archive locators, source uncertainty, and controlled side-material.
- Do not bury the article's central argumentative step in a note.
- Preserve source language when wording matters; translate only to the degree justified by source control.
- Unpublished or partially controlled material can remain useful when its evidentiary level is stated precisely.
- Submission notes should support claims still alive in the body. Abandoned comparators, unused page ranges, and superseded research inventory belong in research controls rather than public notes.

## 15. QA before writing back

- Check source control, claim force, attribution/ownership, chronology, actor clarity, and preservation of genuine counterevidence.
- Check that each abstraction is earned by visible first-order material and that each quotation is at the correct evidentiary granularity.
- Check each paragraph's one-sentence advance; then run the first-sentence-only and paragraph-boundary chain tests.
- Check for module hardening, accidental parallel theses, defensive scaffolding, invented jargon, unsupported causation/transmission, name accumulation, and filler growth.
- Check that compression did not remove protected baseline material, a real source limit, provenance, variant status, or an inferential hinge.
- Check public prose for leaked workflow/control vocabulary and replace it with actual historical/textual relations.
- If a benchmark is active, verify sentence-by-sentence function/load correspondence without imported content or surface imitation.
- After editing in a repository, report the exact path and resulting commit SHA and describe the substantive effect of the diff.

Compact rule: **facts and source ownership first; protect the designated 底本; let sentences perform auditable work; make paragraphs carry completed historical/inferential actions; use historiography at hinges; compress by packing rather than abstraction; preserve uncertainty and counterevidence; and never let style outrun the evidence.**