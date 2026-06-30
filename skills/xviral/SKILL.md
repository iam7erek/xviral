---
name: xviral
description: "Use when the user says XVIRAL, XViral, xviral, or any variant — activates the full documentary production system and presents the complete video intake form."
---

# XVIRAL — Documentary Production System

XVIRAL is the branded entry point for the full documentary-studio pipeline. When this skill activates, present the complete intake form below and nothing else. Do not begin production until the user returns it with at least a topic and language filled in.

## Full Intake Form

Return this form to the user, pre-filling any values already supplied:

```text
╔══════════════════════════════════════════════╗
║             X V I R A L  STUDIO             ║
╚══════════════════════════════════════════════╝

▸ TOPIC / WORKING TITLE:

▸ LANGUAGE:
▸ LANGUAGE VARIANT OR DIALECT:
▸ TARGET COUNTRY / MARKET:

▸ TARGET AUDIENCE:
  (age range, interests, level of prior knowledge)

▸ VIDEO DURATION:
  (e.g. 8 min, 12 min, 15 min)

▸ TONE:
  (e.g. dark and calm, sarcastic, serious, investigative)

▸ PRIMARY ANGLE DIRECTION:
  (optional — a direction, not a final angle; the system finds the sharpest one)

▸ REFERENCE VIDEOS OR CHANNELS FOR STYLE:
  (optional — for voice/pacing reference only, not content)

▸ MUST-INCLUDE IDEAS, EXAMPLES, OR EVENTS:

▸ AVOID:
  (topics, claims, framings, or examples to exclude)

▸ SERIES CONTEXT:
  (standalone episode, or part of a series? if series, what came before?)

▸ PUBLISHING TIMELINE:
  (optional — urgent deadline or flexible?)

▸ EXTRA NOTES:
  (anything else the system should know)
```

## After the User Returns the Form

Once the user submits the form with at least a topic and language:

1. Activate `documentary-pipeline-controller` immediately.
2. Run the full sequential pipeline without further approval: researcher → architect → writer → retention editor → ElevenLabs → final auditor.
3. Apply the Viral Precision system on both axes — Epistemic Integrity and Narrative Power — from the first research step through the final audit.
4. Output only the final paste-ready ElevenLabs narration when both `epistemic_integrity_status: PASS` and `viral_readiness_status: READY` are confirmed.

Blank fields use best judgment. Never ask the user to clarify a blank field before starting production.
