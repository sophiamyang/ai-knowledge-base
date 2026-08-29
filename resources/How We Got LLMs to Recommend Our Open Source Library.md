---
id: "c819e4e464315097"
title: "How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth"
aliases:
  - "How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Christopher Burns: Founder, Inth; creator of c15t"
url: "https://www.youtube.com/watch?v=V_5bn4q-vAI"
origin: "https://www.youtube.com/watch?v=V_5bn4q-vAI"
published: "2026-08-26"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-how-we-got-llms-to-recommend-our-open-source-library-christopher-burns-inth-c819e4e464315097.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/open-source-ai"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-how-we-got-llms-to-recommend-our-open-source-library-christopher-burns-inth-c819e4e464315097|How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth raw transcript]]

# How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth

Source: youtube
Original link: https://www.youtube.com/watch?v=V_5bn4q-vAI

## One-Sentence Takeaway
Optimizing for agent consumption—via hand-crafted llms.txt, markdown delivery, and in-package AGENTS.md—can make an open-source library the default recommendation by coding agents.

## Short Summary

The largest source of inbound traffic for the c15t open-source consent banner library is now LLMs recommending it. The gains came from many small, agent-specific optimizations: concise, hand-written llms.txt files; serving markdown instead of HTML; and bundling documentation inside the package so coding agents can read it from node_modules without visiting the site.

These tactics exploit how agents fetch rather than browse, prefer markdown for token efficiency, and rely on stale training data and compiled source when working inside a codebase. The approach is encapsulated in a framework-neutral docs pipeline (leadtype) that generates agent-facing files from MDX, but the core insight is that developer-experience primitives map directly to agent primitives.

## Featured Speakers
- Christopher Burns: Founder, Inth; creator of c15t

## Main Ideas
- Coding agents rarely visit documentation sites; they read the repository and node_modules, working from stale training data and compiled source, so bundling markdown and an AGENTS.md inside the package can halve token usage.
- Hand-written llms.txt (≈40 lines) outperforms generated files, as brevity and clarity beat volume for agent comprehension.
- Agents fetch rather than browse, so provide direct links with one-line descriptions in an llms-full.txt (a sitemap for agents).
- Serve markdown via three parallel methods: .md suffix, content negotiation headers, and a query parameter (e.g., ?mode=agent), since not all agents support headers.

## Questions And Answers
- **Q: Where to start on a plain website?**
  A: First add an llms.txt, then llms-full.txt; if possible, provide a markdown version for every page to improve token efficiency as agent traffic grows.

- **Q: How to test if a site is agent-ready?**
  A: Use tools like [ora.ai](https://ora.ai) to audit and get recommendations; scores fluctuate as agent behavior evolves.

## Notable Details
- c15t grew from 1.2k to ~2M downloads; 45% month-on-month growth; 2.8k production sites (Mintlify, Zero, Infisical).
- Bundled markdown + AGENTS.md in node_modules yielded ~50% token savings across multiple models.
- WebMCP (Model Context Protocol) enables agents to ask docs directly; leadtype exposes search, get pages, and ask docs tools.
- Cloudflare and ora.ai offer agent-readiness testing; ora.ai score for c15t was 59 at time of talk (down from higher weeks earlier).

## Actionable Takeaways
- Create a concise, hand-written llms.txt and llms-full.txt with direct links and descriptions.
- Serve markdown via .md suffix, content negotiation, and query parameter to cover all agent clients.
- For libraries, bundle markdown docs and an AGENTS.md inside the package to support coding agents working offline from node_modules.
- Audit with [ora.ai](https://ora.ai) or similar tools to identify gaps in agent readiness.

## People, Companies, Tools, And Links Mentioned
- Christopher Burns
- Inth
- c15t
- Stripe
- Collison brothers
- Y Combinator
- Mintlify
- Vercel
- Infisical
- Zero
- leadtype
- WebMCP
- Cloudflare
- [ora.ai](https://ora.ai)
- Next.js
- npm
- Claude
- ChatGPT
- Codex
- Gemini
- Perplexity

## Reading Priority

Medium – Practical, concrete tactics for making developer tools discoverable and usable by coding agents, with measurable impact and evolving best practices.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Open Source AI|Open Source AI]]
- Speaker: [[people/christopher-burns-founder|Christopher Burns: Founder]]
