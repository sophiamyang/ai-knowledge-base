---
id: "904e02e9108c023d"
title: "Parallel’s Parag Agrawal: Building a New Web for AI Agents"
aliases:
  - "Parallel’s Parag Agrawal: Building a New Web for AI Agents"
type: "resource"
source: "podcast"
source_name: "Training Data"
content_type: "podcast"
speakers:
  - "Parag Agrawal, Founder and CEO, Parallel Web Systems"
url: "https://pscrb.fm/rss/p/traffic.megaphone.fm/CPUAI4289055692.mp3"
origin: "https://feeds.megaphone.fm/trainingdata"
published: "2026-08-25"
transcript_method: "mistral_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-28-podcast-parallel-s-parag-agrawal-building-a-new-web-for-ai-agents-904e02e9108c023d.md"
created: "2026-08-28"
tags:
  - "topic/ai-agents"
  - "topic/developer-tools"
  - "topic/web-platform"
  - "topic/ai-infrastructure"
---

Raw transcript: [[raw_transcripts/2026-08-28-podcast-parallel-s-parag-agrawal-building-a-new-web-for-ai-agents-904e02e9108c023d|Parallel’s Parag Agrawal: Building a New Web for AI Agents raw transcript]]

# Parallel’s Parag Agrawal: Building a New Web for AI Agents

Source: podcast
Original link: https://pscrb.fm/rss/p/traffic.megaphone.fm/CPUAI4289055692.mp3

## One-Sentence Takeaway
Agents will query the web at orders of magnitude beyond human volume, requiring new search infrastructure and economic models that align incentives between content owners and AI systems.

## Short Summary
Parallel Web Systems argues that human click data is a poor signal for agentic search, and instead trains on agent feedback to optimize for quality, cost, and latency. The company prioritized shipping a search agent over a search engine to incrementally build its index, and its Turbo product now delivers agentic search in 200 milliseconds.

The core economic challenge is that ad-supported web models break when agents, not humans, consume content. Parallel proposes using Shapley values to attribute and pay content owners based on the incremental value their data provides to agent workflows, predicting real dollar flows to publishers within 12–24 months.

## Featured Speakers
- Parag Agrawal, Founder and CEO, Parallel Web Systems

## Main Ideas
- Human click data is a "bug" for agentic search; agent feedback loops are more reliable for training search and ranking systems optimized for AI workflows.
- Parallel launched a search agent first (not a search engine) to incrementally build its index by replacing outsourced human research workflows, trading off latency for coverage and quality.
- Agent queries will eventually outnumber human queries by orders of magnitude, driven by background agents, multi-agent systems, and always-on monitoring workflows.
- The ad-supported web’s economics collapse when agents replace human traffic, as current monetization (ads, subscriptions) cannot attribute or charge for agent-driven value.
- Shapley values offer a theoretically sound way to attribute value from content to agents, enabling differential pricing based on content quality and the economic value of the work being performed.

## Questions And Answers
**Q: Why not use Google Search for agentic workflows?**
A: Parallel’s agentic search reduces token usage by 50% or more, improves accuracy, and is faster, enabling models to do more work within the same compute budget.

**Q: How does Parallel’s Turbo product achieve 200ms latency?**
A: By optimizing compute allocation across retrieval, ranking, and memory hierarchy, and distilling larger models into smaller, specialized ranking models.

**Q: How will content owners be paid in an agent-driven web?**
A: Parallel proposes using Shapley values to estimate the incremental value of each content source to agent outputs, enabling scalable, incentive-aligned payments tied to usage and value.

## Notable Details
- Parallel’s early customers used search agents for insurance underwriting, sales data enrichment, and financial modeling data collection.
- The company originally incorporated as *Shapley Inc.* before rebranding to Parallel, reflecting its focus on value attribution.
- Cloudflare reports AI traffic (including crawlers) now roughly matches human traffic in page reads, signaling a shift in web consumption patterns.
- Parallel’s API integrates with Google Cloud’s enterprise agent APIs, providing an alternative to Google Search for grounding Gemini and other models.
- Meeting prep agents built with Parallel’s API can execute hundreds of web searches per meeting, multiplying query volume far beyond human-driven searches.

## Actionable Takeaways
- Expect agent-driven search to dominate web query volume within a few years, necessitating new infrastructure and business models.
- For high-value content, optimize for agent readability (e.g., earnings transcripts, API docs) as primary consumers shift from humans to AI.
- Monitor developments in Shapley value-based attribution as a potential standard for compensating content owners in agent workflows.
- Evaluate agentic search providers not just on accuracy but on latency, cost, and integration with model inference pipelines.

## People, Companies, Tools, And Links Mentioned
- [Parallel Web Systems](https://parallel.systems)
- [Google Cloud](https://cloud.google.com)
- [Gemini](https://deepmind.google/technologies/gemini/)
- [Cloudflare](https://www.cloudflare.com)
- Shapley values
- Twitter

## Reading Priority

High – This conversation presents a novel, concrete vision for agentic search infrastructure and economic models, backed by early product traction and partnerships.

## Connections

- Source: [[sources/Training Data|Training Data]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Web Platform|Web Platform]], [[topics/AI Infrastructure|AI Infrastructure]]
- Speaker: [[people/parag-agrawal|Parag Agrawal]]
