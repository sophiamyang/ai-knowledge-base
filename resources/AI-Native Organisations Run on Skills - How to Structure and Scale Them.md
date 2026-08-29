---
id: "b15d3a7b59b448e1"
title: "AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack"
aliases:
  - "AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Imad Touil, Distinguished Engineer at QuantumBlack"
url: "https://www.youtube.com/watch?v=M05vON8i0aI"
origin: "https://www.youtube.com/watch?v=M05vON8i0aI"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-ai-native-organisations-run-on-skills-how-to-structure-and-scale-them-imad-touil-b15d3a7b59b448e1.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/product-development"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-ai-native-organisations-run-on-skills-how-to-structure-and-scale-them-imad-touil-b15d3a7b59b448e1|AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack raw transcript]]

# AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack

Source: youtube
Original link: https://www.youtube.com/watch?v=M05vON8i0aI

## One-Sentence Takeaway
AI-native organizations must treat skills as first-class, governed assets—like microservices—to avoid technical debt, ensure determinism, and scale workflows securely and efficiently.

## Short Summary
Skills are the executable units where an organization’s know-how resides, yet most teams build, share, and govern them poorly. Without structured catalogs, versioning, access controls, and ownership, skills duplicate, degrade in quality, and introduce security risks, undermining workflow determinism and productivity.

The solution borrows from microservices: a centralized platform with metadata, dependencies, versioning, and domain-driven governance to make skills discoverable, composable, and maintainable. This approach reduces token costs via progressive disclosure, improves auditability (e.g., regulatory compliance), and prevents supply-chain risks from unvetted public skills.

## Featured Speakers
- Imad Touil, Distinguished Engineer at QuantumBlack

## Main Ideas
- Skills are the critical layer where organizational know-how becomes executable; unstructured skills break workflow determinism.
- Ungoverned skills create technical debt: duplication, quality decay (as models evolve), poor discoverability, unclear ownership, and security risks (e.g., prompt injection in scripts).
- A centralized skills platform must provide a searchable catalog with metadata, dependencies, versioning, access control, and evaluation/observability—mirroring microservice governance.
- Progressive disclosure of skills reduces token costs by injecting only the necessary skills into the context window at the right time.
- Workflows are "harness blueprints" that shape agent behavior; skills are their most valuable component, while hooks, sub-agents, and MCP servers are secondary.

## Questions And Answers
**Q: Why do skills improve agent outcomes more than raw model capabilities?**
A: Skills enforce deterministic behavior for specific tasks; benchmarks (e.g., SkillsBench) show higher-quality outputs when skills are applied vs. unaided model runs.

**Q: How does governance prevent skill duplication?**
A: A centralized catalog with search and versioning lets agents automatically pull existing skills, reducing redundant development across teams.

**Q: What’s the security risk of ungoverned skills?**
A: Skills may contain scripts or prompts vulnerable to injection; without security pipelines, pulling public skills introduces supply-chain risks.

## Notable Details
- Skills adoption timeline: Anthropic published the first skills article ~8 months prior; an open standard emerged 2 months later, with widespread harness adoption by February.
- SkillsBench results: Models performed well on software engineering/cybersecurity tasks without skills, but outcomes improved significantly with deterministic skills.
- Simulation of 15 teams over 6 months showed ungoverned skills led to high duplication, variable quality/security, and higher costs; governance reduced these issues.
- Example: A "data retention policy" skill composes with GDPR rules, disclosure standards, and filing templates to auto-generate audit trails in regulatory workflows.
- Skills are portable across harnesses (e.g., Claude Code to Cursor) due to standardized formats.

## Actionable Takeaways
- Audit existing skills for duplication, ownership, and security gaps; prioritize high-impact domains (e.g., compliance, data handling).
- Build a centralized skills platform with metadata, versioning, access control, and evaluation pipelines—leveraging existing IDP (Internal Developer Portal) tools.
- Design skills to be specialized, composable, and cost-efficient (e.g., progressive disclosure to minimize token usage).
- Extend governance to entire workflows, not just skills, to standardize and reuse end-to-end processes.
- Explore emerging capabilities: skills registries, static linting for skill quality, and auto-evolving skills with guardrails.

## People, Companies, Tools, And Links Mentioned
- Imad Touil
- QuantumBlack
- Anthropic
- [SkillsBench](https://www.youtube.com/watch?v=M05vON8i0aI) (mentioned in context)
- Claude Code
- Cursor
- Backstage (Internal Developer Portal)
- MCP (Model Context Protocol)

## Reading Priority

High – This talk offers a concrete, novel framework for scaling AI agents in enterprises, backed by benchmarks, architectural patterns, and actionable governance practices.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Product Development|Product Development]]
- Speaker: [[people/imad-touil|Imad Touil]]
