# XVIRAL — Documentary Studio

A Claude Code plugin that turns a topic into a fully-researched, fact-checked, paste-ready ElevenLabs documentary narration — through a multi-agent pipeline enforcing both **Epistemic Integrity** (claims are true and sourced) and **Narrative Power** (the script is actually worth watching).

Say **XVIRAL** to Claude Code to start.

## What it does

1. You give Claude Code a topic (and a few optional details — language, tone, duration, audience).
2. The `xviral` skill presents an intake form, then hands off to `documentary-pipeline-controller`, which runs a sequential agent pipeline:
   - **Researcher** — current research, primary-source closure, evidence classification
   - **Architect** — locks the angle, promise, motif, and narrative structure
   - **Writer** — writes the full spoken draft and claim map
   - **Retention editor** — retention surgery, voice cleanup
   - **Final auditor** — independently blocks factual, structural, or output-contract failures
3. Output is only released once `epistemic_integrity_status: PASS` and `viral_readiness_status: READY` are both confirmed.

## Install

Drop this folder into your Claude Code plugins/skills directory (or install as a plugin via your Claude Code plugin manager), then restart Claude Code. Once loaded, the `xviral` skill and its supporting agents/skills become available automatically.

## Structure

```
.claude-plugin/plugin.json      — plugin manifest
agents/                         — Architect, Researcher, Writer, Retention Editor, Final Auditor
skills/
  xviral/                       — entry point skill (intake form)
  documentary-pipeline-controller/ — orchestrates the full pipeline
  documentary-current-research/
  documentary-topic-intelligence/
  psychological-blueprint-architect/
  cinematic-monologue-writer/
  concrete-grounding-recording-pass/
  retention-surgery/
  noir-voice-anti-generic-style/
  evidence-anti-hallucination/
  elevenlabs-ready-voice-script/
  documentary-short-pack/
  platform-packaging/
  documentary-final-auditor/
```

## Requirements

- [Claude Code](https://claude.com/claude-code)
- ElevenLabs (or compatible TTS) account to use the final voice script output

## License

MIT — see [LICENSE](LICENSE).
