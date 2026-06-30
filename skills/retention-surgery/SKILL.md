---
name: retention-surgery
description: "Use when a documentary master draft and Blueprint need line-level retention editing: stronger opening, less dead air, cleaner loop timing, better re-hooks, and more breathable pacing without changing evidence."
---

# Retention Surgery

Tighten attention without changing the factual or interpretive contract.

## Required Input

- `DraftPacket` including `paragraph_utility_log[]`
- `Blueprint` including `opening_mode` and `template_risks_cleared[]`
- `Evidence Ledger`
- `TopicBrief` including `misinterpretation_risks[]` and `template_similarity_risks[]`

## Procedure

1. **First-sentence traction audit**: does the first sentence create immediate cognitive or sensory pull before any explanation? A citation, researcher name, statistic attribution, or abstract framing as the first sentence is a hard failure — route to writer with specific instruction.
2. **Click-reason activation**: do the first two sentences activate the locked click reason without overstating it?
3. **Topic clarity**: is the real topic named or unmistakably revealed within the first ~20 seconds?
4. **Information gain audit**: does each paragraph deliver new understanding? Remove paragraphs flagged "restate" or "filler" in `paragraph_utility_log[]`.
5. **Discovery turn verification**: verify each of the 3–5 evidence turns changes the viewer's understanding; merge turns that merely add another example where one already exists.
6. **Loop audit**: verify every loop opens and pays off at the planned time.
7. **Re-hook audit**: re-hooks must occur where viewer understanding genuinely changes — not at fixed intervals. Remove mechanical re-hooks; add or sharpen only where a real evidence turn justifies them.
8. **Rhythm audit**: vary sentence length for spoken rhythm; preserve breathing room after high-tension passages.
9. **Claim integrity**: move information only when claim context and attribution remain intact.
10. **Narrative integrity**: preserve the `opening_mode`, Claws beat, viewer mirror, circular return, and ending function.
11. **Expectation fidelity**: compare title-thumbnail promise, cold open, central question, major turn, and ending. Bait-and-switch is a hard failure.
12. **Anti-template audit**: check against `template_similarity_risks[]` from the TopicBrief and the patterns below.
13. **Promise audit**: return `promise_audit` confirming every material promise element is paid.

## Anti-Template Audit

Flag structural failures and add to `attention_failure_routes[]`. Do not attempt to line-edit a template out of existence.

Flag when the draft contains:

- The same opening construction used in a recent episode on an adjacent topic (check `template_similarity_risks[]`)
- More than one "you do X, but for most of history…" construction
- "The answer changes everything" or equivalent
- Three or more stacked rhetorical questions at any single point
- "What makes us human" as a conclusion
- "Your body remembers" without direct documented evolutionary support
- Identical discovery count or re-hook interval matching a known adjacent episode
- A philosophical ending interchangeable with other topics
- Three-item rhetorical lists in more than two separate beats
- Mechanical "but here is where it gets strange" used more than once

**Structural template failures** — route to `documentary-architect` via `attention_failure_routes[]`.
**Line-level attention issues** — fix here using a sharper approved fact, mechanism, contrast, consequence, or reordering. Do not add unsupported adjectives or false certainty.

## Promise Audit

Return `promise_audit` with:

- `packaging_promise`
- `opening_alignment`
- `payoff_locations[]`
- `underpaid_elements[]`
- `overstated_elements[]`
- `bait_and_switch_risk`
- `resolution_status` — pass or revise

Strengthening retention may not broaden or swap the promise. If the script cannot pay a packaging element from approved evidence, weaken the packaging through the controller rather than manufacture a payoff.

## Evidence Guard

A hook, cliffhanger, omission, juxtaposition, or rhetorical question may not create a new factual implication. Do not make a claim seem more certain, causal, current, universal, or severe than its Evidence Ledger entry.

## Required Output: RevisionPacket

- `revised_text`
- `claim_map`
- `change_log`
- `moved_payoffs[]`
- `promise_audit`
- `added_claims[]`
- `altered_claims[]`
- `removed_claims[]`
- `attention_failure_routes[]` — structural attention failures routed to earliest responsible stage, each with description and routing target

`added_claims[]` and `altered_claims[]` must be empty. Otherwise return them to the controller for Factual Regression.

## Quality Gate

- First sentence creates immediate traction without overstating.
- First two sentences activate the click reason.
- The real topic is clear within the first ~20 seconds.
- Evidence arrives as 3–5 escalating discoveries, not an academic inventory.
- The ending returns to the opening motif with changed meaning.
- No accidental open loops.
- No long inert section.
- No bait-and-switch, underpaid promise, or rhetorical substitute for the expected payoff.
- Anti-template audit cleared or `attention_failure_routes[]` populated with routing targets.
- Net edits improve clarity or forward pull.
- Facts, attribution, uncertainty, angle, and narrator identity remain intact.
