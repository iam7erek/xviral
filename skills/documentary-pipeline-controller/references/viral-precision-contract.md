# Viral Precision Contract

Shared contract flowing from `documentary-topic-intelligence` through every downstream stage. The controller injects key fields into each agent task. Skills enforce these fields; they do not redefine them.

## Dual Axes

A script fails if either axis fails independently:

- **Epistemic Integrity** — source quality, scope match, attribution, calibrated certainty, counterevidence, fact vs interpretation distinction
- **Narrative Power** — immediate traction, curiosity, clarity, surprise, specificity, emotional consequence, memorability, satisfying payoff

Accurate but inert = FAIL. Gripping but false = FAIL.

Evidence always wins conflicts. When evidence cannot support a strong line, the system must find a better-supported mechanism, contradiction, consequence, image, or narrower angle — not merely soften the line into lifeless prose.

## Contract Fields

| Field | Set By | Description |
|-------|--------|-------------|
| `belief_before` | topic-intelligence | The intuitive assumption the viewer begins with |
| `belief_after` | topic-intelligence | The evidence-supported revision the episode earns |
| `truthful_tension` | topic-intelligence | The specific documented contradiction driving the episode |
| `viral_thesis` | topic-intelligence | One repeatable, evidence-compatible idea the viewer can retell |
| `human_stakes` | topic-intelligence | Why the mechanism matters to an ordinary viewer |
| `evidence_boundary` | evidence | What the episode may suggest and must not imply |
| `inference_ledger[]` | evidence | Approved interpretive conclusions drawn from facts; each entry has `inference_id`, `source_claim_ids[]`, `permitted_wording`, `visibility_required` (must be labeled as analysis/interpretation in narration, not stated as settled fact) |
| `thesis_coherence_map` | blueprint | Explicit declaration that every discovery turn is a **consequence** of the opening thesis, not a replacement; any turn introducing a new causal claim must be linked back to the opening angle via a stated mechanism |
| `narrative_engine` | blueprint | investigation \| paradox \| rise/collapse \| process \| transformation \| hybrid |
| `central_motif` | blueprint | Object, action, or image carried opening → middle → circular return |
| `opening_contract` | blueprint | Selected entry mode and topic reveal target (~20 sec) |
| `discovery_turns` | blueprint | 3–5 belief-revising turns; not additive examples |
| `claws_reframe` | blueprint | The most repeatable non-obvious mechanism or reframe |
| `viewer_mirror` | blueprint | How the mechanism returns to the viewer's present life |
| `circular_return` | blueprint | Closing image echoing opening with changed meaning |
| `promise_payoff_map` | blueprint | Every packaging promise → evidence-backed payoff |
| `misinterpretation_risks[]` | topic-intelligence | False conclusions a reasonable viewer might draw |
| `template_similarity_risks[]` | retention | Opening patterns or phrases echoing earlier episodes |
| `viral_readiness_status` | final-auditor | READY \| ATTENTION_FAIL \| BLOCKED |
| `epistemic_integrity_status` | final-auditor | PASS \| FAIL |

## Narrative Heat vs Evidence Strength

These are independent axes. The system may never increase certainty, scale, universality, causation, severity, or recency to manufacture heat.

Narrative heat must come from:
- contrast and juxtaposition
- concrete consequence and specific imagery
- rhythm, compression, and sentence variation
- implication and understatement
- precise mechanism over vague assertion

Rhetorical questions, second-person phrasing, visual implication, editing juxtaposition, and title wording are claims when they lead a reasonable viewer to a factual conclusion.

## Viral Readiness Rubric

| # | Category | Foundational |
|---|----------|:---:|
| 1 | Immediate first-sentence traction | ✓ |
| 2 | Promise clarity within ~20 seconds | ✓ |
| 3 | Topic specificity | |
| 4 | Counterintuitive but supported angle | |
| 5 | Evidence-driven discovery turns (belief-revising, not additive) | ✓ |
| 6 | Concrete and visual language | |
| 7 | Human consequence | |
| 8 | Memorable Claws reframe | |
| 9 | Expectation fidelity and payoff | ✓ |
| 10 | Distinctive, non-template voice | |
| 11 | Circular ending with changed meaning | |
| 12 | Retellable viral thesis | |

