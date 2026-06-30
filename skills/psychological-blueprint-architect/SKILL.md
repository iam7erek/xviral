---
name: psychological-blueprint-architect
description: "Use when an approved TopicBrief and Evidence Ledger must become an 8-12 minute emotional arc, beat map, curiosity-loop plan, re-hook schedule, payoff map, and non-obvious Claws beat."
---

# Psychological Blueprint Architect

Design the viewer's emotional and informational journey. Do not write final narration or introduce claims not present in the Evidence Ledger.

## Required Input

- `TopicBrief` including all Viral Precision fields (`belief_before`, `belief_after`, `truthful_tension`, `viral_thesis`, `misinterpretation_risks[]`, `template_similarity_risks[]`)
- `Evidence Ledger` including `narrative_assets{}`
- Target duration and platform

## Procedure

1. Read the locked `promise_contract`; convert its viewer promise into a question the video can answer.
2. Select the evidence-fitting opening mode from the selector below — do not default to relatable present-day action.
3. Record `opening_mode_rationale`: why this entry fits this topic better than the alternatives.
4. Select one primary story architecture.
5. Build Required Narrative Functions in the order evidence best supports.
6. Open one long loop and two or more short loops; assign every loop a payoff.
7. Build per-turn discovery records for all 3–5 evidence turns.
8. Verify each beat has at least one utility function.
9. Map the promise contract to explicit evidence-backed payoffs.
10. Schedule re-hooks where viewer understanding genuinely changes — not at fixed intervals.
11. Create a mandatory **Claws beat** near the turn.
12. Run anti-template checks before finalizing.

## Required Narrative Functions

These functions must appear in every episode. Their order and form follow the evidence, not a fixed template.

1. **Entry** — open with immediate cognitive or sensory traction; the viewer must be pulled before they understand why
2. **Topic Revelation** — name or unmistakably reveal the real topic within roughly the first 20 seconds
3. **Central Question** — state or strongly imply one question the episode will answer
4. **Discovery Chain** — 3–5 turns, each revising, complicating, or deepening what the previous turn appeared to establish
5. **Viewer Mirror** — return the mechanism to a decision, habit, fear, or ordinary consequence in the viewer's present life
6. **Claws Beat** — the most repeatable non-obvious reframe; reveals a documented mechanism, not a poetic restatement
7. **Payoff** — answer or honestly transform the central question using the approved evidence
8. **Circular Return** — close by returning to the opening image, action, or object with an earned change in meaning

The `central_motif` must appear in the Entry, support at least one middle turn, and carry the Circular Return.

## Opening Mode Selector

Choose the opening mode that best fits the evidence and `belief_before`. Do not default to a relatable present-day action — select by evidence fit.

| Mode | When to use |
|------|-------------|
| Familiar present-day action or object | When the viewer's own behavior directly embodies the mechanism |
| Concrete verified anomaly | When the most striking evidence is a specific documented fact that contradicts expectation |
| Consequence-first | When the endpoint is more surprising than the origin story |
| Restrained historical image | When a specific documented moment is the clearest entry into the mechanism |
| Paradox | When two documented facts appear to contradict each other and the resolution is the thesis |
| Clearly signaled hypothetical | When a brief, unmistakably conditional scenario grounds an abstract mechanism — must be labeled |
| Verified number | Only when the number is immediately understandable, genuinely load-bearing, and cannot be mistaken for unsupported precision |

Topic clarity must still arrive within roughly 20 seconds regardless of which mode is chosen.

## Story Architecture Selector

Choose `selected_architecture` from:

- **Investigation / Revelation** — for hidden systems, incentives, contradictions, mysteries, and philosophical questions
- **Paradox / Argument** — when competing explanations or values must be tested
- **Rise / Collapse** — when evidence documents meaningful accumulation, peak, reversal, and consequence over time
- **Process / Countdown** — when ordered stages, escalating thresholds, or a bounded sequence create the clearest explanation
- **Transformation** — only when the Evidence Ledger contains a real protagonist with documented decisions and change

Record `architecture_rationale`. Combine at most two architectures when no single one fits clearly; state which one controls the episode.

Never invent a crisis, mentor, villain, ordeal, victory, or transformation to satisfy a template. Never convert institutions or abstract forces into human characters unless the framing remains clearly interpretive and evidence-compatible.

