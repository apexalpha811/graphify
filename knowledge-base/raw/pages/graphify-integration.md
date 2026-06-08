# Graphify Integration & Laptop B Sync Protocol

## What Graphify is

Graphify builds a knowledge graph from the agent memory vault (`~/.agent-memory`) and stores the outputs in `~/graphify/graphify-out/`. It extracts entities, relationships, and communities from markdown files and produces a queryable graph.

## Graphify Bridge Rule

After every `/graphify .` run:
1. Copy `graphify-out/GRAPH_REPORT.md` into `knowledge-base/raw/`
2. Ingest it as a new source (say "add this" pointing at the copied file)
3. I will write/update a page in `raw/pages/` summarizing any new architecture decisions or community insights surfaced in the report
4. Register it in `wiki/processed.md`

This means every time the graph rebuilds, the Second Brain absorbs the latest picture of how your agents and projects are connected.

## Laptop B Sync — Hermes Feed

**Repo:** https://github.com/apexalpha811/graphify.git

**What Hermes gets on every pull:**
- `graphify-out/GRAPH_REPORT.md` — code knowledge graph
- `knowledge-base/raw/pages/` — all Second Brain content pages
- `knowledge-base/wiki/index.md` — table of contents
- `knowledge-base/wiki/log.md` — activity history
- `knowledge-base/wiki/processed.md` — shared ingestion registry (Hermes never re-ingests files already processed on Laptop A)

**Hermes context:** Hermes reads `knowledge-base/raw/pages/` as its knowledgebase directory. Point Hermes at this folder on first load for a curated entry point into the full wiki.

## Sync Cadence

| Event | Action |
|-------|--------|
| After every Dream Sequence | `git push` from `~/graphify/` |
| After every "save this session" | `git push` from `~/graphify/` |
| After any manual ingest | `git push` from `~/graphify/` |
| Hermes on startup | `git -C C:\Users\kaden\graphify pull` |

Git commit message format: `brain-sync: [YYYY-MM-DD] dream|session|ingest`

## Auto-Rebuild Hook

The post-commit hook in `~/.agent-memory/.git/hooks/post-commit` automatically rebuilds the graph whenever new memories are committed. No manual `/graphify .` needed for routine memory saves.
