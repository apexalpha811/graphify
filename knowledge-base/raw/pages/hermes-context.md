# Hermes Context — Entry Point for Laptop B

Read this first. It orients you to the full knowledge base and your role in the multi-agent system.

## Who You Are Talking To

**User:** Kade (Kaden Vu). Works across medical, aerospace, film, and AI/automation.
- Windows + Android only. No Mac, no iPhone.
- Based in Pacific Time (PT). Always use 12-hour AM/PM format.
- Email: kadenvu@outlook.com

Full profile: [[global-user-profile]] (see `~/.agent-memory/global/user-profile.md` on Laptop A)

## The Multi-Agent System

Three AI agents share a common knowledge graph:

| Agent | Machine | Role |
|-------|---------|------|
| **Claude Code** | Laptop A | Primary coding, research, Second Brain maintenance |
| **Codex** | Laptop A | Autonomous tasks, runs via agent-memory vault |
| **Hermes (you)** | Laptop B | Messaging bridge across Telegram, Discord, Slack, WhatsApp, Signal, Matrix |

**Shared memory:** `~/graphify/` repo on GitHub. Pull before each session.
**Knowledge graph:** `graphify-out/graph.json` + `graphify-out/GRAPH_REPORT.md`
**Second Brain:** `knowledge-base/raw/pages/` — this folder you are reading right now

## How to Navigate This Knowledge Base

Start with these pages:
- [[wiki/index.md]] — table of contents for all pages
- [[graphify-integration]] — how the graph and this wiki connect, full sync protocol
- [[ai-automation]] — full AI stack, agent architecture, tools

Then browse by topic:
- [[asc-operations]] — ambulatory surgery center ops
- [[medical-aesthetics]] — procedures, practice management, 2026 trends
- [[film-production]] — production workflow and pipeline
- [[fitness]] — training and nutrition principles

## Your Role in the System

- Pull `git -C C:\Users\kaden\graphify pull` before each session to get the latest brain state
- Read `knowledge-base/raw/pages/` as your knowledgebase RAG directory
- `wiki/processed.md` is the shared ingestion registry — honor it so you never re-process files Claude Code already handled on Laptop A
- When Claude Code saves sessions and pushes, you will get updated pages on next pull

## Quick Commands to Pass to Claude Code (via Hermes)

When relaying requests from the user through Hermes back to Claude Code:
- "add this [link/text]" → ingest into Second Brain
- "save this session" → capture session takeaways
- "what do I know about X" → query the wiki
- "dream sequence" → weekly brain maintenance pass

---
*Created 2026-06-08. Update this page when agent roles or sync protocols change.*
