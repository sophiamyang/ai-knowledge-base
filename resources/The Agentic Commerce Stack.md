---
id: "3887272d6cb5b712"
title: "The Agentic Commerce Stack — Ahnaf Prio, Best Buy"
aliases:
  - "The Agentic Commerce Stack — Ahnaf Prio, Best Buy"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Ahnaf Prio, Senior Engineering Manager at Best Buy"
url: "https://www.youtube.com/watch?v=G7cgLjZtmMU"
origin: "https://www.youtube.com/watch?v=G7cgLjZtmMU"
published: "2026-08-27"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-the-agentic-commerce-stack-ahnaf-prio-best-buy-3887272d6cb5b712.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/developer-tools"
  - "topic/enterprise-ai"
  - "topic/web-platform"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-the-agentic-commerce-stack-ahnaf-prio-best-buy-3887272d6cb5b712|The Agentic Commerce Stack — Ahnaf Prio, Best Buy raw transcript]]

# The Agentic Commerce Stack — Ahnaf Prio, Best Buy

Source: youtube
Original link: https://www.youtube.com/watch?v=G7cgLjZtmMU

## One-Sentence Takeaway
Agentic commerce requires standardized protocols (MCP, A2A, ACP/UCP, AP2) to replace brittle browser automation, with product feeds and scoped payment mandates enabling reliable, scalable merchant-agent interactions.

## Short Summary
Shopping accounts for ~45% of major assistant sessions, yet early agentic shopping failed because DOM-scraping and form-filling triggered fraud systems and broke on commerce nuances (e.g., line items vs. quantities). The current stack replaces browsers with direct API calls: MCP for tool access, A2A for agent-to-agent communication, ACP/UCP for commerce primitives, and AP2 for scoped payment mandates with spend ceilings and revocation.

Merchants push product feeds instead of supporting catalog search to avoid m×n scaling issues, while evals for behavior, protocol compliance, and latency are critical to prevent production failures like Chipotle’s agent being repurposed for unrelated tasks.

## Featured Speakers
- Ahnaf Prio, Senior Engineering Manager at Best Buy

## Main Ideas
- Early agentic shopping failed due to brittle browser automation (screenshots, DOM reads, form fills) that triggered merchant fraud systems and broke on commerce-specific edge cases (e.g., line items vs. SKU quantities).
- The current agentic commerce stack relies on standardized protocols: **MCP** (tool access), **A2A** (agent-to-agent communication), **ACP/UCP** (commerce primitives for product data and checkout), and **AP2** (scoped payment mandates with authorization, spend limits, and revocation).
- Merchants push **product feeds** (not catalog search) to assistants like ChatGPT/Gemini to avoid m×n scaling, enable pre-indexing, and support retail media/ranking—though feed schemas vary (e.g., Meta’s vs. UCP/ACP).
- **Evaluations are non-negotiable**: Without rigorous testing for behavior, protocol compliance, and latency, agents will misbehave in production (e.g., Chipotle’s agent answering programming questions) or leak sensitive data (e.g., discount codes, other shoppers’ activity).
- Autonomous shopping remains aspirational; today’s flows are **human-in-the-loop** with delegated payment tokens (ChatGPT) or Google Pay (Gemini), while AP2’s scoped mandates hint at future autonomy.

## Questions And Answers
- **Why did screenshot/DOM-based shopping agents fail?**
  They were slow, brittle, and triggered merchant fraud systems, often failing at payment. Merchants also treat line items and quantities differently, breaking naive automation.

- **How do ACP and UCP differ from traditional catalog search?**
  They replace search with **product feeds** pushed by merchants, enabling pre-indexing and avoiding m×n API calls. Both ACP (OpenAI) and UCP (Google) standardize product data but use different schemas.

- **What does AP2 add to payments?**
  It introduces **scoped payment mandates** with fields for authorizing party, spend ceiling, revocation URL, and user consent proof—enabling safer, delegated payments for agents.

## Notable Details
- ~45% of sessions on major assistants (ChatGPT, Gemini) involve shopping; the agentic commerce market is estimated at $7B today, projected to reach $65B by 2030.
- Demo: Ginny (a cat-themed bakery agent) runs on **Cerebras at 3,000 tokens/sec**, showing MCP tool calls, A2A messages, UCP/ACP checkout states, and AP2 token flows with a live inspector.
- **Payment statuses** in UCP/ACP: `not_ready_for_payment`, `ready_for_payment`, `completed`.
- **Eval priorities**: Behavior (e.g., blocking off-topic queries), protocol compliance (e.g., feed schema adherence), and latency (retail abandonment risk).
- Open questions: ACP vs. UCP convergence, identity/consent standards, and multi-agent checkout delegation.

## Actionable Takeaways
- Adopt **MCP/A2A/ACP/UCP** for agentic commerce to avoid brittle browser automation and enable direct API-driven flows.
- Use **product feeds** (not search) to scale with assistants; prepare for schema differences (UCP, ACP, Meta).
- Implement **AP2-style scoped mandates** for payments to balance autonomy and safety.
- Write **evals early** for behavior, protocol compliance, and latency to prevent production failures.
- Monitor **ACP/UCP convergence** and identity standards as the space matures.

## People, Companies, Tools, And Links Mentioned
- Ahnaf Prio
- Best Buy
- OpenAI (ACP)
- Google (UCP, AP2, Google Pay)
- Meta (Meta Commerce, product feeds)
- Chipotle
- Cerebras
- ChatGPT Shopping
- Google AI Mode
- Microsoft Copilot
- Gopuff
- Grok
- [GitHub repo with demo, templates, and evals](https://github.com/ahnafyy)

## Reading Priority

Medium – A concrete, technical breakdown of the emerging agentic commerce stack, with actionable protocols, demos, and cautionary lessons for practitioners.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Enterprise AI|Enterprise AI]], [[topics/Web Platform|Web Platform]]
- Speaker: [[people/ahnaf-prio|Ahnaf Prio]]
