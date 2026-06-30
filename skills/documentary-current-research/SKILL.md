---
name: documentary-current-research
description: "Use when a documentary request needs current facts, sources, dates, statistics, entity verification, conflict resolution, or a Source Ledger, and whenever documentary-pipeline-controller invokes the mandatory research stage."
---

# Documentary Current Research

Build the dated, auditable research foundation for a faceless YouTube documentary in the controller-supplied language and market. Consume the controller's `RequestSpec`; do not classify user intent or choose an output route.

Research is mandatory even for idea-led philosophical essays. Establish the real events, definitions, examples, counterarguments, and limits that make the interpretation honest.

## Freshness Rule

Current entities, events, companies, people, technology, policies, laws, regulations, prices, rankings, and statistics require web verification. Treat remembered facts as leads, not evidence.

- Record the research `as_of_date` and access date.
- Distinguish publication/update date from the date the event occurred.
- Prefer sources current enough for the claim's time scope.
- Re-check claims containing "current," "latest," "today," "now," or similar language immediately before hand-off.
- Do not infer that an undated or old page describes present conditions.

## Source Hierarchy

Prefer the highest available level and preserve source independence:

1. Primary official material: statutes, regulations, court records, government data, filings, transcripts, technical standards, first-party announcements, and original documents.
2. Original research and data: peer-reviewed papers, reputable research institutes, methodological reports, and documented datasets.
3. High-quality reporting: reputable outlets with named reporters, direct sourcing, corrections practices, and clear event dates.
4. Specialist analysis: credible trade publications, professional bodies, and identified subject-matter experts.
5. Discovery-only material: aggregators, search snippets, unsourced summaries, social posts, forums, and user-generated content.

Use level 5 to find stronger sources, not as sole support for a material factual claim. Treat first-party company or individual statements as primary evidence of what they said, not independent proof that the statement is true.

## Primary-Source Closure

For every load-bearing claim, replace a secondary report with the original source when that original source is accessible: study, dataset, official report, transcript, filing, law, archive, or first-party statement. Secondary reporting may add context or independent scrutiny, but it may not remain the sole support merely because it summarizes the original conveniently.

If the original source is inaccessible, state that limitation and lower the support level. Do not describe the claim as directly verified.

## Source-Scope Match

Before approving a source for a claim, compare:

- metric and denominator
- population and sample
- geography
- event/data period and publication date
- forecast horizon
- correlation, attribution, or causal strength
- the phenomenon actually measured

The narration may not widen any of these dimensions. Exposure is not job loss; adoption is not productivity; a forecast covering all economic transitions is not an AI-only forecast; one historical population is not all humanity.

## Research Procedure

1. Decompose the topic into dated candidate claims, definitions, examples, causal assertions, and likely counterclaims.
2. Search the source hierarchy from primary evidence outward.
3. Open and inspect the underlying source; do not cite a search-result snippet as evidence.
4. Capture source metadata and connect each source to stable `claim_id` values.
5. Perform primary-source closure for every load-bearing claim.
6. Record source-scope dimensions and compare them with the proposed narration wording.
7. Triangulate consequential, surprising, disputed, or rapidly changing claims with independent sources when available.
8. Separate documented fact from source allegation, expert interpretation, controller inference, and unresolved uncertainty.
9. Surface conflicts, missing evidence, and scope limits instead of averaging them into false certainty.
10. Identify seductive viral claims that are unsupported or overstated — record them in `forbidden_narrative_traps[]` so downstream stages cannot revive them.
11. Collect narrative assets: for each well-supported claim, identify its strongest counterintuitive angle, the best concrete anchor (object, action, document, sound, visual), and its suitability for hook, Claws beat, or payoff.
12. Hand the complete `ResearchPacket` to the controller and `evidence-anti-hallucination`.

## Source Ledger

Create one row per source with these fields:

- `source_id`
- `URL`
- `publisher`
- `title`
- `publication/update date`
- `event date`
- `access date`
- `source type`
- `supported claim IDs`
- `limitations`
- `primary_source_status`: original, secondary-with-original, original-inaccessible, or discovery-only

Use an explicit null such as `not stated` when a date or field is unavailable. In `limitations`, note conflicts of interest, paywalls, inaccessible methodology, geographic scope, sample limits, translation issues, outdated material, or whether the source only reports another source's claim.

## Candidate Claim Schema

Create one row per research proposition:

- `claim_id`
- `claim_text`
- `claim_kind`: fact, statistic, quote, allegation, interpretation, or definition
- `time_scope`
- `geographic_scope`
- `source_ids`
- `support_level`: direct, corroborated, single-source, disputed, or unsupported
- `conflicting_source_ids`
- `uncertainty`
- `safe_research_wording`
- `source_scope`: metric, population, geography, period, and causal strength
- `last_verified_date`
- `narrative_suitability[]`: hook | claws | payoff | supporting-only
- `best_concrete_anchor`: the most specific researched object, action, document, or setting tied to this claim

