---
name: concrete-grounding-recording-pass
description: "Use when a voice-locked documentary draft needs topic-specific grounding, abstraction control, claim-preserving cleanup, or a cue-free recording version, with the Evidence Ledger supplied by the controller."
---

# Concrete Grounding and Recording Pass

Make the script tangible and recordable without changing its evidence.

## Required Input

- Voice-locked `RevisionPacket`
- `Evidence Ledger` including `narrative_assets{}`
- `Source Ledger`
- Controller-supplied target format

Stop if the Evidence Ledger is missing.

## Grounding Procedure

1. Identify passages with more than four consecutive abstract sentences.
2. Prefer researched objects, actions, settings, routines, documents, sounds, and consequences from `narrative_assets{}` already in the Source Ledger.
3. If an illustrative moment is needed, classify it internally as a `composite-scene`.
4. Keep composite scenes generic enough that they cannot be mistaken for a documented person, quotation, date, or event.
5. For a purely hypothetical example, signal it in the spoken wording with "imagine," "picture," "suppose," "the next time," or another unmistakable conditional construction.
6. A hypothetical example may clarify an approved mechanism but may not introduce an invented fact, named person, quote, statistic, study, date, or event.
7. Use concrete detail where it improves comprehension, recall, or emotional reality — do not turn every passage into a scene.
8. Preserve intentional voltage variations from the approved draft; do not flatten passages written with deliberate tension or deliberate space.

## Grounding Flags

Flag and add to `unsupported_candidates[]` when:

- A sensory detail (sound, smell, texture, temperature, color) is invented and not supported by the Source Ledger
- A scene contains invented specificity: named individuals, quoted dialogue, specific dates, or precise amounts not in the research
- A metaphor obscures the mechanism rather than clarifying it — prefer a concrete researched fact over a vivid comparison that hides how something works
- A hypothetical scene is narrated in indicative mood rather than explicitly signaled as conditional
- Four or more consecutive abstract sentences appear without a concrete anchor from the research

## Evidence Guard

This pass may not add a new factual proposition. It may not change scope, causation, quantity, chronology, attribution, or certainty. Any candidate factual detail not already approved must be returned in `unsupported_candidates[]` for research.

## Recording Cleanup

When the controller requests a clean recording draft:

- remove visual, camera, B-roll, scene, timestamp, chapter, QA, source, and packaging notes
- convert pacing into punctuation and paragraph breaks
- emit spoken narration only
- do not add ElevenLabs tags

For an editor draft, preserve approved editor cues separately from spoken text.

## Required Output: RecordingPacket

- `grounded_master`
- `clean_recording_draft`
- `claim_map`
- `grounding_changes[]`
- `composite_scenes[]`
- `hypothetical_examples[]`
- `unsupported_candidates[]`

`unsupported_candidates[]` must be empty before release.

## Quality Gate

The topic's natural world is specific; the middle does not float; every hypothetical is unmistakably signaled; the voice remains intact; voltage variations from the approved draft are preserved; no passage introduces invented specificity; every factual proposition still maps to the Evidence Ledger.
