# AI & Automation

Personal stack and working knowledge of AI tools, agents, and automation patterns.

## My Stack (Laptop A)

| Tool | Role |
|------|------|
| **Claude Code** | Primary coding and knowledge agent. Reads global CLAUDE.md + project CLAUDE.md. Handles code, research, file ops, Second Brain maintenance |
| **Codex** | Parallel agent. Reads agent-memory vault via Obsidian MCP junction. Used for longer autonomous tasks |
| **Hermes** | Messaging bridge (Telegram, Discord, Slack, WhatsApp, Signal, Matrix). Lives on Laptop B |
| **Graphify** | Knowledge graph builder. Scans agent-memory vault, outputs graph.json + GRAPH_REPORT.md. Auto-rebuilds via git hook |
| **Obsidian** | Local reading UI for agent-memory vault and Second Brain. Graph view shows connections |
| **MCP (Model Context Protocol)** | Anthropic standard for connecting AI agents to tools and data sources |

## Agent Memory Architecture
- `~/.agent-memory/` — shared vault. Claude Code, Codex, and Hermes all read from it
- `~/graphify/` — knowledge graph outputs + this Second Brain (synced to GitHub)
- Laptop B pulls from GitHub. One git push = all agents current
- See [[graphify-integration]] for full sync protocol

## Key Concepts

### Agentic AI
AI systems that can plan, use tools, and take multi-step actions autonomously. The shift from "chatbot" to "agent" is the defining move of 2024-2026.

### MCP (Model Context Protocol)
Anthropic's open standard for connecting LLMs to external tools, data, and services. Replaces ad-hoc tool integrations. MCP servers expose tools that agents call natively.

### RAG vs LLM Wiki
- **RAG** (Retrieval Augmented Generation): retrieve chunks at query time, no accumulation
- **LLM Wiki** (Karpathy pattern): LLM builds and maintains a persistent wiki. Knowledge compounds. See [[second-brain-overview]] for this system

### Multi-Agent Patterns
- **Parallel agents**: same task, multiple agents, merge results (used in graphify extraction)
- **Sequential agents**: output of one feeds next
- **Orchestrator + workers**: one agent coordinates, spawns subagents for subtasks

## 2026 Landscape
- 62% of organizations experimenting with or scaling AI agents (McKinsey 2026)
- Shift from single-model to multi-agent orchestration
- Key frameworks: LangChain, CrewAI, AutoGen, n8n (open source automation)
- Governance becoming critical: observability, audit logs, escalation paths

## Principles I Follow
- Give agents the smallest amount of freedom that still delivers the outcome
- Verify work before reporting done — never "this should work"
- Judgment in commands (CLAUDE.md rules), mechanism in hooks (automated behaviors)
- Session state in tasks, durable knowledge in memory vault

---
*Seeded 2026-06-08. Drawn from this session + agent-memory vault.*
