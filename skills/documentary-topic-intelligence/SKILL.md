---
name: documentary-topic-intelligence
description: "Use when current documentary research must be turned into one defensible, non-obvious angle, audience tension, viewer promise, scope, and factual boundaries, or when documentary-pipeline-controller invokes the angle stage."
---

# Documentary Topic Intelligence

Turn a `ResearchPacket` into one sharp `TopicBrief`. Do not write narration, perform new research, or classify the user's requested output.

## Required Input

- `RequestSpec`
- `ResearchPacket` including `narrative_assets{}` and `forbidden_narrative_traps[]`
- Optional channel or episode constraints

If current research is missing, stop and return the request to `documentary-current-research`.

## Angle Method

1. Identify the strongest documented mechanism, contradiction, incentive, or consequence.
2. Connect it to a durable human pressure: fear, status, control, money, identity, loneliness, mortality, or belonging.
3. Generate several candidate angles internally.
4. Evaluate each using: proof, surprise, specificity, human stakes, visual potential, payoff strength, retellability, misinterpretation risk.
5. Reject angles that:
   - could fit dozens of unrelated videos
   - depend on a forbidden or unsupported claim
   - merely restate the topic
   - rely on generic "what makes us human" language
   - are dark only through adjectives without a documented mechanism
   - sensationalize beyond the ResearchPacket
   - are correct but obvious — a fact the viewer could guess before clicking
   - are broad but empty — no specific evidence makes them interesting
   - depend on any claim in `forbidden_narrative_traps[]`
6. Lock exactly one angle.

The angle may be interpretive, but it must be clearly separable from documented fact.

## Obviousness Gate

Write a mandatory field named **Why this is not obvious**.

It must identify the hidden mechanism or counterintuitive relationship that makes an informed viewer reconsider the topic. If this field cannot be written honestly from the research, reject the angle and choose another.

## Viral Precision Fields

After locking the angle, define:

- `belief_before`: the intuitive assumption or conventional wisdom the viewer begins with
- `belief_after`: the specific, evidence-supported revision the episode earns — must differ meaningfully from `belief_before`
- `truthful_tension`: the single documented contradiction, paradox, or gap that makes the topic worth an episode
- `viral_thesis`: one repeatable, evidence-compatible idea the viewer can explain to someone else in two sentences
- `human_stakes`: the concrete consequence or decision this mechanism creates in an ordinary viewer's life
- `misinterpretation_risks[]`: the false conclusions a reasonable viewer might draw from the angle or packaging; name at least two
- `template_similarity_risks[]`: opening patterns, phrases, or structures that echo known episodes on this or adjacent topics

## Early Packaging Gate

After locking the angle, create exactly three `packaging_hypotheses`. Each must use a different click route from this list:

| Route | What it does |
|-------|-------------|
| Paradox | Two documented facts that appear to contradict each other |
| Hidden mechanism | A specific process most viewers don't know exists |
| Concrete consequence | A documented outcome that surprises |
| Striking object/image | A specific verified visual from the evidence |
| Bounded question | A specific, answerable question the episode genuinely resolves |
| Documented reversal | A belief the episode overturns with evidence |

Each hypothesis must contain:

- `title_direction` — rough curiosity direction, not final title
- `thumbnail_concept` — one instantly legible visual idea with optional short text
- `click_reason` — the specific unresolved tension earning attention
- `viewer_promise` — the intellectual or emotional reward the episode delivers
- `evidence_boundary` — what the package may suggest and must not imply
- `click_route` — which route type above

Judge each title and thumbnail as one promise unit. Reject generic intrigue, unsupported urgency, and concepts that require the image to make a claim the Evidence Ledger could not support.

Lock one hypothesis as `promise_contract`. Preserve its click reason, expected payoff, and evidence boundary through blueprint, drafting, retention, and final packaging. Final wording may improve later; the underlying promise may not silently change.

## Series Fit

Define `series_fit`: the audience territory, recurring human pressure, and channel expectation this episode reinforces.

Add `adjacent_episode_bridges` with two or three evidence-compatible follow-up or companion topics. These are strategic bridges, not fabricated sequels, and must not narrow the current episode merely to advertise future content.

## Required Output: TopicBrief

- `topic`
- `locked_angle`
- **Why this is not obvious**
- `belief_before`
- `belief_after`
- `truthful_tension`
- `viral_thesis`
- `human_pressure`
- `human_stakes`
- `audience_tension`
- `viewer_promise`
- `stakes_and_why_now`
- `scope_in`
- `scope_out`
- `factual_boundaries`
- `do_not_claim`
- `counterargument_to_address`
- `misinterpretation_risks[]` — at least two
- `template_similarity_risks[]`
- `packaging_hypotheses` — exactly three, each using a different click route
- `promise_contract` — the one locked hypothesis with click reason, expected payoff, and evidence boundary
- `series_fit`
- `adjacent_episode_bridges` — two or three
- `working_title_seeds` — five rough directions, not final packaging
- `source_ids_used`

## Quality Gate

- Exactly one angle.
- Exactly three packaging hypotheses each using a different click route.
- `belief_before` and `belief_after` differ meaningfully.
- `viral_thesis` is retellable in two sentences.
- `misinterpretation_risks[]` names at least two specific false conclusions.
- `template_similarity_risks[]` is populated.
- The angle is supported by the ResearchPacket and uses no claim from `forbidden_narrative_traps[]`.
- Fact and interpretation are distinguishable.
- The viewer promise can be paid off in the requested runtime.
- The promise contract is specific enough to audit.
- The angle is dark or unsettling because of the mechanism, not fabricated panic.
- No new statistic, date, quotation, named event, or causal claim is introduced.

## Failure Response

Return a concise `ANGLE_BLOCKED` result stating whether the problem is weak evidence, an obvious framing, incompatible scope, or a missing user constraint.