Quotes require the original speaker, exact context, date, and a source that supports the quoted wording. Statistics require the metric definition, period, geography, denominator where relevant, and originating dataset or methodology.

## Conflict and Uncertainty Contract

- List material disagreements in `conflicts[]` with each source's position and the reason the discrepancy may exist.
- List unresolved questions in `uncertainties[]`; never hide them in prose.
- Do not convert absence of evidence into evidence of absence.
- Do not convert correlation, chronology, or a source's opinion into causation.
- If only a partisan, promotional, anonymous, or single secondary source supports a claim, label that limitation.
- If reliable sources cannot resolve a claim, mark it disputed or unsupported for the Evidence Ledger.

## Causal-Chain Validation

For every claim that involves causation or exclusion — "X caused Y," "not X but Y," "never X," "only X" — explicitly record before approving the claim:

1. The evidence directly supporting the proposed cause
2. Whether the evidence **explicitly tests and rules out** alternative causes, or merely fails to measure them
3. The maximum permitted causal wording given that evidence

A causal absolute is permitted only when the evidence rules out the alternative explicitly. When evidence shows multiple concurrent causes, the claim must be written as multi-causal or scoped to the dominant measured cause with acknowledgment of alternatives. Record forbidden causal absolutes in `forbidden_narrative_traps[]`.

Examples:
- "The thing pulling us back to our desks was never the money" → requires evidence that explicitly tests and rules out economic incentive as a concurrent cause; if not present, the causal absolute is forbidden; permitted wording: "the evidence points more to identity than income as the dominant driver"
- "Luther's *Beruf* caused modern labor identity" → requires independent evidence beyond Weber's interpretation; if not present, classify as `interpretation` with attribution to Weber; permitted wording: "Weber read Luther's *Beruf* as the seed of the Protestant work ethic"

## Multi-Driver Attribution

For any forecast, trend, or displacement number drawn from a multi-cause source (WEF, McKinsey, Oxford Futures, OECD, ILO), record:

1. The source's actual causal scope: does it cover AI only, or automation broadly, or all economic transitions?
2. The maximum attribution to any single driver the source explicitly permits
3. The forbidden attribution: the scope the source does not support

A forecast that covers all economic transitions is **not** an AI-only forecast. Narration may attribute numbers to AI only if the source's own methodology is AI-specific. Otherwise the attribution must match the source's scope. Record scope-narrowed versions in `forbidden_narrative_traps[]`.

Example: WEF 2030 job creation/displacement projections → cover automation broadly, not AI alone; maximum permitted attribution: "forecasters tracking all forms of economic transition project…"; forbidden: attributing the full WEF number to AI.

## ResearchPacket Handoff

Return:

- `topic`
- `as_of_date`
- `research_summary` — what is well established, what is contested, what changed recently, and which evidence limits the documentary's framing
- `source_ledger[]`
- `candidate_claims[]`
- `conflicts[]`
- `uncertainties[]`
- `research_gaps[]`
- `recommended_do_not_claim[]`
- `forbidden_narrative_traps[]` — seductive viral claims that are unsupported or overstated; downstream stages must not revive these
- `narrative_assets{}`:
  - `counterintuitive_findings[]`: claims where evidence contradicts common intuition, with source IDs
  - `concrete_anchors[]`: researched objects, actions, settings, documents, or sounds that can ground the narration
  - `threshold_moments[]`: chronological turning points or specific events with documented dates
  - `mechanisms[]`: causal chains with explicit scope and confidence limits
  - `credible_counterarguments[]`: the strongest objections the evidence supports, with source IDs
  - `consequential_examples[]`: specific documented cases or outcomes that make the mechanism real
  - `hook_candidates[]`: claim IDs best suited to open curiosity without overstating
  - `claws_candidates[]`: claim IDs most likely to support a non-obvious memorable reframe
  - `payoff_candidates[]`: claim IDs that can deliver on a click promise

## Completion Gate

Do not hand off until:

- every material candidate claim has a `claim_id`;
- every supported claim points to one or more Source Ledger rows;
- all required ledger fields are present;
- current claims have fresh web verification;
- conflicts and uncertainty are visible;
- unsupported claims are clearly marked rather than silently omitted;
- every load-bearing claim has primary-source closure or an explicit inaccessible-original limitation;
- proposed wording matches the source's metric, population, geography, period, and causal strength;
- no URL, date, quotation, statistic, publisher, or source title was invented;
- `forbidden_narrative_traps[]` is populated with any identified viral overstatements;
- `narrative_assets{}` is complete with at least three concrete anchors and identified hook/Claws/payoff candidates.
