---
id: "27aa8c4009cd8316"
title: "How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked"
aliases:
  - "How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Peter Werry, Unblocked"
url: "https://www.youtube.com/watch?v=qdAkxLoYNI8"
origin: "https://www.youtube.com/watch?v=qdAkxLoYNI8"
published: "2026-08-27"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-how-to-generate-mergeable-code-with-a-context-engine-peter-werry-unblocked-27aa8c4009cd8316.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/retrieval"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-how-to-generate-mergeable-code-with-a-context-engine-peter-werry-unblocked-27aa8c4009cd8316|How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked raw transcript]]

# How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked

Source: youtube
Original link: https://www.youtube.com/watch?v=qdAkxLoYNI8

## One-Sentence Takeaway
Agents fail when they treat codebases like radiologists’ “satisfaction of search,” so a context engine that surfaces intent, conventions, and past decisions is required for reliable, compounding automation.

## Short Summary
Agents without persistent context behave like new hires who must rediscover build, test, and deploy workflows on every task, leading to wrong assumptions and costly loops. A context engine solves this by distilling organizational knowledge—Slack threads, PRs, architecture docs—into task-specific, citable answers that cut token use and prevent cascading errors.

The demos show a generated architecture diagram with sources, a 2× speed/cost improvement on an optimization plan, and a review agent that boosts senior engineers’ comments and traces a drop in flagged issues back to a Slack discussion.

## Featured Speakers
- Peter Werry, Unblocked

## Main Ideas
- Agents suffer from “satisfaction of search”: they find one plausible answer and stop, missing other relevant context that would change the outcome.
- A million-token context window is insufficient because the full organizational context does not fit and the agent gets distracted, wasting tokens and time.
- A context engine distills intent, conventions, and past decisions from Slack, PRs, docs, and code into task-specific, citable answers that agents can act on without rediscovering the codebase each time.
- The compounding value is preventing loops: wrong early assumptions cascade into later steps, requiring rework; a context engine reduces these loops more than it saves on any single task.
- Review agents can use the same context to surface senior engineers’ past comments and correlate code changes with external discussions (e.g., Slack) to explain behavior shifts.

## Questions And Answers
- **Why not just dump the whole codebase and docs into the context window?**
  It exceeds token limits and distracts the agent with irrelevant details, breaking task-specific flow and wasting tokens.

- **How does the context engine cut costs and time?**
  It pre-distills the right context, so the agent avoids discovery loops and wrong assumptions; in the demo, an optimization plan cost under $1 and ~1 minute with the engine vs. ~2× both without.

## Notable Details
- Demo: asking about the Sourcemark Engine returned a generated architecture diagram with attached sources for human verification.
- Demo: the same optimization plan in Claude Code cost <$1 and ~1 minute with the context engine vs. ~2× time and cost without.
- Review agent boosts comments by reviewer seniority and traced a drop in flagged issues to a Slack thread explaining a model behavior change.
- Open-source tools: a query engine over GitHub history and an engineering social graph that visualizes review coverage and expertise clusters.

## Actionable Takeaways
- Audit where agents loop due to missing context; these are the highest-leverage places to introduce a context engine.
- Surface sources with every agent answer to build trust and enable human verification.
- Use seniority or expertise signals to weight review comments and other organizational knowledge.
- Watch for compounding failures: early wrong assumptions in agent tasks often cascade; measure rework, not just first-task speed.

## People, Companies, Tools, And Links Mentioned
- [Unblocked](https://getunblocked.com)
- Claude Code
- Tariq (Claude Code)
- Richie (Unblocked, senior engineer)
- Brandon (Unblocked)
- Document Query Engine (open source)
- Engineering Social Graph (open source)
- Context Engine Simulator

## Reading Priority

Medium – A concrete, demo-backed argument for why coding agents need curated context, with measurable speed/cost gains and open-source tools to experiment with.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Retrieval|Retrieval]]
- Speaker: [[people/peter-werry|Peter Werry]]
