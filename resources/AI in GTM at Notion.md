---
id: "1202d499891d355f"
title: "AI in GTM at Notion — Flora Liu"
aliases:
  - "AI in GTM at Notion — Flora Liu"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Flora Liu – Engineer, Notion GTM Engineering"
url: "https://www.youtube.com/watch?v=L4I7WgiEquo"
origin: "https://www.youtube.com/watch?v=L4I7WgiEquo"
published: "2026-08-26"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-ai-in-gtm-at-notion-flora-liu-1202d499891d355f.md"
created: "2026-08-29"
tags:
  - "topic/enterprise-ai"
  - "topic/developer-tools"
  - "topic/product-development"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-ai-in-gtm-at-notion-flora-liu-1202d499891d355f|AI in GTM at Notion — Flora Liu raw transcript]]

# AI in GTM at Notion — Flora Liu

Source: youtube
Original link: https://www.youtube.com/watch?v=L4I7WgiEquo

## One-Sentence Takeaway
A unified GTM system that lets humans and agents operate on the same context layer—built around know, decide, act, and learn—reduces errors, speeds workflows, and lifts conversion rates.

## Short Summary
Notion’s GTM engineering team reframed a fragmented marketing-ops problem as a distributed-systems challenge: stitching Salesforce, Gong, Outreach, Snowflake, and a decade of meeting notes into a single decisioning substrate. The architecture collapses every workflow into four layers—context, decision, execution, and feedback—so both reps and agents read, write, and act on the same data without an AI veneer on top.

Early results show enterprise reps logging more qualified opportunities and users given context-aware recommendations 63 % more likely to advance, validating the thesis that a shared, programmable loop beats siloed automation.

## Featured Speakers
- Flora Liu – Engineer, Notion GTM Engineering

## Main Ideas
- GTM automation fails when it cannot ingest the unstructured notes (e.g., “champion left,” “blocked in legal”) that actually drive rep decisions; the solution is a single, trusted context layer that both humans and agents can read and update.
- The system is organized into four layers—Know (truth), Decide (next-best action), Act (execute safely), Learn (close the feedback loop)—with humans and agents operating on the same substrate to prevent drift.
- Agents are deliberately barred from direct customer contact; all external inputs (e.g., Contact Sales forms) are treated as untrusted, and reps remain in the loop for approval and judgment.
- Signals—internal or external customer events—are converted into durable Temporal workflows so that one malformed transcript or API failure cannot halt the entire pipeline.
- Build-versus-buy is resolved per layer: own the context layer (Notion) and rent commoditized services (Snowflake, DynamoDB, Temporal, Clay, email vendors).

## Questions And Answers
- **Why not let agents talk to customers?**
  Direct agent-to-customer communication breaks trust boundaries; untrusted inputs (e.g., web forms) must be mediated by humans who retain ownership of the relationship.

- **How do you prevent stale data from triggering bad actions?**
  Snowflake computes a daily (sometimes real-time) “truth” set of modeled entities; DynamoDB serves a denormalized, millisecond-queryable profile so agents and reps always operate on fresh context.

- **What early metrics validate the approach?**
  In 13 weeks, enterprise reps saw more qualified opportunities, and users receiving context-aware recommendations were 63 % more likely to take the next step.

## Notable Details
- Context layer: Snowflake → modeled entities (accounts, contacts, workspaces, eligibility, facts) → DynamoDB denormalized profiles keyed by the same IDs → Notion for human + agent consumption.
- Each signal spawns a Temporal workflow that orchestrates enrichment, web search, draft generation, scoring, and review; failures are retried and deduplicated without losing state.
- MEDDPICC fields (Metrics, Economic buyer, Decision criteria, Plan, Champion) are extracted from Gong transcripts and used to draft grounded follow-ups.
- Decision logs and engagement outcomes are wired back into the decision layer so the system can self-heal and improve routing.

## Actionable Takeaways
- Shadow your best reps first; encode only the most legible, repeated workflows to avoid baking in mediocre processes.
- Model GTM as primitives—entities, context, triggers, actions, eligibility rules—so the “alien” domain becomes engineerable.
- Design for agents as first-class operators (headless by default) on the same substrate as humans; otherwise the two systems will drift.
- Own the context layer (your proprietary data model and workflows) and rent everything else.
- Treat external inputs as untrusted and keep humans in the loop for any customer-facing action.

## People, Companies, Tools, And Links Mentioned
- Flora Liu
- Notion
- Ivan (Notion CEO)
- Salesforce
- Gong
- Outreach
- ZoomInfo
- Snowflake
- DynamoDB
- Temporal
- Clay
- [Flora Liu’s website](https://www.flofloliu.com/)
- [Flora Liu on Twitter](https://twitter.com/floppyliu)
- [Flora Liu on LinkedIn](https://www.linkedin.com/in/flofloliu/)

## Reading Priority

Medium – A concrete, early-stage case study showing how a shared human-agent substrate can unify GTM workflows and yield measurable gains.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Enterprise AI|Enterprise AI]], [[topics/Developer Tools|Developer Tools]], [[topics/Product Development|Product Development]]
- Speaker: [[people/flora-liu-engineer|Flora Liu – Engineer]]
