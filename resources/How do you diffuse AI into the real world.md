---
id: "a5a09ea8091744d8"
title: "How do you diffuse AI into the real world? — Varun Shenoy, Long Lake"
aliases:
  - "How do you diffuse AI into the real world? — Varun Shenoy, Long Lake"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Varun Shenoy, Cofounder, Long Lake"
url: "https://www.youtube.com/watch?v=B0fjR3yaZFU"
origin: "https://www.youtube.com/watch?v=B0fjR3yaZFU"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-how-do-you-diffuse-ai-into-the-real-world-varun-shenoy-long-lake-a5a09ea8091744d8.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/enterprise-ai"
  - "topic/model-evaluation"
  - "topic/product-development"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-how-do-you-diffuse-ai-into-the-real-world-varun-shenoy-long-lake-a5a09ea8091744d8|How do you diffuse AI into the real world? — Varun Shenoy, Long Lake raw transcript]]

# How do you diffuse AI into the real world? — Varun Shenoy, Long Lake

Source: youtube
Original link: https://www.youtube.com/watch?v=B0fjR3yaZFU

## One-Sentence Takeaway
Diffusing AI into real-world services requires owning the operations, earning autonomy incrementally, and codesigning solutions in person—not just shipping models.

## Short Summary
AI demos impress, but real deployment in services businesses (property management, HR, travel) lags because diffusion is slow and requires process overhauls, like electricity in factories. Long Lake acquires and operates these businesses, so they bear the cost of failure and can iterate on agents that climb from copilots to coworkers.

The core challenge is building asynchronous agents for knowledge work that isn’t parallelized like coding, using real-world traces and ground truth (e.g., “did the roof get fixed?”) to create meaningful evals and continual learning loops. Codesign only works in person—embed in workflows, show up at trade shows, and engage users directly.

## Featured Speakers
- Varun Shenoy, Cofounder, Long Lake

## Main Ideas
- **Diffusion is the bottleneck**: Like electricity in factories, AI adoption in services requires replacing existing workflows and retraining people, not just better models.
- **Own the outcome**: By acquiring and operating businesses, Long Lake aligns incentives—when AI fails, the cost is internal, accelerating iteration and accountability.
- **Autonomy must be earned**: Agents should progress from copilots to coworkers incrementally, as user trust and model capability allow; jumping straight to full autonomy rarely works.
- **Asynchronous agents for services are unsolved**: Unlike coding (where parallel sandboxes work), knowledge work is serial and lacks clear async patterns; this is a key frontier.
- **Real-world traces enable real evals**: Ground truth from operations (e.g., roof repaired, books closed) creates actionable feedback loops, turning hill-climbing benchmarks into regression tests over time.

## Questions And Answers
- **Q: Why don’t services businesses use AI yet?**
  A: Valuable tasks (e.g., closing books with missing receipts, coordinating roof repairs) aren’t on the internet, and workflows are serial, not parallel like coding. Models lack the data and the process integration.

- **Q: How do you build better agents for these tasks?**
  A: Generate rich traces from real work (tool calls, hiccups, outcomes), use them for evals and post-training on out-of-distribution data, and customize per company, user, and client.

- **Q: How do you drive initial adoption?**
  A: Codesign in person—embed tools in existing systems (Excel, ERP), attend conferences, and engage users directly; usage and improvement are a single loop.

## Notable Details
- Long Lake has acquired 35 services businesses (property management, architecture, HR) and took American Express Global Business Travel private for $6.3B.
- Their team is ~40 people, over half in technology, with backgrounds from Palantir, Ramp, Glean, Blackstone, and HIG.
- Engineers parallelize work (e.g., launching 10 jobs), but services workers (e.g., processing emails) do not—this is a key gap for async agents.
- Traces capture implicit feedback (e.g., diffs between AI-generated data and final submissions) and explicit feedback (thumbs up/down, notes).
- Continual learning and enablement must be unified: more usage → better agents → more usage.

## Actionable Takeaways
- Start with copilots, not coworkers—earn autonomy incrementally in real workflows.
- Focus on tasks with clear ground truth (e.g., “was the roof fixed?”) to build meaningful evals.
- Codesign in person: embed tools in existing systems and engage users directly to reduce adoption friction.
- Treat continual learning and enablement as one loop—usage drives improvement, which drives more usage.
- For services, async agents require new patterns—parallelization isn’t natural, so experiment with workflow-specific solutions.

## People, Companies, Tools, And Links Mentioned
- [Varun Shenoy](https://varunshenoy.com)
- [Varun Shenoy on X](https://x.com/varunshenoy_)
- Long Lake
- Elad Gil
- General Catalyst
- Alpha Wave
- American Express Global Business Travel
- Palantir
- Ramp
- Glean
- Blackstone
- HIG
- Edison’s Pearl Street Station
- Ford
- Jensen Huang (NVIDIA)
- Claude Code
- Codex
- Claude Cowork
- MCP (Model Context Protocol)

## Reading Priority

High – A rare, concrete look at the operational and cultural barriers to AI adoption in services, with actionable insights from a practitioner owning the outcomes.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Model Evaluation|Model Evaluation]], [[topics/Product Development|Product Development]]
- Speaker: [[people/varun-shenoy|Varun Shenoy]]
