---
id: "386fd20be2f34c8b"
title: "Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma"
aliases:
  - "Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Jesse Lumarie – Software Engineer, Figma"
url: "https://www.youtube.com/watch?v=ZIYYsAzaLlA"
origin: "https://www.youtube.com/watch?v=ZIYYsAzaLlA"
published: "2026-08-28"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-building-the-engine-while-flying-the-plane-launching-the-figma-mcp-server-jesse--386fd20be2f34c8b.md"
created: "2026-08-29"
tags:
  - "topic/developer-tools"
  - "topic/model-inference"
  - "topic/enterprise-ai"
  - "topic/ai-infrastructure"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-building-the-engine-while-flying-the-plane-launching-the-figma-mcp-server-jesse--386fd20be2f34c8b|Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma raw transcript]]

# Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma

Source: youtube
Original link: https://www.youtube.com/watch?v=ZIYYsAzaLlA

## One-Sentence Takeaway
Figma’s MCP server rapidly became one of its fastest-growing products by solving the core tension between pixel-perfect design translation and enterprise-grade code reuse, while navigating a shifting spec and uneven client support.

## Short Summary

Figma built its first MCP server in three months as a side project, targeting non-designers who needed to pull design context into coding agents. The team chose a React/Tailwind representation of Figma’s scene graph on the hunch that models were most familiar with it, achieving pixel-perfect output but soon realizing enterprises needed pointers to their own accessible, internationalized components via Code Connect.

The project shipped locally first to validate demand, then remotely after OAuth was added to the spec. Early challenges included deprecated transports, uneven client support, and the need to automate evaluations—after a painful manual grading session, they moved to LLM-judged evals running hundreds of times a week. The server’s success hinged on representation choices, compatibility workarounds, and a focus on practical developer workflows.

## Featured Speakers
- Jesse Lumarie – Software Engineer, Figma

## Main Ideas
- Representing Figma’s C++ scene graph as React/Tailwind code improved model comprehension and output fidelity, as models were heavily exposed to this syntax during training.
- Pixel-perfect translation is insufficient for enterprises, which require integration with their own battle-tested, accessible, and internationalized components; Code Connect provides pointers to real components instead of raw markup to solve this.
- Early MCP spec instability and uneven client support forced the team to maintain a compatibility matrix and work around missing features like elicitation and sampling by hacking tool-based alternatives.
- Manual evaluation was unsustainable; automating evals with LLM judges and hundreds of weekly runs enabled rapid iteration on prompts and representations.
- Launching a local server first allowed Figma to validate product-market fit quickly, respect enterprise data locality concerns, and avoid early OAuth complexity, before transitioning to a remote server.

## Questions And Answers
- **Why not use images alone for design-to-code translation?**
  Early in 2025, agents struggled to convert images directly to HTML/CSS, so images were used as supplementary context alongside code, not as the primary input.

- **How did Figma handle the lack of client support for elicitation and sampling?**
  They mimicked elicitation by prompting users to confirm component mapping and used tool calls to have the agent scan the codebase for matches, effectively replicating sampling behavior.

- **What drove the decision to launch locally before remotely?**
  The local server was the fastest path to user feedback, avoided OAuth complexity, and addressed enterprise preferences for keeping data on-device.

## Notable Details
- Base64-encoded inline images bloated the context window and were abandoned.
- The team’s first eval took two hours to grade manually in a spreadsheet, prompting a shift to automated LLM-judged evaluations.
- A client compatibility matrix was actively maintained in March 2025 to track uneven feature support across tools like Claude Desktop, VS Code, and OpenAI.
- Optional query arguments (e.g., language/framework) were added to tool calls to infer user context, despite agents sometimes lying.
- The MCP Inspector (open-source) was critical for debugging server-client interactions.

## Actionable Takeaways
- Prefer representations models are most familiar with (e.g., React/Tailwind) for higher-fidelity outputs, but ensure they align with real-world constraints like accessibility and internationalization.
- Automate evaluations early to avoid manual bottlenecks; LLM judges can scale grading for frequent iterations.
- When specs or clients are unstable, build for the most capable client first (e.g., VS Code) and work around gaps with tool-based hacks.
- Launch locally to validate demand and reduce friction, especially for enterprise users with data locality concerns.
- Monitor optional signals (e.g., framework hints) to diagnose underperforming user segments.

## People, Companies, Tools, And Links Mentioned
- [Figma](https://www.figma.com)
- [MCP (Model Context Protocol) spec](https://github.com/modelcontextprotocol/spec)
- [Anthropic](https://www.anthropic.com)
- [Claude Desktop](https://claude.ai)
- [VS Code](https://code.visualstudio.com)
- [OpenAI](https://openai.com)
- [MCP Inspector](https://github.com/modelcontextprotocol/inspector)
- [Code Connect](https://www.figma.com/code-connect)
- [Figma Slides](https://www.figma.com/slides)
- [Electron](https://www.electronjs.org)

## Reading Priority

Medium – A concrete, firsthand account of building a production MCP server, with actionable insights on representation choices, client compatibility, and evaluation automation.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Developer Tools|Developer Tools]], [[topics/Model Inference|Model Inference]], [[topics/Enterprise AI|Enterprise AI]], [[topics/AI Infrastructure|AI Infrastructure]]
- Speaker: [[people/jesse-lumarie-software-engineer|Jesse Lumarie – Software Engineer]]
