# AI Weekly Reads Knowledge Base

Private persistent state for the [ai-weekly-reads](https://github.com/sophiamyang/ai-weekly-reads) pipeline.

This repo is nested at `knowledge_base/` inside an `ai-weekly-reads` checkout. It stores:

- `raw_transcripts/` — canonical raw transcript/text store
- `resources/` — clean reading notes (one per summarized item)
- `weekly_books/` — weekly Markdown books for Obsidian
- `sources/`, `people/`, `topics/`, `indexes/` — generated Obsidian graph hubs

`Home.md`, `README.md`, and `templates/` are tracked by the main repo and ignored here.

Raw transcripts are verbatim third-party content — keep this repo **private**.

## Cloud session setup

From an `ai-weekly-reads` checkout:

```bash
git clone https://github.com/sophiamyang/ai-weekly-reads-kb /tmp/kb && \
  mv /tmp/kb/.git knowledge_base/.git && rm -rf /tmp/kb && \
  git -C knowledge_base checkout -- . 2>/dev/null || true
```

After a weekly run, commit and push from `knowledge_base/`.
