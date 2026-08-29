---
id: "1642996e12a276c2"
title: "Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber"
aliases:
  - "Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=17-YSUHo6Lk"
origin: "https://www.youtube.com/watch?v=17-YSUHo6Lk"
published: "2026-08-21"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-agentic-sdlc-at-uber-uday-kiran-medisetty-adam-huda-uber-1642996e12a276c2.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/ai-infrastructure"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-agentic-sdlc-at-uber-uday-kiran-medisetty-adam-huda-uber-1642996e12a276c2|Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber raw transcript]]

# Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber

Source: youtube
Original link: https://www.youtube.com/watch?v=17-YSUHo6Lk

## One-Sentence Takeaway
Uber’s agentic SDLC now generates over 70 % of pull requests and doubled lines of code per engineer by routing every model call through a 100 ms guardrail gateway and slashing fleet-wide token use >40 % with an MCP gateway, a 40 M-entry context graph, and a managed skills marketplace.

## Short Summary

Uber’s production agentic workflow is built on six infrastructure pieces: a single model gateway that enforces identity, PII redaction, and five safety models within a 100 ms budget; an MCP gateway that projects 1,000+ internal and SaaS APIs into a CLI to avoid context-window bloat; pre-provisioned “balloon” DevPods; a skills marketplace with 2,500 vetted entries running 20 k executions/day; and a context graph of 150 node/edge types and 40 M entries that replaces 20–30 scattered systems. The result is end-to-end feature delivery from Slack to draft PR, with validation shifted left via simulator screenshots vs. Figma specs, and maintenance looped back as labeled data to improve skills.

The bottleneck has shifted from “can we build it?” to “should we build it?” as capacity, CI load, and decision-making become the new constraints.

## Featured Speakers
- Uday Kiran Medisetty – Engineering leader at Uber
- Adam Huda – Engineering leader at Uber

## Main Ideas
- A centralized model gateway enforces Spire identity, redacts 20+ PII types, and runs five specialized safety models while staying under 100 ms; it handles 100 M requests/day across 800 projects with full attribution.
- An MCP gateway plus CLI projection keeps tool responses out of the context window, cutting fleet-wide token use by >40 %; a Code Mode skill dynamically generates Python scripts to optimize the heaviest MCP consumers.
- A context graph with 150 node/edge types and 40 M entries consolidates ownership, dependency, and design data that agents previously scraped from 20–30 separate systems, improving token efficiency, turns, and latency.
- End-to-end feature delivery stops at draft PR to validate in an inner loop (simulator screenshots vs. Figma specs, staging integration) before CI, reducing outer-loop load and improving diff quality.
- Maintenance is a managed loop: feature-flag cleanup and other upkeep run on scheduled, bounded cadences to avoid overwhelming CI and engineers, while outcomes feed labeled data back to skill authors.

## Questions And Answers
- Q: How does Uber prevent PII leakage and enforce policy at scale?
  A: Every model call routes through a single gateway that applies Spire identity, 20+ PII redaction types, and five specialized safety models, all within a strict 100 ms latency budget.

- Q: What was the biggest token-saving measure?
  A: Projecting 1,000+ MCP tools into a CLI so responses never enter the context window, plus dynamic Python script generation for heavy consumers, yielding >40 % fleet-wide token savings.

- Q: Why stop at draft PR instead of pushing straight to CI?
  A: Validating in the inner loop (e.g., simulator screenshots vs. Figma) catches issues earlier, reduces CI load, and provides human reviewers with a table of passed checks to increase confidence.

## Notable Details
- 70 % of PRs and 2× lines of code per engineer year-over-year attributed to agentic workflows.
- 2,500 skills in the marketplace, each lint-checked and auto-reviewed, with 20 k executions/day.
- 300 unique Cortana personas created in one month, with 20 k daily sessions across Slack, CLI, and web.
- Self-healing CI and shifted-left code review: outer-loop uses a powerful reasoning model; inner-loop uses a faster medium model.
- Maintenance loops run on low-traffic windows (e.g., Sundays) and cap diff volume to avoid Monday overload.

## Actionable Takeaways
- Centralize model access behind a single gateway to enforce identity, PII redaction, and safety within a strict latency SLA.
- Project tool responses outside the context window via CLI to cut token costs; consider dynamic script generation for heavy consumers.
- Build a unified context graph to replace scattered systems for ownership, dependencies, and design data.
- Stop autonomous agents at draft PR and validate in an inner loop (simulator vs. specs) before CI to reduce load and improve quality.
- Treat maintenance as a managed, bounded loop with scheduled runs and labeled-data feedback to improve skills.

## People, Companies, Tools, And Links Mentioned
- Uber
- Spire (SPIFFE)
- OpenAI
- Anthropic
- MCP (Model Context Protocol)
- Bazel
- Cortana (Uber’s AI assistant)
- Minion (Uber’s cloud coding agent)
- [Uday Kiran Medisetty on X](https://x.com/udaykiran)
- [Uday Kiran Medisetty on LinkedIn](https://www.linkedin.com/in/udaykiran/)
- [Adam Huda on X](https://x.com/hudaman)
- [Adam Huda on LinkedIn](https://www.linkedin.com/in/thinktopdown/)
- [Adam Huda’s website](https://adamhuda.com)

## Reading Priority

High – Uber’s production-grade agentic SDLC demonstrates concrete, large-scale infrastructure patterns and measurable gains (70 % PR share, 2× productivity, >40 % token savings) that are directly applicable to enterprise AI adoption.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/AI Infrastructure|AI Infrastructure]]
