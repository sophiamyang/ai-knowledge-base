---
id: "a3711de347f26364"
title: "KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat"
aliases:
  - "KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Yuchen Fama, Product Manager at Red Hat Inference, contributor to vLLM and llm-d"
  - "Ashish Kamra, Senior Manager of Performance Engineering at Red Hat"
url: "https://www.youtube.com/watch?v=YXowceUKYJI"
origin: "https://www.youtube.com/watch?v=YXowceUKYJI"
published: "2026-08-27"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-kv-cache-aware-routing-and-p-d-disaggregation-on-kubernetes-yuchen-fama-ashish-k-a3711de347f26364.md"
created: "2026-08-29"
tags:
  - "topic/model-inference"
  - "topic/ai-infrastructure"
  - "topic/developer-tools"
  - "topic/open-source-ai"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-kv-cache-aware-routing-and-p-d-disaggregation-on-kubernetes-yuchen-fama-ashish-k-a3711de347f26364|KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat raw transcript]]

# KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat

Source: youtube
Original link: https://www.youtube.com/watch?v=YXowceUKYJI

## One-Sentence Takeaway
For agentic workloads with long sessions, high cache hit rates, and extreme input-to-output token ratios, KV-cache-aware routing and prefill/decode disaggregation on Kubernetes can cut inter-token latency by 9x and improve throughput by 60% when paired with high-speed networking.

## Short Summary
Public inference benchmarks often miss the realities of agentic workloads: multi-turn sessions up to 3,000 turns, >90% KV cache hit rates, and input-to-output token ratios exceeding 100:1. These workloads demand new optimizations, as cached tokens cost 10x less than uncached ones, making cache locality and reuse critical.

Two levers stand out: KV-cache-aware routing to minimize cache misses and prefill/decode (P/D) disaggregation to separate compute-bound prefill from memory-bound decode. P/D reduces P99 inter-token latency from ~900ms to ~100ms in Red Hat’s tests, but requires RDMA/RoCE for KV cache transfers. The sweet spot for P/D is mid-range concurrency; at low or high concurrency, aggregated serving can match or exceed its performance.

## Featured Speakers
- Yuchen Fama, Product Manager at Red Hat Inference, contributor to vLLM and llm-d
- Ashish Kamra, Senior Manager of Performance Engineering at Red Hat

## Main Ideas
- Agentic workloads break classic LLM serving assumptions: sessions span thousands of turns, cache hit rates exceed 90%, and input-to-output token ratios often surpass 100:1, making cache management and latency optimization central.
- KV-cache-aware routing (e.g., via llm-d’s endpoint picker) can route requests to pods with existing cache, cutting time-to-first-token (TTFT) from ~3s to ~1s for repeated prompts, and avoiding 10x cost penalties for uncached tokens.
- Prefill/decode disaggregation separates compute-heavy prefill (batch-friendly, high FLOPS) from latency-sensitive decode (memory-bound, sequential), eliminating phase interference that stalls token generation during long prefill bursts.
- P/D shines in mid-concurrency regimes, reducing P99 inter-token latency by ~9x (900ms → 100ms) in tests with 16 H100s, but requires RDMA/RoCE for KV cache transfers; without it, aggregated serving may be preferable.
- The optimal architecture depends on workload characteristics: long contexts, high input/output ratios, and strict inter-token latency (ITL) requirements favor P/D, while short contexts or strict TTFT needs may favor aggregated serving.

## Questions And Answers
- **When does P/D disaggregation outperform aggregated serving?**
  In mid-concurrency regimes with long contexts, high input/output ratios, and strict ITL requirements, P/D reduces latency and jitter. At low or high concurrency, aggregated serving can match or exceed P/D performance.

- **What networking is required for P/D?**
  RDMA or RoCE fabric is necessary to transfer KV caches between prefill and decode workers at scale. Without it, the overhead negates P/D’s benefits.

- **How does KV-cache-aware routing improve performance?**
  By routing requests to pods with existing KV cache (e.g., same system prompt), it avoids recomputing prefill, cutting TTFT from ~3s to ~1s and reducing costs by leveraging 10x cheaper cached tokens.

## Notable Details
- In Red Hat’s traces, agentic sessions reach 3,000 turns with >90% cache hit rates and input-to-output token ratios >100:1.
- Anthropic’s API pricing reflects a 10x cost difference between cached and uncached tokens, making cache optimization economically critical.
- Demo: First request (no cache) takes ~3s; subsequent requests with cache reuse take ~1s. Changing the system prompt forces a new pod and ~3s latency.
- P99 inter-token latency for GPT-OSS-120B on 16 H100s: ~900ms (aggregated) vs. ~100ms (P/D with 2 prefill, 2 decode workers).
- GLM-5.2 on H200s (3 prefill, 1 decode workers) achieved 4x faster TTFT and 60% more requests for a 45:1 input/output ratio workload.
- BF16 KV cache outperformed FP8 for longer prefill phases in Red Hat’s tests.

## Actionable Takeaways
- Prioritize KV-cache-aware routing for agentic workloads to exploit high cache hit rates and reduce TTFT/costs.
- Evaluate P/D disaggregation if your workload has long contexts, high input/output ratios, and mid-range concurrency—but ensure RDMA/RoCE is available.
- For low/high concurrency or strict TTFT needs, aggregated serving may suffice; benchmark both approaches.
- Monitor P99 inter-token latency and cache throughput separately, as averages hide critical tail behaviors in agentic workloads.
- Explore llm-d’s endpoint picker, offload tiers (NVMe/Ceph), and session-aware eviction policies for cache management.

## People, Companies, Tools, And Links Mentioned
- [llm-d](https://github.com/llm-d/llm-d)
- Red Hat (OpenShift, vLLM, KServe, GuideLLM, LLM Compressor, Speculators)
- [Red Hat AI Hugging Face org](https://huggingface.co/RedHat-AI)
- [InferencePerf trace replay tool](https://github.com/llm-d/llm-d) (collaboration with Google and IBM)
- DeepLearning.AI (free course on open-source inference with Cedric and Andrew Ng)
- [Red Hat Developer portal blogs on distributed inference](https://developers.redhat.com/)
- CoreWeave, Google, IBM, Nvidia (ecosystem collaborators)
- GLM-5.2, GPT-OSS-120B (models)
- H100, H200, B200 (GPUs)
- Mooncake (KV-centric store)
- NIXL (KV transfer mechanism)
- RDMA, RoCE (networking fabrics)
- Ceph (distributed file system)

## Reading Priority

High – This talk delivers concrete, novel optimizations for agentic LLM inference with hard numbers, clear tradeoffs, and actionable guidance for production deployments.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Model Inference|Model Inference]], [[topics/AI Infrastructure|AI Infrastructure]], [[topics/Developer Tools|Developer Tools]], [[topics/Open Source AI|Open Source AI]]
- Speakers: [[people/yuchen-fama|Yuchen Fama]], [[people/ashish-kamra|Ashish Kamra]]
