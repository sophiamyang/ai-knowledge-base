---
id: "19d6a94fb2ff03dc"
title: "FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft"
aliases:
  - "FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Tisha Chawla, Microsoft"
  - "Susheem Koul, Microsoft"
url: "https://www.youtube.com/watch?v=GJX19pNhmSw"
origin: "https://www.youtube.com/watch?v=GJX19pNhmSw"
published: "2026-08-22"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-finops-for-ai-agents-who-spent-all-the-tokens-tisha-chawla-susheem-koul-microsof-19d6a94fb2ff03dc.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/model-inference"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-finops-for-ai-agents-who-spent-all-the-tokens-tisha-chawla-susheem-koul-microsof-19d6a94fb2ff03dc|FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft raw transcript]]

# FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft

Source: youtube
Original link: https://www.youtube.com/watch?v=GJX19pNhmSw

## One-Sentence Takeaway
Run-aware token governance for AI agents can cut average spend by ~78% while raising completion rates from 67% to 96% by steering rather than halting runs.

## Short Summary
AI agent workflows often incur unpredictable costs due to unbounded model calls, with no control plane at the code-model boundary. Existing tools (e.g., gateways) only cap or route requests, failing to address run-level behaviors like loops, sub-agent spawning, or context growth.

The proposed TokenOps system instruments agent runs, attributes costs, and enforces budgets via *steer* (e.g., injecting succinctness prompts) before resorting to *halt* (circuit-breaking). Benchmarks on open-source repos show dramatic spend reduction and higher completion rates compared to throttling, with a policy catalog targeting common failure modes (context bloat, tool output, loops).

## Featured Speakers
- Tisha Chawla, Microsoft
- Susheem Koul, Microsoft

## Main Ideas
- **Control gap**: Prior software eras (SaaS, cloud) evolved control surfaces (usage caps, autoscaling), but agentic workflows lack governance at the *code-model call boundary*, where costs originate.
- **Run-aware governance**: TokenOps tracks and attributes token spend per run/segment, enabling policies that act *within* the run (e.g., compaction, caching) rather than only at request gates.
- **Steer over halt**: Cost guards monitor budget consumption *and velocity*; when overruns are predicted, they inject instructions (e.g., "be succinct") to reduce spend without killing the run, improving completion rates.
- **Out-of-band design**: Non-invasive instrumentation via boundary annotations preserves existing code, while a governor restricts control-plane actions to developer-approved interventions.

## Questions And Answers
- **Q: How does TokenOps differ from model gateways?**
  Gateways cap/downgrade requests, but cannot control run-level behaviors (loops, context growth). TokenOps operates at the agent run layer, steering behavior before halting.

- **Q: What’s the impact of steering vs. throttling?**
  Throttling kills runs to cut costs, reducing completion rates. Steering reduces spend while preserving ~96% completion (vs. 67% with throttling).

- **Q: How are policies enforced safely?**
  A governor limits control-plane actions to a pre-approved list (e.g., inject, mutate), preventing arbitrary interference with agent logic.

## Notable Details
- Benchmark results: **78% average spend reduction** and **67% → 96% completion uplift** on BrowserUse and MetaGPT repos with full policy suite.
- Policy catalog covers spend management, context compaction, tool output reduction, loop detection, and progress detection.
- Preview mode allows testing policies without enforcement, easing production adoption.
- Future roadmap: Self-learning module to analyze ledger data, propose new policies, and refine existing parameters.

## Actionable Takeaways
- Audit agent workflows for unbounded loops, context growth, or excessive tool calls—primary targets for steering policies.
- Instrument runs with boundary annotations to attribute costs before enforcing budgets.
- Prioritize *steer* actions (e.g., output truncation, caching) over *halt* to balance cost and completion.
- Start with preview mode to validate policies before enabling enforcement in production.

## People, Companies, Tools, And Links Mentioned
- Microsoft
- [TokenOps public wiki](https://www.youtube.com/watch?v=GJX19pNhmSw) (QR code referenced)
- BrowserUse (open-source repo)
- MetaGPT (open-source repo)
- LiteLLM
- Portkey
- Cloudflare
- LangChain
- LangSmith

## Reading Priority

High – Introduces a novel, production-tested approach to agent cost governance with quantified benchmarks and a clear technical design.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Model Inference|Model Inference]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]]
- Speakers: [[people/tisha-chawla|Tisha Chawla]], [[people/susheem-koul|Susheem Koul]]
