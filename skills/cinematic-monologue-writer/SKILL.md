---
name: cinematic-monologue-writer
description: "Use when an approved TopicBrief, Evidence Ledger, and Blueprint must become a faceless-documentary narration draft while preserving claim classifications, payoffs, and the channel's spoken voice."
---

# Cinematic Monologue Writer

Write the master long-form narration. Follow the route and formatting instructions supplied by `documentary-pipeline-controller`; do not reclassify the user's request.

## Required Input

- `RequestSpec`
- `TopicBrief` including all Viral Precision fields
- `Evidence Ledger` including `narrative_assets{}`
- `Blueprint` including `opening_mode`, per-turn discovery records, and `template_risks_cleared[]`
- Target word count

## Writing Contract

- Write in the controller-supplied language, dialect, and market.
- Sound like an intelligent friend sharing a surprising discovery with one person: conversational, clear, curious, and confident only where evidence allows.
- Vary voltage: calm precision for setup; tighter syntax and compression at genuine evidence turns; restraint and space after disturbing or counterintuitive facts.
- Prefer concrete nouns, actions, contrasts, and consequences over abstract assertions.
- Integrate attribution naturally without sounding academic.
- State interpretations boldly as interpretations; do not hedge approved `verified-fact` claims into mush.
- Use `strongest_permitted_factual_wording` for verified facts; use `strongest_permitted_interpretive_wording` for labeled interpretations.
- Use second person when it creates genuine recognition — not as a compulsory device in every paragraph.
- Open on the `opening_mode` specified in the Blueprint — do not substitute a default relatable-action opening.
- Pay every scheduled loop and protect the Claws beat.
- Reveal the actual topic within the Blueprint's ~20-second opening window.
- Carry the `central_motif` through the opening, at least one middle turn, and the circular ending.
- Make the 3–5 evidence turns feel like discoveries rather than a list of studies.
- Prefer concrete anchors from `narrative_assets{}` over invented scene detail.

## Paragraph Utility Check

Every paragraph must perform at least one function:

- **Discover** — delivers new information that changes the viewer's model
- **Deepen** — adds dimension, mechanism, or specific consequence to a previous turn
- **Complicate** — introduces a complication, contradiction, or counterpoint
- **Pay off** — fulfills a scheduled promise or curiosity loop
- **Mirror** — returns the mechanism to the viewer's present life
- **Release** — deliberate breathing room after a high-tension passage

Remove paragraphs that only restate, summarize, or mark time. Include `paragraph_utility_log[]` in the output.

## Opening Rule

The first two sentences must create immediate traction: a scene, tension, anomaly, paradox, consequence, or specific verified fact that earns attention before explanation. Never open with a researcher name, institution name, study title, or "According to..." construction.

## Voltage Modulation

Do not write every paragraph at the same register:

- **Setup and context**: calm, precise, observational
- **Evidence turns**: tighten syntax, reduce hedging where evidence permits, let the fact land at full permitted force
- **After disturbing or surprising facts**: create space — shorter sentences, slower rhythm, let implication breathe
- **Claws beat**: the most precise, concrete sentence in the script; not the most emphatic
- **Circular return**: quieter than the Claws beat; meaning carries the weight, not word choice

Voltage comes from sentence structure, rhythm, and implication — not from certainty, scale, or adjective density.

## Evidence Use

- Assert only `verified-fact` within `strongest_permitted_factual_wording`.
- Use `strongest_permitted_interpretive_wording` when writing labeled interpretation.
- Preserve attribution for `attributed-report`.
- Signal `interpretation` as analysis, not settled fact.
- Signal `hypothesis` with real uncertainty; do not imply it through a loaded question.
- Use a `composite-scene` only when the internal Claim Map labels it and the scene cannot be mistaken for a documented person or event.
- Never use `forbidden`.
- Weave numbers into narration naturally ("one in five," "fewer than a third"). Researcher names and institution names belong in the Evidence Ledger, not the narration.

## Anti-Template Flags

Do not write:

- More than one "you do X, but for most of history…" construction
- "The answer changes everything" or equivalent
- "What makes us human" or "what it means to be human" as a conclusion
- Three or more stacked rhetorical questions at any single point
- "But here is where it gets strange" used more than once
- "Your body remembers" evolutionary claim not directly supported by approved evidence
- Reusable philosophical endings that could apply to an unrelated topic
- Any phrasing copied or closely adapted from benchmark transcripts

Do not ban high-energy phrasing — ban unearned and interchangeable phrasing.

## Concrete Detail

Derive objects, places, actions, and sensory details from the actual `narrative_assets{}` in the ResearchPacket. Do not invent scene detail not present in the research.

Hypothetical examples must be signaled with "imagine," "picture," "suppose," "the next time," or an equally explicit conditional. Never narrate an invented illustration as a witnessed event.

## Required Output: DraftPacket

- `master_narration`
- `claim_map[]`: paragraph or line reference, wording used, claim ID, classification, and which permitted wording tier (factual or interpretive) was used
- `editor_cue_candidates[]`
- `interpretive_passages[]`
- `composite_scenes[]`
- `new_or_changed_claims[]`
- `paragraph_utility_log[]`: one line per paragraph naming its function (discover | deepen | complicate | pay off | mirror | release)

`new_or_changed_claims[]` must be empty. Any entry in `paragraph_utility_log[]` labeled "restate" or "filler" must be resolved before `READY`.

## Quality Gate

- Runtime and word count fit the request.
- All blueprint beats and payoffs are present.
- No claim exceeds `strongest_permitted_factual_wording` or `strongest_permitted_interpretive_wording`.
- Voltage varies across the script; no uniformly flat register throughout.
- The voice is distinctive without repetitive catchphrases.
- The narration sounds like an intelligent friend, not a lecturer, press release, motivational speaker, or theatrical oracle.
- The `central_motif` and circular return are audible without becoming repetitive.
- No "welcome back," "let's dive in," false universals, or fabricated scenes presented as fact.
- Anti-template flags all clear.
- `paragraph_utility_log[]` contains no unresolved "restate" or "filler" entries.
