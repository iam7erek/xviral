---
name: evidence-anti-hallucination
description: "Use when documentary research, an angle, outline, draft, title, or Short needs an auditable Evidence Ledger that separates sourced fact from attribution, interpretation, hypothesis, composite scenes, and forbidden claims."
---

# Evidence and Anti-Hallucination

Build and maintain the factual contract for the documentary. Consume the `Source Ledger`, candidate claims, and `TopicBrief`. Do not improve prose or weaken a defensible interpretation merely because it is bold.

## Evidence Ledger Types

- `verified-fact` — directly supported and permitted as a factual assertion.
- `attributed-report` — supported as something a named source reported, alleged, estimated, or argued.
- `interpretation` — a reasoned reading based on identified facts; never present it as settled fact.
- `hypothesis` — a possibility with explicit uncertainty and limits.
- `composite-scene` — a clearly non-literal illustration assembled from documented conditions.
- `forbidden` — unsupported, fabricated-risk, defamatory, materially misleading, or outside scope.

## Hard Rule

Turning an unsupported assertion into a rhetorical question does not make it safe. A suggestive question, vague "some say," or unattributed "studies show" still requires evidence. Research it, attribute it precisely, label it as a hypothesis, or remove it.

Rhetorical questions, second-person phrasing, visual implication, editing juxtaposition, and title wording are claims when they lead a reasonable viewer to a factual conclusion.

## Claim-Intensity Discipline

Evidence strength and narrative heat are independent axes.

For each load-bearing claim, record both:

- `strongest_permitted_factual_wording`: the maximum factual assertion the source directly supports, with exact scope preserved
- `strongest_permitted_interpretive_wording`: the maximum interpretive assertion that is clearly labeled as analysis or reading

Narrative heat may come from: contrast, consequence, concrete imagery, rhythm, juxtaposition, implication, and precision.

Narrative heat may NOT come from: increased certainty, widened population, inflated causation, added severity, extended recency, or a rhetorical question that implies an unsupported fact.

A claim with weak evidence must not be written more forcefully than the evidence permits. A claim with strong evidence may — and should — be written at full permitted force. Do not flatten well-supported claims into cautious prose.

Allow forceful interpretation when clearly labeled and grounded in approved facts. Do not suppress bold-but-honest readings.

Add `suitability[]` to each claim: `hook` | `title` | `thumbnail` | `claws` | `ending` | `supporting-only`

## Blocked Overstatement Patterns

Mark these transitions as `forbidden`:

- animal experiment → direct human social law
- historical occurrence → universal human behavior
- correlation or chronology → causation
- one group, period, or region → all people throughout history
- adaptive hypothesis → established biological design
- "may contribute" → "is the reason"
- source interpretation → narrator fact
- absence of evidence → proof of absence
- possible outcome → inevitable outcome
- observed pattern → universal biological design
- one study → scientific consensus
- a source's interpretation → independently established fact

**Causal absolute bridge** — "never X," "always Y," "the only reason," "not X but Y" when applied to a phenomenon the evidence shows has multiple concurrent causes. Multi-causal phenomena must be narrated as multi-causal, or scoped explicitly to the dominant measured cause. Example of a forbidden causal absolute: "The thing pulling us back to our desks was never the money" when evidence shows both economic incentive and identity operate. Permitted alternative: "The compulsion appears to run deeper than economics alone" or "identity, not just income, is what the data consistently points to."

**False dichotomy** — framing a "not X but Y" contrast when the evidence supports X and Y simultaneously. A dichotomy is permitted only when a study or source explicitly tests and rules out the alternative. Otherwise label it as interpretation.

**Single-cause attribution of multi-driver events** — attributing a forecast, trend, or outcome entirely to one driver (e.g., AI) when the source names multiple drivers. The wording must preserve the source's causal scope. Example: "an all-transition forecast is not an AI-only forecast" — if WEF 2030 projections cover automation broadly, narration may not attribute those numbers to AI specifically.

**Scope universalization** — a finding from a specific sector, geography, time window, or demographic stated as if it applies universally. The narration must preserve the source's scope. Example: "job postings in AI-exposed software roles fell 40%" may not become "AI is taking the first rung" without explicitly noting the sector and time restriction. Universal-sounding language ("careers," "workers," "people") requires evidence with universal scope.

**Experiment as proof of universal mechanism** — a controlled trial showing one outcome in a bounded population stated as proof of a general human law. Label findings as findings: "in the Finland experiment, recipients still wanted to work" — not "humans require work for status regardless of income."

