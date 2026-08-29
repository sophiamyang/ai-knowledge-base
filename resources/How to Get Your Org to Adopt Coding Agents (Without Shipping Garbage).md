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
  - "Eyal Blum, Figma"
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
The best engineers resist AI agents the longest because they see every failure mode first, so the fastest path to adoption is to treat their objections as a roadmap for verification and safety.

## Short Summary
AI adoption in engineering organizations follows a three-act arc: early wins, painful failures, and then disciplined use with guardrails. At Figma, the most skilled engineers—who hold the most institutional context—are the last to adopt agents because they encounter every gap in verification and trust the tools the least. The solution is to let these skeptics define the roadmap for making agents safe, as their complaints directly map to missing validation layers.

Beyond trust, adoption creates friction: developer agency and job satisfaction can drop when coding turns into prompting, and communication swells with low-signal AI-generated text. Figma counters this with attention-aware conventions (e.g., human-written summaries atop AI-generated content) and by restoring craft through detailed planning, where engineers spend a week designing a plan that an agent then implements overnight.

## Featured Speakers
- Eyal Blum – Software Engineer at Figma

## Main Ideas
- The strongest engineers resist agents the longest because they carry undocumented institutional knowledge and see every failure mode first; their objections are a prioritized list of where verification is missing.
- Investing in verification (e.g., deterministic tests, linting, compiler checks) and shifting left—moving tasks from humans to agents—unlocks the most productivity, especially when successful agent behaviors are encoded into repeatable, token-efficient flows.
- Planning replaces prompting as the primary creative act: engineers regain agency and joy by spending a week crafting detailed, independently verifiable plans that agents then implement, often overnight.
- A testing pyramid for agents mirrors traditional testing: maximize deterministic checks (unit tests, linting), use agents for architectural reviews, and reserve human judgment for high-level functional validation.
- Attention-aware communication is critical: explicitly mark human-written vs. AI-generated content (e.g., PR descriptions start with a human summary) to preserve scarce human attention and signal quality.

## Questions And Answers
- **Why do the best engineers adopt agents last?**
  They hold the most context, see every failure mode first, and act as bottlenecks because they prevent bad outputs; their skepticism is a signal of missing verification, not resistance to change.

- **How can teams restore developer agency with agents?**
  Shift the creative work to planning: engineers design detailed, verifiable plans (with clear "why" and independent validation gates), then hand off implementation to agents, which restores craft and reduces prompt-and-wait fatigue.

- **What’s a practical way to manage AI-generated communication?**
  Adopt conventions like human-written summaries at the top of AI-generated content (e.g., PR descriptions), so readers know where to focus attention and what to treat as lower-signal.

## Notable Details
- Figma’s internal adoption is uneven: some teams are AI-forward while others remain skeptical, and all must coexist.
- Developer burnout rises when coding (a source of flow and pride) turns into a prompt-and-wait cycle.
- Documents and Slack messages have grown 3–4x in length without adding proportional value; marking AI vs. human content helps.
- Using Test-Driven Development (TDD) with agents—writing tests first, then asking the agent to write code to pass them—yields better results than writing code first and then tests.
- A single well-structured plan can replace 6 weeks of coding work, with the agent implementing 20+ PRs (10–100 lines each) overnight after a week of human planning and review.

## Actionable Takeaways
- Treat skepticism from top engineers as a roadmap: their complaints about agent failures are prioritized tasks for adding verification and guardrails.
- Encode successful agent behaviors into deterministic flows (e.g., tests, linting) to save tokens and time, and to ensure repeatability.
- Adopt attention-aware communication norms (e.g., human-written summaries atop AI text) to preserve signal and respect readers’ time.
- Restore developer agency by emphasizing planning over prompting: spend a week on a detailed, verifiable plan, then let the agent implement it.
- Start with low-friction, in-flow agent use (e.g., tagging an agent in Slack to close a loop) to normalize adoption before introducing complex workflows.

## People, Companies, Tools, And Links Mentioned
- Figma
- Playwright MCP
- [Eyal Blum’s LinkedIn](https://www.linkedin.com/in/eyalg/)

## Reading Priority

Medium – A practical, experience-driven look at the cultural and technical hurdles of adopting coding agents, with actionable patterns for verification, planning, and communication.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]]
- Speaker: [[people/eyal-blum|Eyal Blum]]
