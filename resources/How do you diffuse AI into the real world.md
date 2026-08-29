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
  - "Varun Shenoy: Cofounder, Long Lake"
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
AI diffusion in services requires owning operations to align incentives, co-designing workflows in person, and building evals grounded in real-world outcomes rather than demos.

## Short Summary
Varun Shenoy argues that deploying AI in services businesses is a diffusion problem akin to electricity’s slow adoption: technology alone is insufficient without retraining, process changes, and deep integration. Long Lake acquires and operates businesses (e.g., property management, corporate travel) to control outcomes, ensuring AI failures are their problem—not a customer’s. The core challenge is moving from copilot to asynchronous, long-running agents for non-code knowledge work, where parallelization and ground-truth evals (e.g., "did the roof get fixed?") are critical. Diffusion succeeds only through extreme software-service co-design, requiring in-person collaboration to understand and embed AI into existing workflows.

## Featured Speakers
- Varun Shenoy: Cofounder, Long Lake

## Main Ideas
- **Diffusion is the bottleneck**: Like electricity, AI’s real-world impact lags behind demos because adoption requires process overhauls, retraining, and replacing legacy systems—not just better models.
- **Ownership aligns incentives**: By acquiring and operating businesses, Long Lake bears the cost of AI failures, forcing them to solve real problems (e.g., closing books with missing receipts) rather than selling software and blaming customers.
- **Agent maturity ladder**: Progressing from copilots to coworkers demands earning autonomy incrementally; asynchronous agents for non-code work (e.g., services) remain unsolved, unlike coding where parallelization is trivial.
- **Ground-truth evals**: Real-world traces (tool calls, hiccups, outcomes) enable evals tied to business results (e.g., "was the roof repaired?"), creating a flywheel for continual learning and regression testing.
- **Co-design requires presence**: AI cannot be integrated over Zoom; in-person engagement (trade shows, mountain biking with users) reveals workflow nuances and builds trust for adoption.

## Questions And Answers
- **Why hasn’t AI changed services businesses yet?**
  Diffusion takes time. Even with capable models, businesses must rip out old processes, retrain staff, and accept short-term disruption—just as Ford’s electrified assembly line required 40+ years after Edison’s demo.

- **What’s missing from today’s agent demos?**
  Demos focus on tasks with clear, internet-available data (e.g., coding, flight booking), but the most valuable work (e.g., coordinating roof repairs, scoping blueprints) lacks digital traces and is highly customized per company, user, or client.

- **How do you measure agent success in the real world?**
  Ground-truth outcomes: Did the books close? Was the roof fixed? These evals are built from traces of real work, including implicit feedback (e.g., differences between AI-generated data and final submissions).

## Notable Details
- Long Lake has acquired 35 services businesses (property management, architecture, HR) and took American Express Global Business Travel private for $6.3B.
- Their team is ~40 people, with >50% focused on technology, data, and deployment.
- Engineers naturally parallelize work (e.g., launching 10 jobs, accepting out-of-order completion), but services work (e.g., email, vendor coordination) is traditionally serial—async agents for this domain are an open problem.
- Post-training models on proprietary, out-of-distribution business data (e.g., 20-year-old software workflows) to handle tasks frontier models cannot.
- Learning loops merge continual learning (model improvement) and enablement (adoption): usage drives better agents, which drives more usage.

## Actionable Takeaways
- **Prioritize ground-truth evals**: Design agent tasks around measurable outcomes (e.g., "roof repaired") to create feedback loops that improve models and workflows.
- **Co-design in person**: Embed with users to observe real workflows; remote collaboration misses critical context for services AI.
- **Start with copilots, earn autonomy**: Deploy low-risk, synchronous tools first, then gradually introduce async/long-running agents as trust and capability grow.
- **Acquire or partner deeply**: Ownership or operational control ensures alignment between AI failures and business accountability.
- **Target serial workflows**: Focus on parallelizing traditionally linear tasks (e.g., inbox management, vendor coordination) as a high-leverage opportunity.

## People, Companies, Tools, And Links Mentioned
- [Long Lake](https://www.linkedin.com/in/varunshenoy)
- Varun Shenoy: [Twitter](https://x.com/varunshenoy_), [LinkedIn](https://www.linkedin.com/in/varunshenoy), [Website](https://varunshenoy.com)
- American Express Global Business Travel
- Elad Gil
- General Catalyst
- Alpha Wave
- Palantir, Ramp, Glean, Blackstone, HIG
- Edison’s Pearl Street Station
- Ford’s electrified assembly line (1924)
- Claude Code, Codex, Claude Cowork
- MCPs (Model Context Protocols)

## Reading Priority

High – A rare, concrete look at the operational and cultural barriers to AI adoption in services, backed by a novel ownership model and hard-won lessons from real deployments.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Model Evaluation|Model Evaluation]], [[topics/Product Development|Product Development]]
- Speaker: [[people/varun-shenoy-cofounder|Varun Shenoy: Cofounder]]
