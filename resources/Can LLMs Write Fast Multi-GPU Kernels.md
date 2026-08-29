---
id: "fdbf416f9a6c295f"
title: "Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI"
aliases:
  - "Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Simran Arora, Together AI"
url: "https://www.youtube.com/watch?v=pOvWgX7IJsc"
origin: "https://www.youtube.com/watch?v=pOvWgX7IJsc"
published: "2026-08-27"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-can-llms-write-fast-multi-gpu-kernels-simran-arora-together-ai-fdbf416f9a6c295f.md"
created: "2026-08-29"
tags:
  - "topic/model-inference"
  - "topic/ai-infrastructure"
  - "topic/developer-tools"
  - "topic/foundation-models"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-can-llms-write-fast-multi-gpu-kernels-simran-arora-together-ai-fdbf416f9a6c295f|Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI raw transcript]]

# Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI

Source: youtube
Original link: https://www.youtube.com/watch?v=pOvWgX7IJsc

## One-Sentence Takeaway
Multi-GPU kernel performance is now bottlenecked by interconnects rather than compute, and while a small set of primitives (ParallelKittens) can unlock major gains, even frontier models struggle to reason about the tradeoffs required to generate correct, fast kernels.

## Short Summary
The gap between GPU compute and interconnect throughput has widened, making multi-GPU communication the primary bottleneck in large AI workloads. Standard PyTorch+NCCL baselines often achieve <50% of their communication-aware roofline, but hand-tuned kernels using primitives like ParallelKittens can recover much of this lost performance.

When tasked with generating multi-GPU kernels (ParallelKernelBench), frontier models solve ~30% of problems zero-shot and ~35% with agentic tooling, but most gains cluster in well-represented patterns (e.g., collective primitives), while failures stem from reasoning gaps around collective ordering, data partitioning, and transfer mechanisms (copy engine vs. TMA vs. register-level).

## Featured Speakers
- Simran Arora: Principal Scientist at Together AI, incoming professor at Caltech, leads Frontier Performance Research team

## Main Ideas
- The bottleneck in large AI workloads has shifted from GPU compute to interconnects (NVLink, NVSwitch, InfiniBand), with compute improving 7.2x (A100→B200) while intra-node communication improved only 3x and inter-node 2x, leaving PyTorch+NCCL baselines below 50% of their communication-aware roofline.
- A small set of primitives (ParallelKittens) can bridge this gap by enabling fine-grained control over transfer mechanisms (copy engine, TMA, register-level), overlapping compute/communication (intra-SM vs. inter-SM), and synchronization, adding ~12 lines to single-GPU kernels to achieve state-of-the-art performance in production.
- Frontier models can generate *some* correct and fast multi-GPU kernels (28/87 zero-shot, 35/87 with agentic tooling), but their wins are concentrated in patterns heavily represented online (e.g., collective primitives, tensor-parallel GEMMs), while they fail on reasoning about collective ordering, data partitioning, and transfer mechanism tradeoffs.
- The multi-GPU problem space is combinatorial (data, sequence, tensor, context, layer, pipeline, expert parallelism), each inducing different communication patterns, making it harder for models to generalize beyond familiar cases.

## Questions And Answers
**Q: Why is GPU networking a bottleneck now?**
A: Compute (BF16 tensor cores) improved 7.2x from A100 to B200, but intra-node communication only 3x and inter-node 2x, shifting the bottleneck to interconnects as workloads scale.

**Q: What are the key tradeoffs in multi-GPU kernel design?**
A: Transfer mechanism (copy engine for large messages vs. TMA/register-level for fine-grained, low-latency transfers), overlapping strategies (intra-SM vs. inter-SM for misaligned compute/communication), and synchronization/buffering control.

**Q: How well do models perform on ParallelKernelBench?**
A: Best frontier model solves 28/87 zero-shot (22 faster than PyTorch+NCCL baseline); scaling samples improves correctness to 36 but fast solutions plateau at ~31%. Agentic tooling (Gemini 3 Pro + bash) reaches 35/87 (26 faster), but gains stall with more time.

## Notable Details
- ParallelKittens adds ~12 lines to a single-GPU kernel to enable multi-GPU primitives, used in production at Together AI and Cursor.
- ParallelKernelBench evaluates 87 real-world problems across 7 parallelism dimensions (data, sequence, tensor, context, layer, pipeline, expert), drawn from GitHub repos and optimized libraries.
- Models rarely use TMA or register-level transfers, defaulting to copy engine; they struggle with in-network reductions (e.g., NVSwitch) and inter-SM scheduling.
- Success cases include NeMo vocab-parallel filtering, Hyena context parallelism, and SAM 3 IoU suppression kernels—domains where hand-tuned kernels were previously missing.

## Actionable Takeaways
- Audit your multi-GPU workloads for communication bottlenecks; PyTorch+NCCL baselines likely leave >50% performance on the table.
- For fine-grained communication, prefer device-initiated transfers (TMA/register-level) over copy engine to saturate NVLink with small messages.
- If using models to generate kernels, validate collective ordering and partitioning logic—syntax errors are rare, but reasoning failures are common.
- Monitor advances in agentic tooling for kernel generation; current approaches plateau at ~35% solve rates, suggesting room for specialized methods.
- Explore ParallelKittens for production-grade multi-GPU primitives if hand-tuning is prohibitive.

## People, Companies, Tools, And Links Mentioned
- Simran Arora
- Together AI
- Cursor
- NVIDIA (A100, B200, H100, NVLink, NVSwitch)
- AMD (XGMI)
- Google (TPU, Gemni 3 Pro)
- [ParallelKernelBench GitHub](https://github.com/togethercomputer/ParallelKernelBench)
- [Simran Arora’s website](https://arorasimran.com)
- FlashAttention
- DeepSeek
- Mamba
- Megatron-LM
- FluxFlow
- Nanoflow
- Triton Distributed
- TileLang
- Mojo
- Gluon
- ThunderKittens
- HipKittens
- DPP
- Comet
- RingAttention
- Flux
- Flash-Decoding
- MoE
- CUTLASS
- NeMo
- Hyena
- SAM 3

## Reading Priority

High – This work quantifies a critical, emerging bottleneck in AI infrastructure and provides both a practical solution (ParallelKittens) and a rigorous benchmark (ParallelKernelBench) exposing gaps in frontier model reasoning for multi-GPU systems.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Model Inference|Model Inference]], [[topics/AI Infrastructure|AI Infrastructure]], [[topics/Developer Tools|Developer Tools]], [[topics/Foundation Models|Foundation Models]]
- Speaker: [[people/simran-arora|Simran Arora]]
