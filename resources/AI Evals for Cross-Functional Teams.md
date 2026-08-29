---
id: "372032b07eecd147"
title: "AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash"
aliases:
  - "AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Nachiket Paranjape – DoorDash, GenAI Platform team"
  - "Swaroop Chitlur Haridas – DoorDash, GenAI Platform team"
url: "https://www.youtube.com/watch?v=bMjlRrWjdT0"
origin: "https://www.youtube.com/watch?v=bMjlRrWjdT0"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-ai-evals-for-cross-functional-teams-nachiket-paranjape-swaroop-chitlur-haridas-d-372032b07eecd147.md"
created: "2026-08-29"
tags:
  - "topic/model-evaluation"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/ai-infrastructure"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-ai-evals-for-cross-functional-teams-nachiket-paranjape-swaroop-chitlur-haridas-d-372032b07eecd147|AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash raw transcript]]

# AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash

Source: youtube
Original link: https://www.youtube.com/watch?v=bMjlRrWjdT0

## One-Sentence Takeaway
DoorDash’s GenAI platform shifted evals from an engineering harness to a cross-functional workflow, cutting annotation costs and speeding iteration by letting non-engineers vibe-code their own tools on top of stable APIs.

## Short Summary
DoorDash’s GenAI platform team treats evals as a team sport: strategy/ops set quality bars, product managers define rubrics, operations run annotations, and engineering provides telemetry, datasets, and judges. The loop—trace, sample, annotate, calibrate, monitor—runs continuously, with self-serve judge calibration UIs that show before/after prompts so PMs can trust changes.

The API-first approach lets non-engineers (e.g., strategy/ops) point coding agents at endpoints to build custom annotation UIs for niche use cases (e.g., grading menus, reviewing images), avoiding the need for the platform team to anticipate every UI. This reduced per-annotation costs sharply and accelerated iteration cycles.

## Featured Speakers
- Nachiket Paranjape – DoorDash, GenAI Platform team
- Swaroop Chitlur Haridas – DoorDash, GenAI Platform team

## Main Ideas
- Evals evolved from an engineering harness to a cross-functional effort: strategy/ops set quality bars, product managers translate them into rubrics, operations run annotations, and engineering supplies telemetry, datasets, and judges.
- A continuous loop—trace → sample → annotate → promote golden set → calibrate judge → monitor—drives quality improvements, with flexibility in who owns judge prompts (varies by team) treated as a sign of learning, not a problem to standardize.
- API-first design (over UI-first) enabled non-engineers to vibe-code custom annotation tools (e.g., for menus or images) using coding agents, reducing platform team bottlenecks and per-annotation costs.
- Self-serve judge calibration UIs (e.g., using GEPA library) let PMs/operators run optimization loops, compare original vs. calibrated prompts side-by-side, and choose models (Gemini, Claude, OpenAI) without engineering support.

## Questions And Answers
- **Why did DoorDash move from UI-first to API-first?**
  UI-first couldn’t scale to diverse use cases; stable APIs let non-engineers build their own workflows (e.g., annotation UIs) with coding agents, unblocking teams.

- **How does judge calibration work in practice?**
  Teams start with a baseline judge prompt, run optimization (e.g., via GEPA), and review side-by-side comparisons of original vs. calibrated prompts in a self-serve UI to decide whether to trust the changes.

- **What org structure supports this?**
  Strategy/ops own quality bars, product managers own rubrics, operations run annotations, and engineering provides infrastructure—with prompt ownership varying by team as the org learns.

## Notable Details
- Per-annotation costs fell sharply after adopting self-serve annotation workflows.
- Coding agents (e.g., Codex, Claude Code) were used to "vibe-code" custom annotation UIs for niche tasks like menu grading or image review.
- Judge calibration supports multiple models (Gemini, Claude, OpenAI) and visualizes prompt changes to build trust.
- The platform reuses existing DoorDash infrastructure (e.g., LLM gateway, agent gateway) for authentication, identity, and cost management.
- Session-level, trajectory-based, and human-judgment-scaled evals address distinct needs (e.g., consumer discovery, personalization ML, multi-agent systems).

## Actionable Takeaways
- Adopt an API-first approach to empower non-engineers to build custom workflows (e.g., annotation UIs) with coding agents, reducing bottlenecks.
- Treat evals as a cross-functional loop (trace → sample → annotate → calibrate → monitor) with clear ownership divisions (strategy, product, ops, engineering).
- Implement self-serve judge calibration with side-by-side prompt comparisons to accelerate iteration and trust.
- Accept variability in prompt ownership across teams as a sign of organizational learning, not a failure to standardize.
- Reuse existing infrastructure (e.g., gateways, telemetry) to lower costs and latency for eval workflows.

## People, Companies, Tools, And Links Mentioned
- DoorDash
- Nachiket Paranjape
- Swaroop Chitlur Haridas
- Andy Fang (DoorDash co-founder)
- Raghav (DoorDash, referenced for session-level quality judgments)
- [GEPA library](https://github.com/gepa-ai/gepa) (prompt optimization)
- Codex (coding agent)
- Claude Code (coding agent)
- Gemini (model)
- Claude (model)
- OpenAI (models)

## Reading Priority

Medium – A concrete, practical case study on scaling evals as a cross-functional workflow with measurable cost/velocity improvements.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Model Evaluation|Model Evaluation]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/AI Infrastructure|AI Infrastructure]]
- Speakers: [[people/nachiket-paranjape-doordash|Nachiket Paranjape – DoorDash]], [[people/swaroop-chitlur-haridas-doordash|Swaroop Chitlur Haridas – DoorDash]]