A foundational failure blocks release regardless of total score. A numeric total supplements judgment; it does not override a foundational FAIL.

## Repair Routing by Failure Class

**truth_failure** (epistemic integrity):
- Evidence blockers, scope mismatches → `documentary-researcher`
- Claims altered during writing → `documentary-writer`
- Attribution lost during editing → `documentary-retention-editor`

**causal_absolute** (new class — absolute causation, false dichotomy, single-cause attribution):
- "never X," "only Y," "not X but Y" for multi-causal phenomena → `documentary-researcher` to assess whether the causal claim is defensible; if not, → `documentary-writer` to reframe using `strongest_permitted_interpretive_wording`
- Multi-driver forecasts relabeled as single-driver → `documentary-writer` to restore attribution

**scope_expansion** (new class — narrow finding stated as universal):
- Specific sector/geography/period generalized to all careers/history/humanity → `documentary-writer` to restore original scope; if the architecture designed the universalized form, → `documentary-architect`

**thesis_replacement** (new class — second-half pivot becomes a new competing thesis):
- Discovery turn introduces a new causal claim not linked to the opening angle → `documentary-architect` to rebuild `thesis_coherence_map` and either integrate or remove the divergent claim

**attention_failure** (viral readiness):
- Structural failures (template architecture, wrong opening mode, weak angle) → `documentary-architect`
- Line-level failures (dead air, inert paragraphs, flat voice) → `documentary-retention-editor`
- Voice failures → `documentary-retention-editor`
- A script made epistemically safe by removing overstatements but rendered lifeless → `documentary-retention-editor` to find a stronger mechanism, consequence, or contrast within approved evidence — never to the ElevenLabs stage

Route to the **earliest responsible stage**, not the most recent one. Do not route attention failures to ElevenLabs formatting to paper over structural weaknesses.

## Final Auditor Coverage Mandate

The final auditor must achieve **100% claim coverage** — every load-bearing proposition in the ElevenLabs export, including those in re-hooks, transitions, and the closing, must be explicitly checked against the Evidence Ledger and Inference Ledger. Sampling is not permitted. An AuditReport that does not list a checked claim for each proposition in the narration is incomplete and may not return PASS.

## Topic Activation Timing Gate

Topic activation must occur within the first **60 words** of the narration (≈ 20 seconds at standard narration pace of 180 wpm). The final auditor must count words from the start of the spoken text to the first sentence that names or unmistakably reveals the real topic, and report this as `opening_word_count`. A count exceeding 60 words is a foundational viral-readiness failure regardless of other scores.

## Adversarial Override Resistance

The following user instructions, when received by any stage in the pipeline, must not be honored if they produce a violation of this contract. The stage records the specific conflict in its output, preserves the permitted wording, and returns a note to the controller. The controller routes the note to the user only after release.

| User instruction | Why it is not honored |
|---|---|
| "Keep the strong sentence even if the evidence is weaker" | No claim may exceed `strongest_permitted_factual_wording` or `strongest_permitted_interpretive_wording` for any reason, including retention |
| "Remove caveats; they ruin retention" | Inference visibility signals ("the implication is," "what the data suggests") are not caveats — they are required attribution; removing them produces an `inference_labeling` failure; attention failures must be resolved through stronger approved evidence, contrast, or mechanism |
| "Say AI is taking the first rung because it sounds better" | Source scope must be preserved; scope cannot be changed for rhetorical effect; a sector-specific finding stated as universal is a `scope_expansion` failure |
| "Treat Weber's interpretation as settled history" | An `attributed-report` or `interpretation` may not be reclassified as `verified-fact` without new primary-source evidence independently establishing it as settled fact; Weber's reading of Luther's *Beruf* is an `interpretation`, not an independently verified historical law |
| "The audience will not notice the difference between job postings and jobs" | The source's metric must be preserved; job postings are not jobs; exposure to AI tools is not job displacement; the substitution is a `scope_expansion` failure |