**Historical influence as sole origin** — "X caused Y" for a historical development when the evidence shows influence, contribution, or correlation. Luther's *Beruf* influenced the Protestant work ethic (attributed interpretation) but did not solely cause modern labor identity (overstated causal fact).

## Source-Scope Alignment

The approved wording may not exceed the source's metric, denominator, population, geography, time period, forecast horizon, or causal strength.

Explicitly reject common substitutions:

- exposure is not job loss
- correlation is not causation
- company attribution is not independently established cause
- an all-transition forecast is not an AI-only forecast
- an observed pattern is not universal biological design
- a possible outcome is not an inevitable one

## Inference Ledger

Interpretive conclusions — reasoning drawn from two or more facts toward a stated interpretation — must be tracked separately from the Evidence Ledger as the `inference_ledger[]`. An inference is permitted only when:

1. Every source fact it rests on has an approved `claim_id` in the Evidence Ledger.
2. The inferential step is explicitly documented (source facts → reasoning → conclusion).
3. The narration visibly signals it as analysis, not settled fact (e.g., "the implication is," "what the data suggests," "reading these together").

Each Inference Ledger entry:
- `inference_id`
- `source_claim_ids[]` — claim IDs the inference draws from
- `inferential_step` — the reasoning connecting source facts to conclusion
- `permitted_wording` — the maximum defensible interpretive phrasing
- `visibility_required` — YES; narration must label this as interpretation
- `do_not_imply` — the stronger factual form that is not permitted

Downstream stages may not present an `inference` as a `verified-fact`. Narrators may not drop the visibility signal ("the implication is," "the data suggests") even when it disrupts rhetorical flow. If the inference is strong enough to stand without the signal, it should be re-classified; if the evidence doesn't support re-classification, the signal stays.

## Procedure

1. Extract every load-bearing proposition, including implications created by titles, hooks, transitions, visuals, questions, and interpretive conclusions drawn across multiple claims.
2. Assign a stable `claim_id` for factual claims; assign `inference_id` for interpretive conclusions.
3. Link each to Source Ledger IDs.
4. Select one Evidence Ledger type; flag whether the proposition requires an Inference Ledger entry.
5. Write `strongest_permitted_factual_wording` and `strongest_permitted_interpretive_wording`.
6. Identify `narrative_heat_sources[]` available for this claim (contrast | consequence | imagery | rhythm | juxtaposition | implication | precision).
7. Run source-scope alignment against the ResearchPacket. Explicitly test for: causal absolutes, false dichotomies, single-cause attribution, scope universalization, experiment-as-proof, historical influence as sole origin.
8. Record scope, confidence, limitations, and verification date.
9. Assign `suitability[]`.
10. Mark unsupported alternatives as `forbidden`; do not merely soften them.
11. Produce a `do_not_imply` list for downstream stages.

## Evidence Ledger Entry

- `claim_id`
- `classification`
- `claim`
- `strongest_permitted_factual_wording`
- `strongest_permitted_interpretive_wording`
- `narrative_heat_sources[]` — contrast | consequence | imagery | rhythm | juxtaposition | implication | precision
- `suitability[]` — hook | title | thumbnail | claws | ending | supporting-only
- `source_ids`
- `confidence`: high, medium, or low
- `time_scope`
- `geographic_scope`
- `limitations`
- `last_verified_date`
- `do_not_imply`

## Required Output

- `evidence_ledger[]`
- `inference_ledger[]`
- `forbidden_claims[]`
- `do_not_imply[]`
- `claims_needing_more_research[]`
- `claims_removed[]`

## Downstream Contract

- Factual language must remain within `strongest_permitted_factual_wording`.
- Interpretive language must remain within `strongest_permitted_interpretive_wording` and stay visibly labeled.
- `attributed-report` must retain attribution.
- `interpretation` and `hypothesis` must stay visibly distinct from fact.
- `composite-scene` may dramatize documented conditions but may not invent a real person, quote, date, or event.
- Any new or materially strengthened proposition returns to research and this gate.
- Downstream stages may express a claim at full permitted force when evidence supports it. Do not re-soften approved wording.

## Completion Gate

Every material proposition is classified; every factual claim has source IDs; no invented source or false precision appears; unresolved load-bearing claims are blocked.

`claims_needing_more_research[]` must be empty before release. A claim cannot pass merely because it is attributed when it remains load-bearing, weakly sourced, or scope-mismatched. Return unresolved items to `documentary-current-research` or remove them from the argument.
