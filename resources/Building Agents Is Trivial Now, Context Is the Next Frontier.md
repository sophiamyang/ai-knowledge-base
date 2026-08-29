---
id: "7e5d62dfb2bc37ea"
title: "Building Agents Is Trivial Now, Context Is the Next Frontier — Jeff Ng, Unblocked"
aliases:
  - "Building Agents Is Trivial Now, Context Is the Next Frontier — Jeff Ng, Unblocked"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Jeff Ng, Founding Engineer, Unblocked"
url: "https://www.youtube.com/watch?v=HvMyYLTfvhg"
origin: "https://www.youtube.com/watch?v=HvMyYLTfvhg"
published: "2026-08-21"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-building-agents-is-trivial-now-context-is-the-next-frontier-jeff-ng-unblocked-7e5d62dfb2bc37ea.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/retrieval"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-building-agents-is-trivial-now-context-is-the-next-frontier-jeff-ng-unblocked-7e5d62dfb2bc37ea|Building Agents Is Trivial Now, Context Is the Next Frontier — Jeff Ng, Unblocked raw transcript]]

# Building Agents Is Trivial Now, Context Is the Next Frontier — Jeff Ng, Unblocked

Source: youtube
Original link: https://www.youtube.com/watch?v=HvMyYLTfvhg

## One-Sentence Takeaway
Building AI agents is now trivial, but their reliability hinges on access to reconciled, task-relevant context that current frameworks like MCP do not provide.

## Short Summary
Six months ago, deploying a production-grade agent required solving checkpointing, sandbox isolation, and observability—infrastructure taxes that cloud primitives and frameworks (e.g., Flue, Vercel Eve, Mastra) have since absorbed. Today, defining an agent reduces to selecting a model, instructions, tools, and a sandbox, but agents still fail silently when missing critical context (e.g., Slack threads, postmortems) that humans intuitively supply.

The core problem is that access (e.g., via MCP) is not understanding: agents receive raw, contradictory data and must reconcile it themselves, often poorly. A *context engine*—which synthesizes, ranks, and scopes organizational knowledge (docs, code, tickets, conversations) to an agent’s permissions—flips outcomes from repeating mistakes to preventing them.

## Featured Speakers
- Jeff Ng, Founding Engineer, Unblocked

## Main Ideas
- Agent deployment has shifted from infrastructure-heavy (checkpointing, sandboxes, observability) to a simple definition of model, instructions, tools, and sandbox, thanks to cloud primitives and frameworks.
- Agents fail when they lack *reconciled context*: even with access to code and tickets, missing cross-system knowledge (e.g., Slack discussions, postmortems) leads to confidently wrong decisions.
- MCP (Model Context Protocol) provides access to data but not understanding; it floods agents with raw, conflicting results, forcing ad-hoc reconciliation and increasing costs.
- A *context engine* addresses this by modeling organizational knowledge, resolving conflicts, and delivering synthesized, permission-scoped context that agents can act on directly.
- Without a context engine, background agents silently propagate errors (e.g., re-enabling a setting that previously caused an outage), whereas humans in the loop compensate with tribal knowledge.

## Questions And Answers
- **Why don’t local agent workflows suffer from missing context?**
  Humans act as the context layer, supplying missing facts, steering decisions, and catching errors in real time—knowledge that agents lack when deployed autonomously.

- **What’s the difference between MCP and a context engine?**
  MCP grants access to raw data (e.g., Slack, Linear, GitHub), but a context engine reconciles, ranks, and synthesizes that data into actionable understanding, respecting permissions and reducing noise.

- **How does a context engine change agent outcomes?**
  In Ng’s demo, the same agent initially recommended re-enabling a faulty setting (causing an outage) but, when grounded by a context engine, instead recommended *preventing* the outage by referencing the postmortem and Slack discussion.

## Notable Details
- Six months ago, building an agent required a team’s quarter to solve infrastructure taxes (checkpointing, sandbox isolation, observability), none of which improved agent capabilities.
- Cloudflare, Vercel, and AWS now provide primitives that frameworks (Flue, Vercel Eve, Mastra) use to abstract away plumbing, reducing agent definition to ~4 components.
- Demo: An agent enriching a Linear ticket about QA pipeline latency (3–4s vs. ~100ms) recommended re-enabling `async dispatch`—a change that had *previously caused an outage*—because it lacked access to the Slack thread and postmortem.
- Context engines connect docs, code, tickets, and conversations, then build a model of the organization to provide *grounded* context (reconciled, ranked, scoped) to agents.
- Use cases for context engines: issue enrichment, coding (hydrating agent plans), code review (PRs appear expert-reviewed), customer success/sales Q&A.

## Actionable Takeaways
- Audit agent failures for missing context (e.g., cross-system discussions, postmortems) before blaming the model or tools.
- Treat MCP as a data access layer, not a context solution; pair it with a synthesis layer to resolve conflicts and reduce token waste.
- Prioritize *grounded context* (synthesized, permission-scoped) over raw data access for autonomous agents in production.
- Explore context engines for high-stakes workflows (e.g., code review, incident response) where tribal knowledge is critical.

## People, Companies, Tools, And Links Mentioned
- Jeff Ng
- Unblocked ([getunblocked.com](https://getunblocked.com))
- Cloudflare
- Vercel
- AWS
- Flue
- Vercel Eve
- Mastra
- Linear
- MCP (Model Context Protocol)
- Claude Code
- Codex

## Reading Priority

Medium – A concrete, demo-backed argument that context—not model or tooling—is the bottleneck for reliable autonomous agents, with clear implications for enterprise deployments.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Retrieval|Retrieval]]
- Speaker: [[people/jeff-ng|Jeff Ng]]
