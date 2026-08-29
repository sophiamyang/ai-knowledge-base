---
id: "e9abc39637c0a468"
title: "Productionizing LLM Gateways: Architecture, Tradeoffs and Hard Lessons — Kanish Manuja, Twilio"
aliases:
  - "Productionizing LLM Gateways: Architecture, Tradeoffs and Hard Lessons — Kanish Manuja, Twilio"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Kanish Manuja, Principal Engineer at Twilio"
url: "https://www.youtube.com/watch?v=zrZ1amZBSPw"
origin: "https://www.youtube.com/watch?v=zrZ1amZBSPw"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-productionizing-llm-gateways-architecture-tradeoffs-and-hard-lessons-kanish-manu-e9abc39637c0a468.md"
created: "2026-08-29"
tags:
  - "topic/model-inference"
  - "topic/ai-infrastructure"
  - "topic/enterprise-ai"
  - "topic/developer-tools"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-productionizing-llm-gateways-architecture-tradeoffs-and-hard-lessons-kanish-manu-e9abc39637c0a468|Productionizing LLM Gateways: Architecture, Tradeoffs and Hard Lessons — Kanish Manuja, Twilio raw transcript]]

# Productionizing LLM Gateways: Architecture, Tradeoffs and Hard Lessons — Kanish Manuja, Twilio

Source: youtube
Original link: https://www.youtube.com/watch?v=zrZ1amZBSPw

## One-Sentence Takeaway
An LLM gateway forces a zero-sum tradeoff between availability, latency, guardrails, and cost, and naive reliability patterns from traditional APIs backfire with LLMs.

## Short Summary
An LLM gateway sits between applications and model providers to route, authenticate, and govern traffic. Its core tension is that degradation requires sacrificing at least one of four priorities: availability, latency, guardrails, or cost. Streaming responses lock you into a provider mid-request, eliminating fallback options and surfacing errors like "Something went wrong."

Standard retry and circuit-breaker logic is ill-suited for LLMs because calls are slow and expensive; per-request fallback to a secondary provider is often superior. Latency must be tracked per model and route, not gateway-wide, because a reasoning model’s normal latency can exceed a chat model’s outage threshold. Guardrails themselves are fallible services, forcing a choice between failing open (serving requests without checks) or closed (blocking requests).

## Featured Speakers
- Kanish Manuja, Principal Engineer at Twilio

## Main Ideas
- Retries and circuit breakers are counterproductive for LLMs: retries explode latency and cost, while circuit breakers ignore healthy secondary providers. Prefer per-request fallback (sequential or parallel) with cooldowns for persistently failing primaries.
- Streaming responses surrender control: once tokens begin streaming, switching providers is impossible, so errors appear abruptly. This is a deliberate tradeoff for perceived speed.
- Latency must be measured and timed out per model and route, not aggregated. A reasoning model’s P99 can spike to 60 seconds unpredictably, which would be catastrophic for a chat route; mixed workloads make gateway-wide metrics meaningless.
- Guardrails are services that can fail, requiring explicit decisions on fail-open vs. fail-closed behavior, time budgets, and fallback mechanisms (e.g., secondary checks or cached decisions).
- Centralized governance (cost tracking, rate limits) does not require a centralized gateway; decentralized gateways with shared plugins or custom code can achieve governance without a single point of failure.

## Questions And Answers
- **Why not use traditional retries for LLM calls?**
  Retries consume latency budgets quickly and multiply costs due to the slow, expensive nature of LLM calls. Circuit breakers also ignore available secondary providers.

- **How should latency be tracked in a gateway with mixed workloads?**
  Track P99 latency per model and per route, not gateway-wide. A reasoning model’s normal latency may be an outage for a chat model, so aggregated metrics obscure real issues.

- **Should guardrails fail open or closed?**
  There is no universal answer. Fail-open allows requests to proceed without checks (prioritizing availability), while fail-closed blocks requests (prioritizing security). The choice depends on the use case and the worst-case scenario you can tolerate.

## Notable Details
- Fallbacks are not transparent: differences in tool-calling schemas, token limits, and stop reasons between providers require a normalization layer for cross-provider fallbacks.
- Secondary (fallback) providers should have *more* headroom than primaries, as they are the last line of defense. Under-provisioning them risks cascading failures.
- Hedging the tail: firing a duplicate request if the primary consumes a high percentile (e.g., P90) of the latency budget can mitigate P99 spikes.
- Load shedding is critical for gateways under retry storms. Web servers’ internal queues must be bounded, and traffic prioritization can protect high-value use cases.
- Shared API keys and noisy tenants can disrupt gateway performance; segregate keys per route or use case to isolate failures.

## Actionable Takeaways
- Replace retries with per-request fallbacks (sequential or parallel) and cooldowns for failing providers.
- Measure and set timeouts per model and route, not gateway-wide. Treat reasoning models’ latency variability as a first-class concern.
- Decide in advance whether guardrails fail open or closed, and implement time budgets and fallbacks for guardrail services.
- Avoid centralizing traffic in a single gateway; instead, decentralize the gateway while centralizing governance via plugins or shared code.
- Test fallback providers as rigorously as primaries, and provision them with higher headroom to handle surge traffic.

## People, Companies, Tools, And Links Mentioned
- Kanish Manuja
- Twilio
- [Kanish Manuja’s LinkedIn](https://www.linkedin.com/in/kanish-manuja-a99bb923/)

## Reading Priority

High – Concrete, production-tested advice on LLM gateway tradeoffs, with specific anti-patterns and actionable alternatives.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Model Inference|Model Inference]], [[topics/AI Infrastructure|AI Infrastructure]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Developer Tools|Developer Tools]]
- Speaker: [[people/kanish-manuja|Kanish Manuja]]
