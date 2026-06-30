---
name: documentary-pipeline-controller
description: "Use when the user wants to make a YouTube documentary, supplies a topic, or returns the Documentary Studio intake form."
---

# Documentary Studio Controller

Keep the main context small. Orchestrate the five plugin agents through a file-backed, sequential pipeline. Do not perform specialist research, architecture, writing, editing, or auditing in the main conversation.

The system operates on two axes simultaneously: **Epistemic Integrity** and **Narrative Power**. See `references/viral-precision-contract.md` for the shared contract fields, repair routing by failure class, and the Viral Readiness Rubric. Both axes are enforced from research through final audit; a failure on either axis fails the release.

## One-Shot Intake

For a generic video request or bare topic, return one localized form and nothing else:

```text
TOPIC / WORKING TITLE:
LANGUAGE:
LANGUAGE VARIANT OR DIALECT:
TARGET COUNTRY / MARKET:
TARGET AUDIENCE:
VIDEO DURATION:
TONE:
MUST-INCLUDE IDEAS, EXAMPLES, OR EVENTS:
AVOID:
```

Pre-fill supplied values. Say briefly that blank fields use best judgment. When the user returns the form with a topic and language, run the pipeline without intermediate approval.

## Run Directory

Create a private run directory such as:

`.documentary-studio/runs/<timestamp>-<short-slug>/`

Use file paths for hand-offs. Give every agent input paths and one `artifact_path`. Agents must return the path only, never paste the artifact into the parent conversation.

## Sequential Pipeline

1. Dispatch `documentary-researcher`.
   - Output: `research.md`
   - Produces: Source Ledger, Evidence Ledger with `strongest_permitted_factual_wording` and `suitability[]`, `inference_ledger[]`, `narrative_assets{}`, `forbidden_narrative_traps[]`

2. Dispatch `documentary-architect`.
   - Inputs: intake and `research.md`
   - Output: `architecture.md`
   - Produces: TopicBrief with all Viral Precision fields including `thesis_coherence_map`, Blueprint with `opening_mode`, per-turn discovery records, and `template_risks_cleared[]`

2.5. **Evidence-Challenge Step** — Before dispatching the writer, the controller reads `architecture.md` and checks:
   - Does every discovery turn in the Blueprint map to a `claim_id` or `inference_id` in `research.md`?
   - Does `thesis_coherence_map` explicitly link each discovery turn back to the opening thesis via a stated mechanism?
   - Are any causal absolutes ("never," "only," "not X but Y") in the architecture supported by evidence that explicitly rules out the alternative?
   - Does the architecture introduce any multi-driver forecasts attributed to a single cause?
   If any of these checks fails, route back to `documentary-architect` with the specific gap before proceeding. Do not pass an architecture with unresolved causal absolutes or unmapped discovery turns to the writer.

3. Dispatch `documentary-writer`.
   - Inputs: intake, `research.md`, and `architecture.md`
   - Output: `draft.md`
   - Produces: narration, Claim Map with `inference_id` coverage, `paragraph_utility_log[]`

4. Dispatch `documentary-retention-editor`.
   - Inputs: all prior artifacts and `draft.md`
   - Output: `clean-draft.md`
   - Produces: revised narration, `attention_failure_routes[]`, `promise_audit`

5. Invoke `elevenlabs-ready-voice-script` on `clean-draft.md`.
   - Output: `elevenlabs.txt`

6. Dispatch `documentary-final-auditor`.
   - Inputs: all artifacts including `elevenlabs.txt`
   - Output: `audit.md`
   - Returns: `epistemic_integrity_status`, `viral_readiness_status`, and `claims_checked_count`

Never run dependent stages in parallel.

## Viral Readiness Gate

Before publishing the visible output, confirm both statuses from `audit.md`:

- `epistemic_integrity_status: PASS`
- `viral_readiness_status: READY`

If either fails, route to the Repair Loop before releasing any output to the user.

## Repair Loop

If the auditor returns any FAIL or ATTENTION_FAIL, read only `audit.md`. Route each blocker by failure class per `references/viral-precision-contract.md`:

**truth_failure** (epistemic integrity):
- Evidence blockers, scope mismatches, unsupported claims → `documentary-researcher`
- Claims altered during writing → `documentary-writer`
- Attribution lost during editing → `documentary-retention-editor`

**causal_absolute** (absolute causation, false dichotomy, single-cause attribution):
- Architecture designed the absolute → `documentary-architect` to rebuild with multi-causal wording
- Writer introduced the absolute → `documentary-writer` to replace with `strongest_permitted_interpretive_wording`

**scope_expansion** (narrow finding stated universally):
- Architecture designed the universal framing → `documentary-architect`
- Writer widened scope → `documentary-writer` to restore original scope limits

