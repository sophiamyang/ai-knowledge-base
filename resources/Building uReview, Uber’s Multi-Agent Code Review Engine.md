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
  - "Will Bond & Ameya Ketkar, Uber"
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
  - "topic/model-evaluation"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-building-ureview-uber-s-multi-agent-code-review-engine-will-bond-ameya-ketkar-ub-89cb77c19944743b|Building uReview, Uber’s Multi-Agent Code Review Engine — Will Bond & Ameya Ketkar, Uber raw transcript]]

# Building uReview, Uber’s Multi-Agent Code Review Engine — Will Bond & Ameya Ketkar, Uber

Source: youtube
Original link: https://www.youtube.com/watch?v=EL123UNokkI

## One-Sentence Takeaway
Uber built uReview, an in-house multi-agent code review system, to address a growing code review bottleneck by scaling customizable, high-quality automated reviews while reducing cost by 60% and achieving a 67% comment addressal rate.

## Short Summary

Code review delays at Uber grew from 3 hours in 2024 to 9 hours in 2026, driven by increasing PR volume and size, making it a critical bottleneck for thousands of engineers across distributed teams. To solve this, Uber developed uReview, a custom multi-agent system integrated with Phabricator and GitHub, designed to enforce consistent review rules for both human and AI agents while supporting team-specific customizations.

The system’s effectiveness hinged on robust observability—tracking reply sentiment, comment addressal rates, and agent trajectories—to tune performance, as models confidently assert reviews even when wrong. By focusing on these metrics, Uber improved quality-to-cost ratios, reduced costs by 60%, and now processes ~25,000 comments weekly, with 67% addressed by developers.

## Featured Speakers
- Will Bond: Engineer at Uber, co-creator of uReview
- Ameya Ketkar: Engineer at Uber, co-creator of uReview

## Main Ideas
- Code review became Uber’s primary engineering bottleneck, with first-review times tripling from 2024 to 2026 due to scaling PR volume and complexity.
- Uber built uReview in-house to support Phabricator (and GitHub migration), enforce consistent reviews for both humans and AI agents, and allow team-specific customizations at scale.
- Early observability (cost, NPS, Google Forms) was insufficient; tracking reply sentiment, addressal rates (~67%), and agent trajectories enabled tuning for quality and cost efficiency.
- Models do not self-identify errors—they assert reviews with full confidence—requiring guardrails, team-specific rules, and feedback loops to guide accuracy.
- Customization was critical: teams define their own reviewers (single-file, multi-file, AI linters, or custom agents) but scaling these cheaply and reliably was the hardest challenge.

## Questions And Answers
- **Why not buy a commercial solution?**
  Most vendors did not support Phabricator, and Uber needed agents in the inner loop to follow the same review rules as humans, with distributed team ownership.

- **How did observability improve uReview?**
  Initial metrics (cost, NPS) were too coarse; adding sentiment analysis, addressal rates, and agent trajectory tracking revealed actionable gaps, reducing costs by 60% and improving accuracy by ~70%.

- **What’s the role of humans as AI agents take over more code review?**
  Humans shift from nitpicking implementations to higher-level concerns like architecture, domain expertise, and product thinking—expanding, not eliminating, the outer loop.

## Notable Details
- uReview posts ~25,000 comments weekly; 67% are addressed by developers, with 75% of high-severity issues resolved.
- Costs dropped 60% and accuracy improved ~70% compared to a naive initial implementation.
- Teams author custom review "skills" (e.g., via Claude) quickly, but running them at scale with consistent quality and low cost required significant iteration.
- Deduping, rating, categorizing, and filtering comments reduces noise for engineers.
- Uber’s six language-specific monorepos each have unique anti-patterns and style guides baked into multi-file review agents.

## Actionable Takeaways
- For enterprise AI tools, prioritize observability beyond cost/NPS—track addressal rates, sentiment, and agent trajectories to tune quality.
- Distribute customization to teams but centralize guardrails and routing to maintain consistency and scalability.
- Expect AI agents to handle low-level reviews; refocus human effort on architecture and domain expertise.
- If adopting automated code review, plan for deduping and filtering to avoid overwhelming engineers with redundant or low-value comments.
- Anticipate that models will not self-correct—design feedback loops to continuously improve accuracy.

## People, Companies, Tools, And Links Mentioned
- [Uber](https://www.uber.com)
- [Phabricator](https://phabricator.wikimedia.org)
- [GitHub](https://github.com)
- [Claude](https://www.anthropic.com)
- [Will Bond on Twitter](https://x.com/wbond)
- [Will Bond on LinkedIn](http://linkedin.com/in/wbond)
- [Ameya Ketkar on LinkedIn](https://www.linkedin.com/in/ameya-ketkar)
- [Ameya Ketkar on Google Scholar](https://scholar.google.com/citations?user=6JO46GMAAAAJ&hl=en)

## Reading Priority

High – A rare, detailed case study on scaling enterprise AI for code review with concrete metrics, tradeoffs, and lessons for observability and human-AI collaboration.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Model Evaluation|Model Evaluation]]
- Speaker: [[people/will-bond-ameya-ketkar|Will Bond & Ameya Ketkar]]
