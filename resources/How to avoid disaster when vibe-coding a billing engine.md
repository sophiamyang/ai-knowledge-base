---
id: "62c354b3a301515f"
title: "How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe"
aliases:
  - "How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Andrew Garvin, Stripe"
url: "https://www.youtube.com/watch?v=mJqwmmOx4WA"
origin: "https://www.youtube.com/watch?v=mJqwmmOx4WA"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-how-to-avoid-disaster-when-vibe-coding-a-billing-engine-andrew-garvin-stripe-62c354b3a301515f.md"
created: "2026-08-29"
tags:
  - "topic/coding-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/product-development"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-how-to-avoid-disaster-when-vibe-coding-a-billing-engine-andrew-garvin-stripe-62c354b3a301515f|How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe raw transcript]]

# How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe

Source: youtube
Original link: https://www.youtube.com/watch?v=mJqwmmOx4WA

## One-Sentence Takeaway
Vibe-coding a billing engine with agents can accelerate setup into a test environment, but human oversight remains critical due to deep business logic, real-money risks, and the need for explicit guardrails like portable skills files and verbose error messages.

## Short Summary
Billing systems, especially usage-based and credit-driven models, carry high stakes when automated by agents—mistakes in auto-recharge, credit expiry, or overage logic can be costly. Andrew Garvin argues for using agents to spin up test environments quickly (e.g., replicating Lovable’s scoped credit pools) but stopping short of production deployment without human review. He distinguishes three agent roles—*as product* (e.g., AI services metered by usage), *as buyer* (e.g., agents provisioning infrastructure via Stripe Projects CLI), and *as user* (e.g., a single agent replacing many human logins, rendering seat-based pricing obsolete).

The talk demonstrates a workflow where a natural-language prompt ("replicate Lovable’s pricing") provisions a sandbox with metered usage, draft invoices, and scoped credit pools, enabled by Metronome’s skills files and Stripe’s orchestration. The core insight: agentic development in billing must prioritize safety, clarity, and discoverability over full autonomy.

## Featured Speakers
- Andrew Garvin: Cofounder of Metronome (acquired by Stripe), a usage-based billing platform.

## Main Ideas
- **Agents excel at acceleration, not autonomy**: Use agents to provision test environments (e.g., Stripe Projects + Metronome) and validate complex billing logic (e.g., credit pools, overage handling), but keep humans in the loop for production due to financial and business-critical risks.
- **Three agent roles in commerce**:
  - *Agent as product*: AI services (e.g., OpenAI, Anthropic) require usage-based metering and credit models.
  - *Agent as buyer*: Agents provision infrastructure (e.g., via Stripe CLI) to discover and assemble backend services.
  - *Agent as user*: A single agent may replace multiple human logins (e.g., HubSpot’s shift from seats to credits), invalidating traditional pricing models.
- **Guardrails for agentic billing**:
  - Portable *skills files* to embed API context and domain knowledge (e.g., Metronome’s billing primitives).
  - Verbose, actionable error messages to enable agent self-correction.
  - Sandboxed testing with synthetic usage data to validate logic before production.
- **Pricing model shifts**: Seat-based models are giving way to credits/commits (e.g., HubSpot’s EMEA rollout) as agents consolidate workloads, requiring granular scoping (e.g., separate pools for builds, cloud calls, gateway usage).

## Questions And Answers
- **Q: How do you prevent agents from misconfiguring billing logic?**
  A: Use skills files to inject domain context (e.g., credit expiry rules), verbose errors for self-correction, and sandboxed testing with synthetic usage before production.

- **Q: Why are companies moving from seats to credits?**
  A: Agents can perform the work of many human users, making seat counts irrelevant; credits align costs with actual usage and enable controls (e.g., agent-specific wallets).

## Notable Details
- Metronome meters API calls for OpenAI and Anthropic, operating at global scale with complex credit/commit models.
- Stripe Projects CLI provisions Stripe accounts + backend services (e.g., Vercel, Postgres, Metronome) via natural language, with exponential adoption growth in 2026.
- Lovable’s pricing model features prepaid credits with auto-recharge, scoped pools (builds, plan mode, cloud, gateway), and overage invoicing.
- HubSpot is transitioning from seats to credits in EMEA, lowering seat prices while adding usage-based components.
- Demo shows an agent creating a Metronome sandbox with a draft invoice, scoped credit pools, and synthetic usage in ~10 minutes.

## Actionable Takeaways
- Use agents to spin up test environments for billing logic, but enforce human review before production.
- Adopt portable skills files to encode domain-specific rules (e.g., credit handling) for agents.
- Design pricing models for *agent as user*: scope credits by function (e.g., builds vs. gateway calls) and consider commits/overage protections.
- Monitor the shift from seat-based to credit-based pricing in enterprise SaaS (e.g., HubSpot, Salesforce) as a signal for agent-driven usage patterns.
- Explore Stripe Projects CLI for agent-discoverable backend provisioning.

## People, Companies, Tools, And Links Mentioned
- [Andrew Garvin](https://www.linkedin.com/in/agarvin/)
- Stripe
- Metronome
- [Stripe Projects](https://stripe.com/projects)
- Lovable
- HubSpot
- OpenAI
- Anthropic
- Vercel
- Hugging Face
- Cognition
- Cursor
- SAP
- Andreessen Horowitz

## Reading Priority

Medium – A concrete, vendor-agnostic framework for safely applying agents to high-stakes systems like billing, with actionable guardrails and real-world pricing trends.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Coding Agents|Coding Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Product Development|Product Development]]
- Speaker: [[people/andrew-garvin|Andrew Garvin]]
