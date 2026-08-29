---
id: "2aee6050e70fd05d"
title: "How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma"
aliases:
  - "How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Eyal Blum, Software Engineer at Figma"
url: "https://www.youtube.com/watch?v=5Bn0xro2ol8"
origin: "https://www.youtube.com/watch?v=5Bn0xro2ol8"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-how-to-get-your-org-to-adopt-coding-agents-without-shipping-garbage-eyal-blum-fi-2aee6050e70fd05d.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-how-to-get-your-org-to-adopt-coding-agents-without-shipping-garbage-eyal-blum-fi-2aee6050e70fd05d|How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma raw transcript]]

# How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma

Source: youtube
Original link: https://www.youtube.com/watch?v=5Bn0xro2ol8

## One-Sentence Takeaway
The fastest way to win over skeptical engineers is to treat their objections as a roadmap for verification and safety, then let them see the fixes make their own work easier.

## Short Summary
Adoption of coding agents at Figma follows a three-act pattern: early wins, painful failures, then disciplined guardrails. The best engineers resist longest because they carry undocumented context and see every failure mode first; their skepticism is a signal of missing verification. Agency loss and bloated communication are real costs, but can be mitigated by shifting from prompting to planning, encoding successful workflows into deterministic tests, and marking AI-generated text so readers can allocate scarce attention.

## Featured Speakers
- Eyal Blum, Software Engineer at Figma

## Main Ideas
- Adoption curves are uneven: early enthusiasts hit walls, then teams must add guardrails to reach reliable use; coexisting workflows require support without forcing uniformity.
- The strongest engineers adopt last because they hold the codebase together with mental duct tape and see every failure first; their objections map directly to missing verification.
- Shift from prompting to planning: spend a week crafting a detailed, verifiable plan, then let the agent implement overnight; this restores agency and accelerates review.
- Build a testing pyramid for agents: push as much as possible into deterministic checks (linters, compilers, unit tests), use agents for architectural standards, and reserve human review for functional correctness.
- Attention-aware communication: explicitly mark human-written vs. AI-generated text so readers can prioritize their limited attention.

## Questions And Answers
- **Why do the best engineers adopt agents last?**
  They carry institutional context nobody wrote down, see every failure mode first, and become bottlenecks; their skepticism is a prioritized list of where verification is missing.

- **How can planning replace prompting?**
  Write a detailed plan with a clear "why," break it into independently verifiable phases, and send it to the agent only after review; this restores craft and reduces drift.

- **What is the simplest cultural fix for bloated AI communication?**
  Start PR descriptions and messages with a human-written line, then add generated text below; readers know where to focus.

## Notable Details
- Plans often take a week to write and align across teams, then agents implement overnight; one example delivered six weeks of coding work in one week including review.
- A plan should be broken into PR-sized chunks; if a chunk feels too big to review without a coffee break, it is too big.
- Sending unmarked AI analysis to a senior skeptic was called out as sloppy; marking intent and authorship prevented repeat offenses.
- Tagging an agent in Slack to close a loop normalizes everyday use and lowers friction for hesitant teammates.

## Actionable Takeaways
- Treat skepticism as a roadmap: hand the strongest critics ownership of the verification and safety plan.
- Encode successful agent workflows into deterministic tests to save tokens and time.
- Adopt attention-aware communication: label human vs. AI text so readers can triage.
- Prefer planning over prompting: invest in detailed, verifiable plans and let agents execute.
- Start small in existing tools (e.g., tagging agents in Slack) to normalize use before introducing fancy workflows.

## People, Companies, Tools, And Links Mentioned
- [Figma](https://www.figma.com)
- Playwright MCP

## Reading Priority

Medium – A pragmatic, experience-backed playbook for enterprise adoption of coding agents, with concrete workflows and cultural practices.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]]
- Speaker: [[people/eyal-blum|Eyal Blum]]
