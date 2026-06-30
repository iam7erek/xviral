---
name: platform-packaging
description: "Use when an approved documentary script needs YouTube upload assets: titles, thumbnail concepts and text, description, chapters, tags, pinned comment, or opening on-screen text."
---

# Platform Packaging

Package an approved script without editing the narration or inventing a stronger promise.

## Required Input

- `TopicBrief` including Viral Precision fields and `promise_contract`
- Approved master script
- `Evidence Ledger`
- `Blueprint`
- Commercial Safety Gate result

## Click Route Types

Generate titles and thumbnails from genuinely different click routes. Do not produce variations of the same hook type.

| Route | What it does |
|-------|-------------|
| Paradox | Presents two documented facts that appear to contradict each other |
| Hidden mechanism | Names a specific process most viewers don't know exists |
| Concrete consequence | Leads with a documented outcome that surprises |
| Striking object/image | Centers a specific verified visual or object from the evidence |
| Bounded question | Asks a specific, answerable question the episode genuinely resolves |
| Documented reversal | Names a belief the episode overturns with evidence |

Clickability must come from unresolved documented truth, not from missing context that reverses the premise.

## Required Output

### Titles (10)

Mostly under 60 characters. For the leading three options, include per-option metadata:

- `title_text`
- `click_route` — which route type from above
- `click_reason` — the specific unresolved tension driving the click
- `expected_payoff` — what the viewer expects to learn
- `supporting_claim_ids[]` — the claim IDs this title draws on for any factual phrase
- `supporting_inference_ids[]` — the inference IDs from the Inference Ledger this title draws on for any interpretive phrase; if any interpretive phrase lacks an approved `inference_id`, the title is invalid
- `evidence_boundary` — what this title may suggest and must not imply
- `likely_misreading` — the false conclusion a viewer might draw
- `opening_alignment` — which first sentence in the script best fulfills this title's promise

For the remaining seven titles, include `title_text`, `click_route`, and `evidence_boundary` at minimum.

### Thumbnail Concepts (3)

Each entry includes:

- `visual_concept` — one specific, instantly legible image
- `overlay_text` — 2–4 words maximum
- `emotional_read` — the immediate viewer response this image creates
- `click_route`
- `supporting_claim_ids[]`
- `evidence_boundary`

Judge each title and thumbnail as one promise unit. The combination must create one expectation, not competing promises.

### Supporting Assets

- Description: two-line hook, concise summary, and chapters
- Chapters: derived from the Blueprint without spoiling the main payoff
- Tags: 10–20 relevant search terms
- Pinned-comment question: one question that invites genuine viewer response
- Opening on-screen phrase: 3–6 words

## Rules

- Match the locked angle and actual payoff.
- All titles, thumbnails, descriptions, and chapter labels remain evidence-gated.
- Each of the 10 titles uses a different click route or a meaningfully different entry into the same route — do not generate near-identical variations.
- Do not use fake numbers, false urgency, dehumanization, graphic imagery, or promises absent from the script.
- Avoid generic split-face AI art and interchangeable "THIS CHANGES EVERYTHING" packaging.
- Reflect a `yellow` or `red` safety result with a safer alternative.

## Quality Gate

The package is clickable because the mechanism is interesting, not because the claim was inflated. Every factual phrase in titles and thumbnail text maps to an approved `claim_id`. Every interpretive phrase in titles and thumbnail text maps to an approved `inference_id` from the Inference Ledger. At least three of the ten titles use different click routes. The leading title-thumbnail pair's `opening_alignment` is present in the script's actual first sentence.
