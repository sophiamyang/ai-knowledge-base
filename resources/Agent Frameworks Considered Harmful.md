---
id: "9642ca6ea29ef8ca"
title: "Agent Frameworks Considered Harmful — Rémi Louf, .txt"
aliases:
  - "Agent Frameworks Considered Harmful — Rémi Louf, .txt"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Rémi Louf, CEO of .txt"
url: "https://www.youtube.com/watch?v=KHudyx5wW3U"
origin: "https://www.youtube.com/watch?v=KHudyx5wW3U"
published: "2026-08-22"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-agent-frameworks-considered-harmful-r-mi-louf-txt-9642ca6ea29ef8ca.md"
created: "2026-08-29"
tags:
  - "topic/ai-agents"
  - "topic/developer-tools"
  - "topic/model-inference"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-agent-frameworks-considered-harmful-r-mi-louf-txt-9642ca6ea29ef8ca|Agent Frameworks Considered Harmful — Rémi Louf, .txt raw transcript]]

# Agent Frameworks Considered Harmful — Rémi Louf, .txt

Source: youtube
Original link: https://www.youtube.com/watch?v=KHudyx5wW3U

## One-Sentence Takeaway
Agent frameworks often overcomplicate orchestration; a minimal runtime built on events, content-addressed prompts, and typed boundaries can reliably run agents without graphs or code.

## Short Summary
Rémi Louf argues that most agent frameworks force unnecessary complexity (e.g., graph-based orchestration) and obscure debugging by hiding the true prompt and reasoning from the user. His alternative is a lightweight runtime where agents are defined in Markdown, subscribe to typed events, and log everything in an append-only, causally linked store. Prompts are content-addressed (hashed by component), enabling precise diffs and replays across models. The result: 20 production agents at .txt built by non-engineers, with open-source models replacing third-party APIs.

The core insight is that agent reliability hinges on observability and strict boundaries (typed tool calls and events), not on framework features. Louf’s system treats agents like processes in a kernel, with the runtime enforcing isolation and journaling, while agent definitions remain userland artifacts.

## Featured Speakers
- Rémi Louf, CEO of .txt

## Main Ideas
- **Events over graphs**: Agents should subscribe to typed events (e.g., `voice_note.processed`) rather than live in a graph with explicit edges; fan-in/fan-out and topology emerge automatically from the log.
- **Content-addressed prompts**: Store each prompt component (system message, tools, user input) as a hash; prompts become lists of hashes, enabling exact diffs between runs and replays against different models.
- **Strict boundaries**: Typed tool calls and typed events prevent malformed actions (20% of Louf’s early events were rejected without them) and make bad actions impossible, not just unlikely.
- **Observability as a first-class concern**: An append-only, causally linked event log and the ability to reconstruct the exact prompt sent to the model are critical for debugging and cost control.

## Questions And Answers
- **Why not use existing agent frameworks?**
  Frameworks often bury prompts in code, lack fine-grained observability, and require graph maintenance; Louf’s approach separates the runtime (kernel) from agent definitions (userland), avoiding these issues.

- **How do you debug agent failures?**
  The event log links causes to effects, and content-addressed prompts let you diff runs to see which component (e.g., a tool description) changed.

## Notable Details
- Louf’s runtime emerged from failures: duplicates → proper queue with attempt counting; lost voice notes → append-only log; broken prompts → content-addressed storage.
- Open-source models replaced third-party APIs for his use case (non-coding tasks), even running locally on a laptop.
- Structured outputs (a .txt specialty) were critical: 20% of events were malformed without typed boundaries.
- Agents are defined in Markdown files dropped into a folder, enabling non-engineers to contribute (20 agents now run at .txt).
- Replays allow cost comparison across models by rebuilding old requests from the graph.

## Actionable Takeaways
- Start with events and typed boundaries before adopting a heavy framework; build a minimal runtime to learn what you truly need.
- Treat prompts as code: version, diff, and content-address components to enable auditing and replays.
- Prioritize observability: log everything causally and ensure you can reconstruct the exact input the model saw.
- Dogfood your own agent infrastructure; frameworks often reveal gaps only when used in production.

## People, Companies, Tools, And Links Mentioned
- Rémi Louf
- .txt ([ddotxt.ai](https://ddotxt.ai))
- [The Typical Set](https://thetypicalset.com)
- [@remilouf on X](https://x.com/remilouf)
- [Rémi Louf on LinkedIn](https://www.linkedin.com/in/remilouf/)
- Codex
- Anthropic
- OpenAI
- Opus 4.6
- Git
- Nix
- llama.cpp

## Reading Priority

Medium – A pragmatic, engineering-focused take on agent reliability with concrete mechanisms and production lessons.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/AI Agents|AI Agents]], [[topics/Developer Tools|Developer Tools]], [[topics/Model Inference|Model Inference]]
- Speaker: [[people/r-mi-louf|Rémi Louf]]
