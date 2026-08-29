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
  - "Nachiket Paranjape, DoorDash GenAI Platform"
  - "Swaroop Chitlur Haridas, DoorDash GenAI Platform"
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
DoorDash’s GenAI platform shifted evals from an engineering harness to a cross-functional workflow, cutting per-annotation costs and accelerating iteration by letting non-engineers vibe-code their own tools on top of stable APIs.

## Short Summary
DoorDash’s GenAI platform team reframed evals as a team sport: strategy/ops set quality bars, product managers define rubrics, operations run annotations, and engineering provides telemetry, datasets, and judges. The loop—trace, sample, annotate, promote golden sets, calibrate judges, monitor—runs self-serve via a UI that shows before/after prompts so PMs can decide whether to trust changes.

The API-first approach let non-engineers use coding agents to build custom annotation UIs for use cases like grading restaurant menus or reviewing images, avoiding the need for the platform team to anticipate every interface. Judge prompt ownership varies by team, and that variability is treated as a sign of learning rather than a problem to standardize away.

## Featured Speakers
- Nachiket Paranjape, DoorDash GenAI Platform
- Swaroop Chitlur Haridas, DoorDash GenAI Platform

## Main Ideas
- Evals evolved from an engineering harness to a cross-functional effort where domain experts (strategy/ops, PMs, annotators) drive quality, while engineering supplies APIs, telemetry, datasets, and judges.
- A continuous loop—trace → sample → annotate → golden set → calibrate judge → monitor—forms the backbone of reliable AI shipping, with each step designed to be self-serve.
- API-first design enabled non-engineers to vibe-code custom annotation UIs using coding agents, reducing platform team bottlenecks and per-annotation costs.
- Judge prompt calibration is exposed via a UI that shows original vs. optimized prompts side-by-side, building trust and allowing PMs to approve changes without engineering hand-offs.
- Ownership of judge prompts varies by team (strategy/ops, PM, or engineering), and this flexibility is embraced as part of organizational learning rather than forced standardization.

## Questions And Answers
- **Why did DoorDash move from UI-first to API-first to workflow-first?**
  UI-first served non-engineers initially, but API-first unblocked engineers to build custom systems, and workflow-first empowered strategy/ops and PMs to operate the platform directly via coding agents.

- **How did self-serve judge calibration reduce friction?**
  A UI lets PMs or operators configure and run calibration loops (e.g., with GEPA) on any model, compare original and optimized prompts, and approve changes without engineering support.

- **What drove the drop in per-annotation cost?**
  Self-serve annotation platforms and vibe-coded UIs increased velocity, reduced dependency on engineers, and streamlined the workflow for thousands of weekly annotations.

## Notable Details
- The platform’s two surfaces: a **telemetry layer** (traces, scores, observations accessed via MCP/SDK/APIs) and a **workflow layer** (annotation tasks, golden dataset reviews, judge creation/calibration).
- **GEPA library** used for prompt optimization in judge calibration.
- **Coding agents (e.g., Codex, Claude Code)** enabled non-engineers to build custom annotation UIs by pointing agents at stable APIs.
- **Visualization in calibration UI** shows original vs. calibrated judge prompts to build trust and transparency.
- **Varied prompt ownership** across teams (strategy/ops, PM, or engineering) is treated as a feature, not a bug, to accommodate learning.

## Actionable Takeaways
- Adopt an **API-first approach** to empower non-engineers to build custom tools (e.g., annotation UIs) with coding agents, reducing bottlenecks.
- Design evals as a **self-serve, cross-functional workflow** with clear roles: strategy/ops set quality bars, PMs define rubrics, ops run annotations, engineering provides infrastructure.
- Implement **judge calibration UIs** that show before/after prompts to build trust and enable non-engineers to iterate independently.
- Embrace **variability in prompt ownership** as a sign of organizational learning, rather than enforcing premature standardization.
- Monitor **per-annotation costs** and iteration velocity as key metrics for eval platform success.

## People, Companies, Tools, And Links Mentioned
- DoorDash
- Nachiket Paranjape
- Swaroop Chitlur Haridas
- Andy Fang (DoorDash co-founder)
- Raghav (DoorDash, referenced for session-level quality judgments talk)
- [GEPA library](https://github.com/gepa-ai/gepa)
- Codex
- Claude Code
- Gemini
- Claude
- OpenAI

## Reading Priority

Medium – A concrete, practical case study on scaling evals as a cross-functional discipline with measurable cost and velocity improvements.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Model Evaluation|Model Evaluation]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/AI Infrastructure|AI Infrastructure]]
- Speakers: [[people/nachiket-paranjape|Nachiket Paranjape]], [[people/swaroop-chitlur-haridas|Swaroop Chitlur Haridas]]
