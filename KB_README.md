# AI Knowledge Base

Private, persistent store of AI transcripts, reading notes, and the Obsidian
graph built from them. Multiple workflows publish into it;
[ai-weekly-reads](https://github.com/sophiamyang/ai-weekly-reads) is the first
and is not privileged — anything that honors the contract below can write here.

Raw transcripts are verbatim third-party content. **Keep this repo private.**

## Layout

| Folder | Holds | Written by |
|---|---|---|
| `raw_transcripts/` | Canonical verbatim transcript/text, one file per item | Publishers |
| `resources/` | Clean notes — summary plus frontmatter, one per item | Publishers |
| `weekly_books/` | Weekly Markdown books for Obsidian | `ai-weekly-reads` only |
| `sources/`, `people/`, `topics/`, `indexes/` | Generated Obsidian graph hubs | Generated — do not hand-edit |

`Home.md`, `README.md`, and `templates/` are tracked by the `ai-weekly-reads`
repo and ignored here.

## Publishing contract

A publisher needs to get three things right. Everything else is generated.

### 1. Stable IDs

Every item carries a 16-character id: `sha256(key).hexdigest()[:16]`, where
`key` is the most durable identifier available — a feed GUID, then a permalink,
then the media URL, and only then a composite of feed, title, and date.

**Do not key on the title.** Publishers edit titles after release, and a
title-derived id then changes, so the next run treats an item it has already
processed as new and re-transcribes it.

The id is both the dedup key and the filename suffix. Before processing
anything, check whether `resources/` already has a note with that id — the
whole point of persisting this repo is to skip work already done.

### 2. Filenames

```
raw_transcripts/YYYY-MM-DD-<source_type>-<slug>-<id>.md
resources/<slug>-<id>.md
```

The date is when the item was ingested, not when it was published.

### 3. Frontmatter

Both note types are Markdown with YAML frontmatter. The graph generators and
the audit script read these fields by name, so a publisher that omits them
produces notes that exist but never connect to anything.

**`resources/` note:**

```yaml
---
id: "fb91d441a98ab78e"     # sha256(key)[:16]
title: "..."
aliases: ["..."]           # Obsidian link aliases
type: "resource"
source: "podcast"          # source_type: podcast | youtube | ...
source_name: "Lex Fridman Podcast"
content_type: "podcast"
speakers: ["..."]          # optional; drives people/ hubs
url: "https://..."         # the item
origin: "https://..."      # the feed or channel it came from
published: "2026-08-26"    # publication date, not ingest date
transcript_method: "..."   # how the text was obtained; useful when auditing
status: "summarized"       # or needs_summary
priority: "medium"
send_to_kindle: true
raw_transcript: "raw_transcripts/<file>.md"
created: "2026-08-28"      # ingest date
tags: ["topic/coding-agents"]   # topic/ prefix drives topics/ hubs
---
```

The body is the summary, preceded by an Obsidian link to the raw transcript.

**`raw_transcripts/` note:** the same identity fields (`id`, `title`, `aliases`,
`source`, `source_name`, `content_type`, `url`, `origin`, `created`) with
`type: "raw-transcript"`, then `# <title> Raw Transcript` and the verbatim text.

### Generated hubs

`sources/`, `people/`, `topics/`, and `indexes/` are derived from resource
frontmatter, not authored. A publisher that writes valid frontmatter gets them
for free; regenerate with `scripts/obsidian_graph.py` in `ai-weekly-reads`, or
reimplement from the fields above.

## Cloud session setup

This repo is used as a *nested* git repo — its `.git` is moved into
`knowledge_base/` inside a publisher's checkout, so the publisher's own repo
never tracks transcripts. From an `ai-weekly-reads` checkout:

```bash
git clone https://github.com/sophiamyang/ai-knowledge-base /tmp/kb && \
  mv /tmp/kb/.git knowledge_base/.git && rm -rf /tmp/kb && \
  git -C knowledge_base checkout -- . 2>/dev/null || true

# Assert the fetch refspec so `origin/main` exists and `git status` can report
# ahead/behind. A plain clone sets this, but a `.git` built any other way
# (init + remote add + pull) leaves it unset, and then the only way to check
# whether the KB is pushed is `git ls-remote`. Idempotent.
git -C knowledge_base config remote.origin.fetch '+refs/heads/*:refs/remotes/origin/*' && \
  git -C knowledge_base fetch origin
```

Verify the restore before running anything — `git -C knowledge_base status -sb`
should print `## main...origin/main`, and `resources/` should already be
populated. An empty `resources/` means the restore failed, and the run will
re-transcribe everything it has already done.

An existing checkout from before the rename still points at
`ai-weekly-reads-kb`. GitHub redirects it, but update it anyway:

```bash
git -C knowledge_base remote set-url origin https://github.com/sophiamyang/ai-knowledge-base
```

## Concurrency

There is no locking. Two workflows pushing at once will collide on
`indexes/` and the other generated hubs, which every publisher rewrites. Pull
before writing, and prefer staggered schedules over simultaneous runs.

After a run, commit and push from `knowledge_base/`.