## Per-Turn Discovery Record

For each of the 3–5 discovery turns, record:

- `prior_belief`: what the viewer believes entering this turn
- `new_evidence`: the specific claim IDs delivered in this turn
- `belief_revision`: how the viewer's model changes after this turn
- `emotional_effect`: curiosity | surprise | unease | recognition | consequence
- `concrete_anchor`: the specific researched object, action, or setting from `narrative_assets{}` that grounds this turn
- `loop_action`: opens | pays | complicates an existing curiosity loop

Turns that merely add another example without revising the viewer's model must be merged or cut.

## Beat Utility Rule

Each beat in the beat map must perform at least one function:

- opens a real question
- supplies evidence that changes the viewer's model
- revises the viewer's prior belief
- complicates an apparent answer
- raises concrete consequence
- pays a scheduled promise
- provides purposeful breathing room (deliberate decompression, not dead air)

Remove beats that merely restate without advancing understanding.

## Anti-Template Checks

Before finalizing, verify the blueprint does not contain:

- More than one of the opening turns using a "you do X, but for most of history…" construction
- "The answer changes everything" or equivalent
- Three or more stacked rhetorical questions at any single point
- "What makes us human" as a conclusion
- "Your body remembers" evolutionary claim without direct documented support
- An opening mode identical to what a known adjacent episode used
- A philosophical ending interchangeable with an unrelated topic
- Three-item rhetorical lists in more than two separate beats
- Mechanical "but here is where it gets strange" transition used more than once

Cross-reference `template_similarity_risks[]` from the TopicBrief. Record `template_risks_cleared[]` confirming each check passed.

## Promise-Payoff Contract

Create `promise_payoff_map` with:

- `promise_element`
- `expected_payoff`
- `target_beat`
- `claim_ids`
- `payoff_type` — answer | mechanism | reframe | consequence | emotional resolution

Every element that materially contributes to the click reason must receive a payoff. Delayed context is allowed; bait-and-switch is not. Do not pay the promise with mood, rhetoric, or a broader adjacent insight when the packaging implies a specific answer.

## Claws Beat

The Claws beat is the most repeatable non-obvious reframe in the episode. It must reveal a documented mechanism, incentive, contradiction, or consequence — not merely restate the thesis more poetically.

## Required Output: Blueprint

- `selected_architecture`
- `architecture_rationale`
- `opening_mode`
- `opening_mode_rationale`
- `emotional_arc`
- `central_question`
- `central_motif`
- `topic_reveal_target`
- `discovery_turns[]` — full per-turn discovery records
- `thesis_coherence_map[]` — for each discovery turn, an explicit declaration that it is a **consequence** of the opening thesis linked via a stated mechanism; any turn that introduces a new independent causal claim with no stated mechanical link to the opening angle is flagged `thesis_replacement_risk` and must be restructured or removed before READY
- `viewer_mirror`
- `circular_return`
- `promise_payoff_map[]`
- `curiosity_loops[]` with open and payoff timestamps
- `beat_map[]` with timestamp, function, beat utility, claim IDs, tension, and visual opportunity
- **Claws beat** with target timestamp and supporting claim IDs
- `re_hook_points[]` — at genuine understanding changes, not fixed intervals
- `payoff_schedule[]`
- `ending_function`
- `claims_not_to_imply[]`
- `template_risks_cleared[]`

## Quality Gate

- Opening mode selected for this topic's evidence, not channel habit.
- `opening_mode_rationale` explains why this entry fits better than alternatives.
- Topic clarity within roughly 20 seconds regardless of opening mode.
- All 3–5 discovery turns have full per-turn records; no turn merely adds an example.
- `thesis_coherence_map[]` is present for all discovery turns; no turn is flagged `thesis_replacement_risk`.
- Every beat has at least one utility function.
- `template_risks_cleared[]` confirms all anti-template checks passed.
- Selected architecture follows the evidence rather than a universal beat sheet.
- The promise is paid off at the specificity implied by the title-thumbnail hypothesis.
- Every `promise_payoff_map` entry has an expected payoff, target beat, and supporting claim IDs.
- Every factual beat references approved claim IDs.
- The Claws beat is specific, evidence-compatible, and non-obvious.
- Re-hooks occur where understanding changes, not at fixed intervals.
- The structure fits the requested runtime.
