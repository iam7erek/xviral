---
name: noir-voice-anti-generic-style
description: "Use when a fact-locked documentary draft needs the channel voice: calm, intelligent, concrete, dark through understatement, and occasionally dryly sarcastic without generic AI prose or factual drift."
---

# Noir Voice and Anti-Generic Style

Apply the channel voice without turning every episode into the same monologue.

## Required Input

- `RevisionPacket`
- `TopicBrief`
- `Evidence Ledger`

## Voice Contract

- Calm, low-key, precise, and observant as a baseline.
- Sound like an intelligent friend who has just found something worth showing the viewer, not a lecturer displaying research.
- Philosophical only after concrete evidence is established.
- Dark through implication and restraint, not melodrama.
- Dry sarcasm may target institutions, incentives, status rituals, and absurd contradictions.
- Never mock victims, vulnerable people, protected groups, grief, disability, or poverty.
- Choose the grammatical perspective that fits the subject; second person is optional.

## Voltage Modulation

The baseline is calm — but not uniformly flat. Controlled voltage is part of the voice, not a violation of it.

- **Setup and context**: calm, precise, observational — let the facts accumulate weight quietly
- **At a genuine evidence turn**: tighten syntax, let the fact land without additional adjectives or amplification
- **After a disturbing or counterintuitive fact**: create deliberate space — shorter sentences, slower rhythm, let implication do the work
- **Claws beat**: the most precise, concrete line in the episode; not the most emphatic or dramatic
- **Circular return**: quieter than the Claws beat; meaning carries the weight, not word choice

Do not sand every line to the same low-energy register. Variance in rhythm and compression is voice, not inconsistency. A flat monotone reads as generic AI prose.

## Signature Lines

A small number of episode-specific signature lines are permitted. A valid signature line is:

- concrete and tied to this episode's specific mechanism or evidence
- claim-safe and within approved wording
- not reusable on an unrelated topic
- derived from the episode's own evidence, not channel convention or past scripts

Do not recycle signature constructions across episodes. A recurring channel catchphrase is a template failure.

## Remove

- Corporate and generic AI prose
- Empty three-item lists
- Stacked rhetorical questions
- Stock "human condition," "fast-paced world," "what makes us human," and "everything changed" language
- Purple metaphors that hide the mechanism
- Repeated channel catchphrases and interchangeable openings
- Lecture transitions such as "research shows," "it is important to note," and consecutive source summaries when the same evidence can be narrated as discovery
- Researcher names, institution names, and study titles spoken aloud in the narration; use the finding, not the byline
- Any opening that begins with a citation, statistic attribution, or academic framing

## Protect

- Claim wording, attribution, uncertainty, and Claim Map references
- The locked angle, Claws beat, loop payoffs, and ending function
- The `central_motif`, selected opening mode, discovery chain, viewer mirror, and circular ending
- Topic-specific terminology and concrete detail
- Intentional voltage variations — do not flatten passages written with deliberate tension or deliberate space

## Required Output: RevisionPacket

- `revised_text`
- `claim_map`
- `style_change_log`
- `added_claims[]`
- `altered_claims[]`

No new claim or restructured factual implication is allowed. If either array is non-empty, return it for Factual Regression.

## Quality Gate

Read for cadence. Sentence lengths vary naturally; voltage shifts at genuine evidence moments; the voice remains restrained as a baseline while allowing controlled intensity at real turns; sarcasm is ethical; no phrase sounds reusable across unrelated topics. The listener should feel personally addressed by a smart equal, never instructed from a podium.
