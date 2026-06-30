---
name: documentary-short-pack
description: "Use when an approved long-form documentary must produce exactly three 30-60 second derivatives: a Trailer, Standalone Short, and Provocation, or when the user explicitly requests those short-form assets."
---

# Documentary Three-Short Pack

Create three distinct Shorts from the approved long-form script. Do not summarize the same passage three times.

## Required Input

- Approved master script
- `TopicBrief` including Viral Precision fields
- `Evidence Ledger`
- `Blueprint`
- Commercial Safety Gate result

## Required Output

Exactly three Shorts: Trailer, Standalone, Provocation. Each uses a different function and a different hook.

### Trailer

- Opens the central tension or question.
- Creates desire for the long-form payoff without revealing it.
- Works as a deliberate trailer, not a chopped introduction.
- Does not fake a stronger mystery than the episode actually delivers.

### Standalone Short

- Delivers one complete insight.
- Makes sense without the long video.
- May point naturally to the documentary after satisfying its own promise.
- Pays one specific insight fully; does not open loops it cannot close in 30–60 seconds.

### Provocation

- Presents a defensible dark, counterintuitive, or dryly sarcastic proposition.
- Encourages disagreement or discussion without false outrage.
- Targets systems and contradictions, never vulnerable people.
- States a defensible interpretation — not an unsupported claim dressed as boldness.

### Per-Short Required Fields

Each of the three Shorts must include:

- `short_type`: trailer | standalone | provocation
- `hook`: the opening line or image
- `spoken_script`
- `promise`: what the viewer is promised within this Short
- `payoff`: how the Short delivers on that promise — must be present in the script
- `source_claim_ids[]`: every factual assertion mapped to an Evidence Ledger claim ID
- `source_inference_ids[]`: every interpretive assertion mapped to an approved Inference Ledger `inference_id`; if an interpretive phrase lacks an approved `inference_id`, it must be removed or reclassified before release
- `evidence_boundary`: what this Short may suggest and must not imply
- `attribution_check`: confirm that attribution essential to truth is preserved despite compression
- `compression_audit`: confirm no interpretation was elevated to fact during shortening, and confirm no inference visibility signal ("the implication is," "what the data suggests") was dropped for a load-bearing interpretive assertion
- `suggested_caption`
- `link_to_long_form`

Default duration: 30–60 seconds. Use the controller-supplied language, dialect, and market localization.

## Evidence Guard

All three inherit the Evidence Ledger. Compression may not remove attribution when it is essential to truth. A new claim, statistic, example, or stronger implication returns to research and evidence review before use.

Abbreviating a qualified claim to its unqualified version is a scope violation, not acceptable compression.

## Quality Gate

- Exactly three outputs: Trailer, Standalone, Provocation.
- Three different functions and hooks; no two use the same opening construction.
- Standalone and Provocation do not depend on the long-form for resolution.
- `source_claim_ids[]` populated for every factual assertion in each Short.
- `source_inference_ids[]` populated for every interpretive assertion in each Short.
- `attribution_check` confirms no essential attribution was lost to compression.
- `compression_audit` confirms no interpretation was elevated to fact and no inference visibility signal was dropped for a load-bearing interpretive assertion.
- No unsupported claim or monetization-risk escalation.