**thesis_replacement** (second-half pivot replaces opening thesis):
- `documentary-architect` to rebuild `thesis_coherence_map`; the divergent claim must be mechanically linked to the opening thesis or removed

**attention_failure** (viral readiness):
- Structural failures (template architecture, wrong opening mode, weak angle) → `documentary-architect`
- Line-level failures (dead air, inert paragraphs, flat voice) → `documentary-retention-editor`
- Voice failures → `documentary-retention-editor`
- A corrected script that is now epistemically valid but lifeless → `documentary-retention-editor` to find a stronger mechanism, consequence, or contrast within approved evidence

After repair, re-run the Evidence-Challenge Step (2.5) if the repair touched architecture or research. Rebuild every downstream artifact from the corrected stage. Invoke `elevenlabs-ready-voice-script` again on the regenerated clean draft. Dispatch a new independent audit on the regenerated `elevenlabs.txt`.

Do not route attention failures to `elevenlabs-ready-voice-script` to paper over structural weaknesses. Do not ask the user to resolve research or writing defects. Remove or narrow claims that cannot be verified. Stop only if the user's requested thesis itself cannot be made factual without materially changing the topic.

## Deterministic Artifact Validation

Before dispatching each stage, verify the following required fields are present and non-empty in the incoming artifact. Block with `VALIDATION_BLOCKED` and list the exact missing fields if any check fails. Do not pass partial artifacts downstream.

### After Step 1 (research.md) — block if missing:
- `as_of_date`, `source_ledger[]` (≥ 1 entry with `source_id`, `URL`, `primary_source_status`), `candidate_claims[]` (each with `claim_id`), `evidence_ledger[]` (each with `claim_id`, `classification`, `strongest_permitted_factual_wording`, `strongest_permitted_interpretive_wording`), `inference_ledger[]` (each with `inference_id`, `source_claim_ids[]`, `inferential_step`, `permitted_wording`, `visibility_required: YES`, `do_not_imply`), `forbidden_narrative_traps[]`, `narrative_assets{}` (with `concrete_anchors[]` ≥ 3, `hook_candidates[]`, `claws_candidates[]`, `payoff_candidates[]`), `claims_needing_more_research[]` (must be empty)

### After Step 2 (architecture.md) — block if missing:
- `locked_angle`, `belief_before`, `belief_after` (must differ from `belief_before`), `viral_thesis`, `misinterpretation_risks[]` (≥ 2 entries), `promise_contract` (with `click_reason`, `expected_payoff`, `evidence_boundary`), `selected_architecture`, `opening_mode`, `opening_mode_rationale`, `central_motif`, `discovery_turns[]` (3–5 entries each with `prior_belief`, `new_evidence`, `belief_revision`, `concrete_anchor`, `loop_action`), `thesis_coherence_map` (each discovery turn linked to opening thesis via stated mechanism), `promise_payoff_map[]`, `claws_beat` (with target timestamp and `claim_ids[]`), `template_risks_cleared[]`

### After Step 2.5 (evidence-challenge) — block if:
- Any discovery turn has no `claim_id` or `inference_id` mapping in research.md
- `thesis_coherence_map` has any turn without a stated mechanical link to the opening thesis
- Any causal absolute in the architecture has no evidence explicitly ruling out the alternative
- Any multi-driver forecast is attributed to a single driver

### After Step 3 (draft.md) — block if missing:
- `claim_map[]` (every load-bearing proposition has `claim_id` or `inference_id`), `paragraph_utility_log[]` (no "restate" or "filler" entries), `new_or_changed_claims[]` (must be empty), `inference_visibility_log[]` (each `inference_id` used confirms visibility signal present)

### After Step 4 (clean-draft.md) — block if missing:
- `claim_map`, `promise_audit`, `added_claims[]` (must be empty), `altered_claims[]` (must be empty)

### After Step 6 (audit.md) — block release if:
- `epistemic_integrity_status` is not `PASS`
- `viral_readiness_status` is not `READY`
- `claims_checked_count` is not equal to total propositions extracted from narration
- Any of these arrays is non-empty: `evidence_blockers[]`, `causal_absolute_blockers[]`, `scope_expansion_blockers[]`, `inference_labeling_blockers[]`, `thesis_coherence_blockers[]`

## Context Isolation

- The Controller receives status and path only from agents.
- Do not paste research packets, drafts, or audit reports into the main context.
- Do not invoke specialist skills in the main context except `elevenlabs-ready-voice-script`.
- `platform-packaging` and `documentary-short-pack` run only when explicitly requested.
- Do not make one agent perform another agent's responsibility.

## Visible Output

After `epistemic_integrity_status: PASS` and `viral_readiness_status: READY`, read `elevenlabs.txt` and output it verbatim.

The visible answer contains only paste-ready narration and sparse valid English ElevenLabs tags. No title, markdown fence, sources, explanations, audit result, or text addressed to the user.