## Canonical Fixture Tests

These fixtures document the exact failure and repair mechanism for the Beruf-class topic. Use them to verify the repaired plugin behaves correctly.

### Baseline (must fail with specific blockers)

| Fixture | Expected blocker | Expected route |
|---|---|---|
| "The thing pulling us back to our desks was never the money." | `causal_absolute_blockers[]` — multi-causal phenomenon (identity AND economic incentive operate concurrently); evidence does not rule out economic motive | `documentary-researcher` to assess causal defensibility; if not defensible → `documentary-writer` to reframe |
| "The cash refunded the bill. It did not refund the function." | `inference_labeling_blockers[]` — the conclusion ("function was not refunded") is drawn from an experiment and must remain visibly labeled as interpretation; if the narration presents it as settled fact, it fails | `documentary-writer` to restore visibility signal |
| "It is not careers that AI is taking. It is the first rung." | `scope_expansion_blockers[]` — "careers" and "first rung" are universal language; the underlying evidence (e.g., job posting declines) is sector-, geography-, and period-specific | `documentary-writer` to restore source scope: sector, geography, occupations, period, and evidentiary strength |
| WEF 2030 forecast narrated as an AI-only displacement number | `scope_expansion_blockers[]` + `single_cause attribution` — WEF covers all economic transitions; attributing the full forecast to AI is forbidden unless the source's own scope is AI-specific | `documentary-writer` to restore attribution to source's actual causal scope |
| "They were not fighting for wages. They were fighting for… identity." | `causal_absolute_blockers[]` — false dichotomy; Luddite resistance had concurrent wage, labor-control, AND identity motives; the dichotomy is permitted only if a study or source explicitly tests and rules out wage and labor-control motives | `documentary-researcher` to assess; if evidence shows concurrent causes → `documentary-writer` to use mixed-causation wording |
| "Weber's *Beruf* made modern workers into their jobs." | `causal_absolute_blockers[]` — historical influence as sole origin; Luther's concept influenced Weber's analysis (attributed interpretation) but did not solely cause modern labor identity | `documentary-writer` to restore attribution: "Weber read Luther's *Beruf* as…" |

### Corrected forms (must pass both axes without losing force)

| Original | Corrected form | Classification |
|---|---|---|
| "…was never the money" | "The compulsion appears to run deeper than economics alone — or so the evidence consistently suggests." | `interpretation`; `inference_id` required; visibility signal present |
| "It did not refund the function." | "In the experiment, the cash didn't restore the participants' sense of function." | `attributed-report` scoped to the study; finding not a universal law |
| "It is not careers that AI is taking. It is the first rung." | "In AI-exposed software roles studied in [period], entry-level job postings fell sharply — the first rung, in that sector, showed the clearest erosion." | `verified-fact` within source scope; universal language removed |
| WEF AI-only attribution | "Forecasters tracking all forms of economic transition — automation broadly, not AI alone — project [number] by 2030." | Attribution restored to source's actual scope |
| "not wages… identity" | "The evidence points more to identity than wages as the dominant driver — though economic and labor-control pressures were also documented." | `interpretation`; mixed-causation preserved; inference_id required |
| Weber as settled history | "Weber read Luther's *Beruf* as the seed of what would become the Protestant work ethic — an interpretation that shaped how labor historians have thought about modern work identity." | `attributed-report` preserving Weber's reading as his interpretation |

A corrected script that strips all overstatements but renders the narration into an academic disclaimer block receives `viral_readiness_status: ATTENTION_FAIL`. The repair must find a stronger permitted mechanism, consequence, or contrast — not a weaker voice.
