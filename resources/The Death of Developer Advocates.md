---
id: "e0a8f973b18ba293"
title: "The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph"
aliases:
  - "The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Stephanie Jarmak, Agent Advocate and Research Scientist at Sourcegraph"
url: "https://www.youtube.com/watch?v=Lrw0jqBNaw0"
origin: "https://www.youtube.com/watch?v=Lrw0jqBNaw0"
published: "2026-08-26"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-the-death-of-developer-advocates-stephanie-jarmak-sourcegraph-e0a8f973b18ba293.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/product-development"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-the-death-of-developer-advocates-stephanie-jarmak-sourcegraph-e0a8f973b18ba293|The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph raw transcript]]

# The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph

Source: youtube
Original link: https://www.youtube.com/watch?v=Lrw0jqBNaw0

## One-Sentence Takeaway
Developer advocacy must evolve to treat AI agents as a primary user and recommender, optimizing for their unique needs in discoverability, API clarity, and frictionless adoption.

## Short Summary
The core argument is that developer relations (DevRel) is not obsolete but must adapt to a new audience: AI agents. These agents now read docs, call APIs, encounter errors, and recommend tools, effectively becoming a critical user and influencer. Benchmarking reveals gaps in how tools are discovered and adopted by agents, such as mismatches between expected and actual API parameters, or failure to surface tools for specific pain points.

The shift requires rethinking enablement, community, and feedback loops to serve both human developers and agents. Practical steps include optimizing for "generative engine optimization" (GEO), ensuring fresh and machine-readable content, and reducing friction in adoption pathways.

## Featured Speakers
- Stephanie Jarmak, Agent Advocate and Research Scientist at Sourcegraph

## Main Ideas
- AI agents are now a distinct user segment for developer tools, acting as both direct users (reading docs, calling APIs) and recommenders (suggesting tools to humans). Their experience must be instrumented and optimized like any other user’s.
- Traditional DevRel principles (enablement, community, feedback) still apply, but the audience has expanded to include agents. This requires machine-readable content, agent-friendly APIs, and structured feedback from agent interactions.
- Benchmarking agent workflows (e.g., Sourcegraph’s CodeScaleBench) reveals friction points, such as agents burning turns on incorrect assumptions or failing to surface tools for specific use cases. These insights can drive product and content improvements.
- "Generative Engine Optimization" (GEO) is critical: stale or poorly structured content compounds against discoverability, as agents rely on real-time, authoritative sources. Freshness, clarity, and direct pain-point alignment improve recommendations.
- The "curb cut" analogy applies: optimizing for agents (e.g., clear APIs, minimal adoption friction) indirectly improves the experience for human developers, as both benefit from reduced complexity.

## Questions And Answers
- **How do agents currently fail to recommend tools?**
  Agents often miss surfacing tools for specific pain points (e.g., "breaking downstream services") unless content explicitly ties the tool to the problem. In one test, Sourcegraph was recommended 65% of the time for generic comparisons but 0% for a concrete pain-point prompt.

- **Why does stale content hurt discoverability?**
  Agents trained on outdated data (e.g., older models) may amplify obsolete information (e.g., pitching deprecated products like Cody). Fresh, authoritative content (e.g., LLMs.txt pages) helps override this noise.

- **What’s the role of MCP registries?**
  Agents and developers increasingly rely on marketplaces and registries (e.g., MCP) to discover tools. Being present in these ecosystems reduces friction and increases adoption likelihood.

## Notable Details
- Sourcegraph’s CodeScaleBench includes hundreds of lifecycle tasks to evaluate how agents perform with and without Sourcegraph’s code navigation tool. Traces revealed agents wasting turns on incorrect parameter assumptions (e.g., `read_line` vs. `start_line`).
- In a GEO experiment, Claude Sonnet 4 recommended Sourcegraph’s older product (Cody) more frequently than newer offerings, highlighting how stale training data and internet content compound discoverability issues.
- Agents prefer structured content like charts, FAQs, and up-to-date examples. They also favor tools with minimal adoption friction (e.g., no multi-step demos or sales calls).
- The talk itself was designed to be "agent-legible," with QR codes and toy repos provided for agents to explore, reinforcing the practical focus on agent accessibility.

## Actionable Takeaways
- Audit your tool’s agent experience by running a coding agent against your docs and analyzing the traces for friction points (e.g., unclear APIs, missing error handling).
- Prioritize GEO: update content to explicitly tie your tool to specific pain points, use structured formats (charts, FAQs), and ensure real-time accuracy (e.g., LLMs.txt pages).
- Reduce adoption friction: ensure your tool is listed in agent marketplaces (e.g., MCP registries) and requires minimal steps to integrate.
- Treat agent optimization as a "curb cut": improvements for agents (e.g., clearer APIs, better docs) will likely benefit human developers too.
- Experiment with agent-driven feedback loops to identify gaps in discoverability or usability, then iterate on content and product design.

## People, Companies, Tools, And Links Mentioned
- [Stephanie Jarmak](https://x.com/sgjarmak)
- [Stephanie Jarmak’s website](https://www.sjarmak.ai/)
- [Stephanie Jarmak on LinkedIn](https://www.linkedin.com/in/stephanie-jarmak)
- Sourcegraph
- Sourcegraph Cody
- CodeScaleBench
- Claude (Anthropic)
- Claude Sonnet 4
- Claude 4.6
- MCP (Model Context Protocol) registries
- LLMs.txt

## Reading Priority

Medium – A practical, evidence-backed argument for adapting DevRel to the agent era, with concrete examples and actionable steps for developer tooling teams.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Product Development|Product Development]]
- Speaker: [[people/stephanie-jarmak|Stephanie Jarmak]]
