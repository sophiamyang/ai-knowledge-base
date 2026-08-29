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
AI-native organizations must treat skills as first-class, governed assets to avoid technical debt, ensure deterministic workflows, and scale know-how across teams.

## Short Summary
Skills—reusable, composable units of know-how—are where an organization’s actual workflow logic resides, yet most teams build, share, and govern them poorly. Ungoverned skills lead to duplication, decaying quality, security risks, and non-deterministic outcomes, mirroring the technical debt seen in unmanaged microservices.

The solution is a centralized skills platform with cataloging, versioning, access control, and ownership, paired with governance that spans architecture, infrastructure, and security. Without this, even well-designed agentic workflows degrade as models evolve and teams diverge.

## Featured Speakers
- Imad Touil, Distinguished Engineer at QuantumBlack

## Main Ideas
- Skills encapsulate an organization’s executable know-how; if unstructured, workflows become non-deterministic and hard to maintain.
- Ungoverned skills create technical debt: duplication across teams, quality decay as models change, undiscoverable assets, and security risks from unvetted scripts.
- Skills should be designed like microservices: reusable, modular, discoverable, portable, specialized, composable, consistent, and cost-efficient (via progressive disclosure to reduce token usage).
- Governance requires a centralized platform with a searchable catalog, dependency/versioning management, access controls, and named owners across domains (architecture, infra, security).
- Workflows are harness blueprints, and skills are the critical component that determines their reliability; the same governance principles should extend to entire workflows.

## Questions And Answers
**Why do skills improve agent outcomes?**
Skills provide deterministic, task-specific logic that outperforms ad-hoc prompting, especially for complex or regulated tasks (e.g., GDPR compliance, data retention policies).

**What happens without skills governance?**
Teams duplicate effort, quality degrades as models evolve, skills become undiscoverable, and security risks emerge from unchecked scripts or prompt injection.

**How should organizations start?**
Enable individuals to create/test skills, then centralize them in a governed catalog with metadata, versioning, and access controls, while assigning domain owners.

## Notable Details
- Skills adoption rose rapidly: Anthropic published the first skills article 8 months prior, followed by an open standard adopted by most agent harnesses within 2 months.
- Benchmarks show skills improve outcomes for tasks like software engineering and cybersecurity compared to model-only approaches.
- A simulation of 15 teams over 6 months demonstrated that governed skills reduce duplication, improve quality/security, and lower costs by reusing centralized assets.
- Skills can embed scripts, making them a supply-chain risk if pulled from public registries without security checks.
- Skills registries and evaluation tools (e.g., linting against best practices) are emerging, with auto-evolving skills as a next frontier.

## Actionable Takeaways
- Audit existing skills: identify duplication, ownership gaps, and security risks.
- Build a centralized skills catalog with metadata, versioning, and access controls, modeled after internal developer portals (IDPs).
- Assign domain owners (architecture, infra, security) to govern skill design, dependencies, and lifecycle.
- Evaluate skills against best practices (e.g., Anthropic’s guidelines) and retest them as models update.
- Extend governance to workflows, treating them as composable assets in a marketplace.

## People, Companies, Tools, And Links Mentioned
- Imad Touil
- QuantumBlack
- [Anthropic](https://www.anthropic.com)
- [Claude Code](https://claude.ai/code)
- [Cursor](https://cursor.com)
- GDPR

## Reading Priority

Medium – A concrete, experience-backed framework for scaling AI-native teams, with actionable parallels to microservices governance.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Product Development|Product Development]]
- Speaker: [[people/imad-touil|Imad Touil]]
