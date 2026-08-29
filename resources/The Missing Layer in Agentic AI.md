---
id: "944cf959aa80c397"
title: "The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs"
aliases:
  - "The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=XsvUhpnHepE"
origin: "https://www.youtube.com/watch?v=XsvUhpnHepE"
published: "2026-08-26"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-the-missing-layer-in-agentic-ai-giedrius-teimantas-oxylabs-944cf959aa80c397.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/developer-tools"
  - "topic/ai-infrastructure"
  - "topic/web-platform"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-the-missing-layer-in-agentic-ai-giedrius-teimantas-oxylabs-944cf959aa80c397|The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs raw transcript]]

# The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs

Source: youtube
Original link: https://www.youtube.com/watch?v=XsvUhpnHepE

## One-Sentence Takeaway
Agentic AI fails silently on the open web because missing infrastructure layers feed CAPTCHAs and invalid content to models, wasting 70% of tokens and breaking workflows.

## Short Summary
Most agentic workflows assume a 200 HTTP response means usable content, but CAPTCHAs, blocks, and heavy JavaScript often waste tokens and break flows. The fix is a scraping-informed infrastructure layer: avoid browsers until checkout, validate content before token spend, and use lightweight APIs for discovery and decision stages.

The approach replaces browser automation with a search API for discovery (compact JSON, <700 ms) and a scraper API for decision (markdown, explicit errors, geolocation), reserving a hardened headless browser only for checkout. This reduces cost, increases reliability, and scales parallel requests without silent failures.

## Featured Speakers
- Giedrius Šteimantas, Oxylabs

## Main Ideas
- **Browser avoidance**: Use browsers only for dynamic, interactive tasks (e.g., checkout); replace with lightweight APIs for discovery and decision stages to cut cost and latency.
- **Content validation**: HTTP 200 ≠ valid content; explicit errors for blocks/CAPTCHAs prevent silent token waste (e.g., 70% of tokens spent on CAPTCHAs when 7/10 pages fail).
- **Token efficiency**: Compact JSON (search API) and markdown (scraper API) reduce token count per request, enabling parallel fan-out queries without model overhead.
- **Geolocation consistency**: Localized results in discovery/decision must match checkout to avoid stock/price mismatches; requires proxy + geolocation at the infrastructure layer.

## Questions And Answers
- **Why do agents fail silently on the web?**
  They rely on HTTP status codes or response size, not content validation, so CAPTCHAs/blocks are fed to LLMs as "valid" inputs, wasting tokens and breaking flows.

- **How can discovery be done without browsers?**
  Use a search API (e.g., Fast Search API) returning compact JSON (<2,000 tokens, <700 ms) to let agents fan out queries and select URLs from indexed results.

- **When is a browser unavoidable?**
  Checkout requires dynamic interaction (e.g., size selection, cart updates), but must be hardened with stealth, residential proxies, and geolocation to avoid blocks.

## Notable Details
- Oxylabs’ Fast Search API: <2,000 tokens/response, ~700 ms latency, predictable pricing.
- Oxylabs Web Scraper API: returns markdown, fails explicitly on blocks, supports geolocation, and bills only for successful requests.
- Playwright MCP + Oxylabs headless browser: drop-in replacement for checkout, with stealth and proxy/geolocation built in.
- Parallel requests: scraper API enables hundreds of concurrent calls without browser overhead.
- Silent failures: teams often miss CAPTCHA/block issues by checking only HTTP 200 or response size.

## Actionable Takeaways
- Audit agent workflows for silent failures: validate content before token spend, not just HTTP status.
- Replace browser automation with APIs for discovery/decision stages; reserve browsers for checkout only.
- Enforce geolocation consistency across all stages to avoid stock/price mismatches.
- Prioritize lightweight, structured outputs (JSON/markdown) to reduce token costs and latency.
- Adopt "no cure, no pay" infrastructure (e.g., scraper APIs) to eliminate costs for failed requests.

## People, Companies, Tools, And Links Mentioned
- Giedrius Šteimantas
- Oxylabs
- [Oxylabs](https://oxylabs.io)
- [Giedrius Šteimantas on LinkedIn](https://www.linkedin.com/in/steimantas)
- Playwright MCP
- Fast Search API
- Web Scraper API

## Reading Priority

Medium – Practical, concrete guidance on a critical but overlooked layer for agentic AI, with actionable patterns from a battle-tested scraping provider.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/AI Infrastructure|AI Infrastructure]], [[topics/Web Platform|Web Platform]]
