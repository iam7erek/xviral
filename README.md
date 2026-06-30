<div align="center">

# XVIRAL

**Documentary Studio — a multi-agent Claude Code plugin that turns a topic into a paste-ready, fact-checked documentary narration.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Plugin version](https://img.shields.io/badge/version-1.2.0-informational)](.claude-plugin/plugin.json)
[![Claude Code](https://img.shields.io/badge/built%20for-Claude%20Code-7c3aed)](https://claude.com/claude-code)

</div>

---

## What is XVIRAL?

XVIRAL is a [Claude Code](https://claude.com/claude-code) plugin. Say **`XVIRAL`** in a Claude Code session and it takes a topic from idea to a paste-ready ElevenLabs narration, by running it through a pipeline of specialized agents that enforce two things on every release:

- **Epistemic Integrity** — every claim is true, sourced, and traceable
- **Narrative Power** — the script earns attention; it's actually worth watching

No manual stitching of research, writing, and fact-checking across separate prompts — one pipeline, one accountable output.

## How it works

```
  you: "XVIRAL"
        │
        ▼
  ┌─────────────┐     intake form (topic, language, tone, duration, audience…)
  │   xviral    │────────────────────────────────────────────────────────────►
  └─────────────┘
        │
        ▼
  ┌───────────────────────────┐
  │ documentary-pipeline-      │  orchestrates the run, sequentially:
  │ controller                 │
  └───────────────────────────┘
        │
        ├─► Researcher          current research, primary-source closure, evidence classification
        ├─► Architect           locks the angle, promise, motif, narrative structure
        ├─► Writer              full spoken draft + claim map
        ├─► Retention editor    retention surgery, voice cleanup
        └─► Final auditor       independently blocks factual / structural / contract failures
                │
                ▼
   epistemic_integrity_status: PASS
   viral_readiness_status:     READY
                │
                ▼
   paste-ready ElevenLabs narration
```

Output is only released once both status checks pass — there's no partial or unaudited output.

## Quickstart

1. Install the plugin (see below).
2. In a Claude Code session, type:
   ```
   XVIRAL
   ```
3. Fill in the intake form Claude Code returns (topic and language are the only required fields — everything else is optional and defaults to best judgment).
4. The pipeline runs end-to-end and hands back a paste-ready narration script for ElevenLabs (or any compatible TTS).

## Install

Clone this repo into your Claude Code plugins/skills directory:

```bash
git clone https://github.com/iam7erek/xviral.git
```

Then point your Claude Code plugin manager at the cloned `xviral` folder (or copy it into your skills directory directly), and restart Claude Code. The `xviral` skill and every supporting agent/skill load automatically — no further configuration needed.

## Project structure

| Path | Purpose |
|---|---|
| `.claude-plugin/plugin.json` | Plugin manifest |
| `agents/` | Architect, Researcher, Writer, Retention Editor, Final Auditor |
| `skills/xviral/` | Entry point — presents the intake form |
| `skills/documentary-pipeline-controller/` | Orchestrates the full pipeline |
| `skills/documentary-current-research/` | Current-events research pass |
| `skills/documentary-topic-intelligence/` | Topic scoping & intelligence |
| `skills/psychological-blueprint-architect/` | Narrative angle & structure |
| `skills/cinematic-monologue-writer/` | Spoken-draft writing |
| `skills/concrete-grounding-recording-pass/` | Grounds abstractions in concrete detail |
| `skills/retention-surgery/` | Pacing & retention editing |
| `skills/noir-voice-anti-generic-style/` | Style pass — kills generic AI voice |
| `skills/evidence-anti-hallucination/` | Claim verification against sources |
| `skills/elevenlabs-ready-voice-script/` | Final TTS-ready formatting |
| `skills/documentary-short-pack/` | Short-form cutdown packaging |
| `skills/platform-packaging/` | Per-platform packaging (titles, descriptions, etc.) |
| `skills/documentary-final-auditor/` | Final pass/fail gate |

## Requirements

- [Claude Code](https://claude.com/claude-code)
- An [ElevenLabs](https://elevenlabs.io) (or compatible TTS) account to voice the final script

## Contributing

Issues and PRs are welcome — open one on the [issues page](https://github.com/iam7erek/xviral/issues).

## Author

[**@iam7erek**](https://github.com/iam7erek)

## License

MIT — see [LICENSE](LICENSE).
