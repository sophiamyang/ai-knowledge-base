---
id: "91e6311cec48079e"
title: "Inside 847 Production Clinical AI Notes — Sebastian Fox, Composo"
aliases:
  - "Inside 847 Production Clinical AI Notes — Sebastian Fox, Composo"
type: "resource"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
speakers:
  - "Sebastian Fox, Composo"
url: "https://www.youtube.com/watch?v=yqF6XhzbWBk"
origin: "https://www.youtube.com/watch?v=yqF6XhzbWBk"
published: "2026-08-22"
transcript_method: "gemini_youtube_transcribe"
status: "summarized"
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/2026-08-29-youtube-inside-847-production-clinical-ai-notes-sebastian-fox-composo-91e6311cec48079e.md"
created: "2026-08-29"
tags:
  - "topic/model-evaluation"
  - "topic/ai-safety"
  - "topic/enterprise-ai"
  - "topic/ai-infrastructure"
---

Raw transcript: [[raw_transcripts/2026-08-29-youtube-inside-847-production-clinical-ai-notes-sebastian-fox-composo-91e6311cec48079e|Inside 847 Production Clinical AI Notes — Sebastian Fox, Composo raw transcript]]

# Inside 847 Production Clinical AI Notes — Sebastian Fox, Composo

Source: youtube
Original link: https://www.youtube.com/watch?v=yqF6XhzbWBk

## One-Sentence Takeaway
Production ambient clinical AI scribes produce dangerous errors in ~5% of notes, with ~20% missing critical details, because current verification systems cannot reliably judge *what matters* in context.

## Short Summary

Ambient AI scribes in healthcare—already used in ~33% of US practices—generate notes with serious errors (e.g., omitting red-flag symptoms like jaw pain in giant-cell arteritis) that often go unnoticed. A large real-world study found ~1 in 20 notes contained errors severe enough to harm patients, ~1 in 5 omitted important information, and ~1 in 10 included hallucinations, yet most incidents are unreported.

The root issue is that verification systems (e.g., frontier models with rubrics) struggle to distinguish *contextually critical* omissions or distortions (e.g., "France" vs. "Lake Malawi" in a travel history) from harmless ones. Static rubrics or fine-tuned models cannot encode tacit, evolving domain judgment, so even sophisticated checkers miss ~20% of serious errors.

## Featured Speakers
- Sebastian Fox: Medical doctor and founder of Composo, building AI evaluation systems for high-stakes domains.

## Main Ideas

- **Error prevalence and stakes**: In production, ~5% of ambient scribe notes contain errors that could cause significant harm, with ~20% omitting important details and ~10% hallucinating content. These errors are underreported because they blend into records without triggering incidents.
- **Verification’s blind spot**: Current evaluation systems (e.g., frontier models + rubrics) excel at detecting explicit mismatches between transcripts and notes but fail at judging *contextual importance*—e.g., whether omitting "Lake Malawi" (schistosomiasis risk) vs. "France" (irrelevant) in a travel history matters.
- **Tacit, moving standards**: Domain expertise involves implicit, context-dependent judgment (e.g., "sudden onset" vs. "it just happened" for a headache) that cannot be fully codified in static rules. Guidelines, models, and even expert opinions evolve, making fixed rubrics or fine-tuned weights inadequate.
- **Discover-capture-calibrate loop**: Effective evaluation requires (1) *discovering* failure modes from real outputs (not synthetic tests), (2) *capturing* expert judgments on those cases (including reasoning), and (3) *calibrating* each output against retrieved, relevant examples and corrections—assembling a dynamic, case-specific standard.
- **Evaluation as a process**: Evaluation cannot be a one-time build; it must continuously adapt as new failure modes emerge and standards shift. Free-form expert comments on real outputs are the raw material for this evolution.

## Questions And Answers

**Q: Why do even "good" ambient scribe notes contain dangerous errors?**
A: Models often add, change, or omit details that *seem* plausible but flip meaning (e.g., inferring "abrupt sudden onset" from "it just happened") or drop critical context (e.g., jaw pain in a headache case). These errors are hard to catch because they require domain-specific judgment about what matters in a given context.

**Q: Why do verification systems miss ~20% of serious errors?**
A: Verifiers can spot differences between transcripts and notes but cannot reliably determine which differences are *medically significant*. For example, omitting "Lake Malawi" (diagnostic) vs. "France" (irrelevant) in a travel history requires contextual reasoning that static rubrics or models lack.

**Q: How can evaluation systems improve?**
A: Replace static rubrics with a dynamic loop: (1) mine real outputs for failure modes, (2) collect expert judgments (with reasoning) on those cases, and (3) for each new output, retrieve and apply the most relevant judged examples and guidelines to calibrate its evaluation.

## Notable Details

- **Real-world error examples**:
  - Omission: Jaw pain (critical for giant-cell arteritis) missing from a headache note.
  - Hallucination: A patient with tonsillitis recorded as having chest pain, angina, diabetes, and a fake hospital address.
  - Overinference: "It just happened" (patient’s words) → "abrupt sudden onset" (implies potential brain bleed).
  - Meaning flip: Patient and doctor agreed to "try antibiotics first" → note records "Arrange tests today."
- **Transcription-layer errors**: Sound-alike mishearings (e.g., Humalog → Humulin; hyperthyroidism → hypothyroidism) or dropped negations (e.g., "no evidence of cancer" → "evidence of cancer").
- **Performance gap**: A frontier-model judge with a rubric and deterministic checks still missed ~20% of serious errors in a dataset of production notes. The discover-capture-calibrate loop reduced misses significantly by grounding judgments in retrieved, relevant examples.

## Actionable Takeaways

- **Audit real outputs**: Start by having domain experts review and comment on real-world outputs to surface failure modes you didn’t anticipate.
- **Build a dynamic evaluation loop**: Use expert judgments on real cases to assemble context-specific standards for each output, rather than relying on static rubrics or fine-tuned models.
- **Prioritize contextual retrieval**: For each output, retrieve and apply the most relevant judged examples, corrections, and guidelines to guide evaluation.
- **Treat evaluation as ongoing**: Continuously update your failure mode ontology and judgment dataset as models, guidelines, and domain practices evolve.
- **Watch for silent failures**: Assume underreporting in high-stakes domains; proactively hunt for errors that don’t trigger incidents (e.g., omissions in clinical notes).

## People, Companies, Tools, And Links Mentioned
- Sebastian Fox
- [Composo](https://composo.ai)
- [Sebastian Fox on LinkedIn](https://www.linkedin.com/in/seb--fox/)

## Reading Priority

Medium – This reveals a critical, underreported flaw in high-stakes AI deployment (healthcare) and offers a concrete, actionable framework for evaluation that applies to any domain where contextual judgment matters.

## Connections

- Source: [[sources/AI Engineer|AI Engineer]]
- Topics: [[topics/Model Evaluation|Model Evaluation]], [[topics/AI Safety|AI Safety]], [[topics/Enterprise AI|Enterprise AI]], [[topics/AI Infrastructure|AI Infrastructure]]
- Speaker: [[people/sebastian-fox|Sebastian Fox]]
