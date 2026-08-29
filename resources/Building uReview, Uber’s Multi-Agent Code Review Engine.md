---
id: "89cb77c19944743b"
title: "Building uReview, Uber’s Multi-Agent Code Review Engine — Will Bond & Ameya Ketkar, Uber"
aliases:
  - "Building uReview, Uber’s Multi-Agent Code Review Engine — Will Bond & Ameya Ketkar, Uber"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Will Bond, Engineer at Uber"
  - "Ameya Ketkar, Engineer at Uber"
url: "https://www.youtube.com/watch?v=EL123UNokkI"
origin: "https://www.youtube.com/watch?v=EL123UNokkI"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-building-ureview-uber-s-multi-agent-code-review-engine-will-bond-ameya-ketkar-ub-89cb77c19944743b.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/ai-infrastructure"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-building-ureview-uber-s-multi-agent-code-review-engine-will-bond-ameya-ketkar-ub-89cb77c19944743b|Building uReview, Uber’s Multi-Agent Code Review Engine — Will Bond & Ameya Ketkar, Uber raw transcript]]

# Building uReview, Uber’s Multi-Agent Code Review Engine — Will Bond & Ameya Ketkar, Uber

Source: youtube
Original link: https://www.youtube.com/watch?v=EL123UNokkI

## One-Sentence Takeaway
Uber built uReview, an in-house multi-agent code review system, to address a growing code review bottleneck, achieving a 60% cost reduction and 67% comment addressal rate by focusing on observability, customization, and scaling agentic reviews alongside human feedback.

## Short Summary
Code review delays at Uber grew from 3 to 9 hours between 2024 and 2026 as PR volume and size increased, making it a critical bottleneck. The company built uReview—a custom, multi-agent system integrated with Phabricator and GitHub—to standardize reviews for both human engineers and AI agents, ensuring consistency, scalability, and compliance across hundreds of teams and six monorepos.

The system’s effectiveness hinged on evolving beyond cost metrics to track sentiment, addressal rates, and agent trajectories, revealing that models confidently assert incorrect reviews without self-awareness. By enabling team-specific customizations and improving observability, Uber reduced costs by 60% while increasing quality, demonstrating that scaling agentic reviews requires more than just skill authoring—it demands robust feedback loops and operational discipline.

## Featured Speakers
- Will Bond, Engineer at Uber
- Ameya Ketkar, Engineer at Uber

## Main Ideas
- Code review became Uber’s primary engineering bottleneck as PR volume and size grew, with first-review times tripling from 2024 to 2026.
- Uber built uReview in-house to support Phabricator (and GitHub migration), ensure consistent reviews for both humans and AI agents, and scale customization across hundreds of teams without centralized management.
- Early observability (cost, NPS, Google Forms) was insufficient; tracking reply sentiment, addressal rates, and agent trajectories enabled tuning for quality and cost, revealing that models do not self-correct and require guardrails.
- Customization was critical: teams wrote their own reviewers (e.g., linters, multi-file agents) but scaling them cheaply and reliably was the hard part, requiring ownership models, deterministic routing, and surfaced observability.
- The shift to an agentic SDLC does not eliminate the outer loop (human review) but reorients it toward higher-level concerns like architecture and domain expertise, while agents handle implementation details and nits.

## Questions And Answers
- **Why didn’t Uber buy a code review solution?**
  Most vendors did not support Phabricator, and Uber needed agents in the inner loop to be reviewed against the same rules as humans, with distributed customization and risk-aware routing.

- **How did Uber improve uReview’s quality-to-cost ratio?**
  By tracking sentiment, addressal rates (67% of comments are addressed), and agent trajectories, they tuned prompts and guardrails, reducing costs by 60% and improving accuracy by 70% over a naive implementation.

- **What’s the role of humans as agentic code review scales?**
  Humans shift from implementation-level feedback to higher-level concerns like architecture and product thinking, expanding rather than eliminating the outer loop.

## Notable Details
- uReview posts ~25,000 comments weekly, with 10% receiving feedback and 4% of PRs getting negative feedback.
- 75% of high-severity issues flagged by uReview are addressed by developers.
- Teams author custom agents (e.g., linters, multi-file reviewers) by leveraging past PRs and knowledge bases, often with LLM assistance (e.g., Claude).
- Early versions suffered from duplicated or low-value comments; post-processing now rates, categorizes, filters, and deduplicates to surface only high-confidence, actionable feedback.
- Agentic SDLC risks "cavitation" (agents oscillating on fixes) if review accuracy is low, requiring higher precision for inner-loop feedback.

## Actionable Takeaways
- Prioritize observability beyond cost: track sentiment, addressal rates, and agent trajectories to tune quality and efficiency.
- Distribute customization but centralize guardrails: let teams own their review rules while enforcing consistency and compliance at scale.
- Design for both inner and outer loops: optimize agentic reviews for precision to avoid cavitation, and reorient human effort toward architecture and domain expertise.
- Expect iteration: scaling agentic systems requires more work on runtime, routing, and feedback loops than on initial skill authoring.

## People, Companies, Tools, And Links Mentioned
- [Uber](https://www.uber.com)
- [Phabricator](https://phabricator.wikimedia.org)
- [GitHub](https://github.com)
- [Claude](https://www.anthropic.com)
- Will Bond: [Twitter](https://x.com/wbond), [GitHub](https://github.com/wbond)
- Ameya Ketkar: [GitHub](https://github.com/ameya-ketkar), [Google Scholar](https://scholar.google.com/citations?user=ameya-ketkar)

## Reading Priority

High – A rare, detailed case study on scaling multi-agent code review in a large enterprise, with concrete metrics, tradeoffs, and lessons for agentic SDLC adoption.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/AI Infrastructure|AI Infrastructure]]
- Speakers: [[people/will-bond|Will Bond]], [[people/ameya-ketkar|Ameya Ketkar]]
