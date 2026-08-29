---
id: "65d4189aaca47d70"
title: "The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp"
aliases:
  - "The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Arman Vaziri, leads product and sales-led growth engineering at Ramp"
url: "https://www.youtube.com/watch?v=VjEP0xqTUI0"
origin: "https://www.youtube.com/watch?v=VjEP0xqTUI0"
published: "2026-08-26"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-the-building-blocks-of-gtm-orchestration-arman-vaziri-ramp-65d4189aaca47d70.md"
created: "2026-08-29"
tags:
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/product-development"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-the-building-blocks-of-gtm-orchestration-arman-vaziri-ramp-65d4189aaca47d70|The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp raw transcript]]

# The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp

Source: youtube
Original link: https://www.youtube.com/watch?v=VjEP0xqTUI0

## One-Sentence Takeaway
Go-to-market orchestration at scale requires a unified customer data platform, durable automation, and reusable agent skills to turn intent into multi-channel execution without months of coordination overhead.

## Short Summary

The core challenge in GTM is not generating ideas but operationalizing them: pulling audiences, creating enablement materials, and aligning teams across channels. Ramp addressed this by first building an internal customer data platform (CDP) that unifies CRM, product, enrichment, and interaction data—both structured and unstructured—into a consistent, searchable substrate.

On top of this foundation, they layer durable, resumable workflows (via Temporal) and a skill library that lets teams customize agent outputs, starting with high-impact use cases like pre-meeting briefs and then scaling horizontally. The result is the ability to describe a campaign (e.g., targeting golfers at construction firms) and automatically generate audiences, copy, creatives, and in-app nudges across channels.

## Featured Speakers
- Arman Vaziri, leads product and sales-led growth engineering at Ramp

## Main Ideas
- The primary bottleneck in GTM is not ideation but the operational cost of turning ideas into coordinated, multi-channel execution.
- A unified internal customer data platform (CDP) is foundational: it integrates CRM, product, enrichment, buying signals, and interaction data (including unstructured notes/transcripts) with referential integrity and real-time event streaming.
- Durable execution threads (via Temporal) treat each workflow as a resumable sequence of tool/model calls, avoiding reprocessing if workers fail and enabling human-in-the-loop pauses.
- A skill library allows teams to define their own output formats (e.g., meeting briefs), which drove adoption by making agents adaptable to individual preferences.
- The stack compounds: vertical solutions (e.g., meeting prep) inform horizontal scaling (e.g., outbound, post-meeting follow-ups), while employee-facing tools (GTM MCP) surface the same capabilities for custom agent building.

## Questions And Answers
- **Q: How should a smaller team start building this?**
  A: Begin with narrow, high-impact automations (e.g., personalized outbound copy) to solve specific problems, then iteratively connect these vertical solutions. Avoid spending a year designing a perfect architecture; learn by shipping and scaling incrementally.

- **Q: How do you handle multi-entity mapping (e.g., one email tied to multiple businesses)?**
  A: Treat it as a fuzzy matching problem: persist mappings (e.g., attendee emails to accounts) so downstream consumers don’t recompute them, reducing redundancy and errors.

## Notable Details
- The CDP uses Postgres for transactional guarantees and referential integrity, Kafka for real-time events, and embeddings (via Turbopuffer) for unstructured data search.
- Pre-meeting briefs aggregate usage vitals, open tickets, agendas, and customer context, requiring email-to-account mapping to handle overlapping business affiliations.
- Agents combine vector, attribute, and keyword search to pull scoped information (e.g., per account) without loading full raw corpora into context.
- Ramp’s GTM MCP exposes the same tools/skills to employees, enabling them to build custom agents; their prompts and workflows often reveal new use cases to productionize.

## Actionable Takeaways
- Start with a single high-value automation (e.g., meeting prep or outbound personalization) to prove the pattern before scaling.
- Invest in a CDP that unifies structured and unstructured data with clear referential integrity—this is the substrate for all downstream orchestration.
- Use durable execution frameworks (e.g., Temporal) to handle long-running, resumable workflows with human checkpoints.
- Build a skill library to let teams customize agent outputs, increasing adoption and flexibility.
- Expose internal tools to employees via an MCP-like interface to surface new use cases and accelerate productionization.

## People, Companies, Tools, And Links Mentioned
- Arman Vaziri
- Ramp
- [Temporal](https://temporal.io/)
- Turbopuffer
- Kafka
- Postgres
- dbt
- Snowflake

## Reading Priority

Medium – A concrete, technical breakdown of how a high-growth company operationalizes GTM with data and agents, offering actionable patterns for similar challenges.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Product Development|Product Development]]
- Speaker: [[people/arman-vaziri|Arman Vaziri]]
