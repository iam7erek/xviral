---
name: elevenlabs-ready-voice-script
description: "Use when the controller routes an explicit ElevenLabs, TTS, audio-tag, paste-ready, or completed One-Shot Intake request."
---

# ElevenLabs-Ready Voice Script

This is a terminal formatter, not a writing or research stage. Use it only after an explicit ElevenLabs/TTS/audio-tag request or completed One-Shot Intake routed by the controller.

## Required Input

- Approved `clean_recording_draft`
- Language
- Optional voice and performance preference

## Preserve Meaning

- Do not add, remove, strengthen, or reinterpret claims.
- Do not add dialogue, scenes, examples, or emotional conclusions.
- Preserve names and technical terms while normalizing their spoken form.
- If normalization could change meaning, leave the original wording.
- Preserve intentional voltage variations from the approved draft — do not flatten the script to a uniform delivery register.

## Eleven v3 Formatting

- Use English bracketed tags that describe audible delivery or reactions.
- Place tags immediately before the affected line.
- Use no more than 1–3 tags per cue and do not tag every sentence.
- Prefer common tags such as `[calm]`, `[serious]`, `[low voice]`, `[slow]`, `[tense]`, `[curious]`, `[whispers]`, `[sighs]`, and `[exhales]`.
- Use punctuation, line breaks, ellipses, and dashes for pacing.
- Do not use SSML break tags.
- Do not use visual, camera, music, B-roll, movement, or production tags.
- Environmental sound effects require an explicit sound-design request.
- Keep tags in English even when spoken text is another language.

## Tag Discipline

Do not use performance tags to:
- simulate certainty, urgency, or authority not present in the approved wording
- create melodrama around claims the evidence does not support
- add emotional weight to passages deliberately written with restraint

Performance tags improve natural delivery and preserve approved voltage changes. They may not substitute for narrative substance or simulate unsupported dramatic effect.

## Spoken Normalization

Normalize numbers, dates, currencies, abbreviations, URLs, and units only when the intended pronunciation is unambiguous and appropriate to the target language.

## Final Sanitizer

Remove:

- headings, markdown, numbering, bullets
- research notes, Claim Map, citations, QA, edit logs
- visual, scene, camera, timestamp, chapter, packaging, and source notes
- `[PAUSE]` and unsupported SSML

Convert useful pacing to line breaks, punctuation, or valid audible tags.

## Required Output

Only paste-ready spoken text and valid audible performance tags. No title, explanation, packaging, sources, or notes.

For One-Shot ElevenLabs Narration, do not add a greeting, completion message, markdown fence, language label, or any text addressed to the user. The first visible character begins the narration or a valid audible tag; the last visible character ends the narration.

## Quality Gate

The output can be pasted directly into ElevenLabs v3 without deleting a line; tag density is restrained; no tag simulates unsupported certainty or melodrama; intentional voltage shifts from the approved draft are preserved; and the wording remains factually identical to the approved clean recording draft. Release remains blocked until `documentary-final-auditor` audits this exact terminal export.
