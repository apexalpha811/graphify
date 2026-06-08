# Graph Report - .  (2026-06-08)

## Corpus Check
- 168 files · ~117,047 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 184 nodes · 190 edges · 23 communities (15 shown, 8 thin omitted)
- Extraction: 82% EXTRACTED · 18% INFERRED · 0% AMBIGUOUS · INFERRED: 34 edges (avg confidence: 0.84)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Agent Memory Vault Structure|Agent Memory Vault Structure]]
- [[_COMMUNITY_Multi-Agent System|Multi-Agent System]]
- [[_COMMUNITY_CCS Pain Chart Form|CCS Pain Chart Form]]
- [[_COMMUNITY_Claude Code Config|Claude Code Config]]
- [[_COMMUNITY_A-NATION Brand Colors|A-NATION Brand Colors]]
- [[_COMMUNITY_A-NATION Brand Guidelines|A-NATION Brand Guidelines]]
- [[_COMMUNITY_Firecrawl API & Features|Firecrawl API & Features]]
- [[_COMMUNITY_Memory Design Decisions|Memory Design Decisions]]
- [[_COMMUNITY_Global Agent Rules|Global Agent Rules]]
- [[_COMMUNITY_Knowledge Vault Structure|Knowledge Vault Structure]]
- [[_COMMUNITY_Firecrawl Scraper|Firecrawl Scraper]]
- [[_COMMUNITY_CCS Form Fields|CCS Form Fields]]
- [[_COMMUNITY_Obsidian Config|Obsidian Config]]
- [[_COMMUNITY_Design Systems|Design Systems]]
- [[_COMMUNITY_Session Management|Session Management]]
- [[_COMMUNITY_Hermes Agent|Hermes Agent]]
- [[_COMMUNITY_Firecrawl Brand Voice|Firecrawl Brand Voice]]
- [[_COMMUNITY_Firecrawl Tech Stack|Firecrawl Tech Stack]]
- [[_COMMUNITY_Daily & Journal|Daily & Journal]]
- [[_COMMUNITY_Goals & Reference|Goals & Reference]]
- [[_COMMUNITY_Archive|Archive]]
- [[_COMMUNITY_Logs & Meta|Logs & Meta]]
- [[_COMMUNITY_Projects|Projects]]

## God Nodes (most connected - your core abstractions)
1. `Culver City Surgical Pain Chart Form 2026 (PI Cases, English)` - 14 edges
2. `Firecrawl-copycat` - 11 edges
3. `Culver City Surgical Pain Chart Form 2026 (PI Cases, English)` - 9 edges
4. `Claude Code Agent` - 7 edges
5. `4. Typography` - 7 edges
6. `Knowledge Vault README` - 7 edges
7. `Decision: Memory Loading via Hooks + Slash Commands` - 7 edges
8. `Knowledge Tree — General Memory` - 7 edges
9. `Decision: Memory Loading via Hooks + Slash Commands` - 7 edges
10. `build_pdf.py` - 6 edges

## Surprising Connections (you probably didn't know these)
- `Claude Code Agent` --coexists_with--> `Codex Agent`  [INFERRED]
  agents/claude-code/README.md → AI/Codex/README.md
- `Global User Profile` --conceptually_related_to--> `Session Auto-Resume at 5-Hour Reset`  [INFERRED]
  agents/claude-code/README.md → .agent-memory/global/session-auto-resume.md
- `Agent Memory Vault` --implements--> `Multi-Agent Vault Sharing Pattern`  [EXTRACTED]
  agents/claude-code/README.md → CLAUDE.md
- `Codex Agent` --reads_from--> `Agent Memory Vault`  [EXTRACTED]
  AI/Codex/README.md → agents/claude-code/README.md
- `Global User Profile` --describes--> `Kade (User)`  [EXTRACTED]
  agents/claude-code/README.md → .agent-memory/global/user-profile.md

## Import Cycles
- None detected.

## Communities (23 total, 8 thin omitted)

### Community 0 - "Agent Memory Vault Structure"
Cohesion: 0.11
Nodes (23): Agent Memory Vault — Shared AI Knowledge Base, Agent Memory Vault Index, /check_reset Slash Command, Session Auto-Resume at 5-Hour Reset, ccusage SessionStart Hook, Time Format Rule — 12-Hour Pacific Time, Timezone Setting — Pacific Time (PST/PDT), /commit_obsidian Slash Command (+15 more)

### Community 1 - "Multi-Agent System"
Cohesion: 0.15
Nodes (15): Agent Memory Vault, Claude Code Agent, Codex Agent, Codex Operating Hub, Design Systems Folder, Hermes Agent, Hermes Cron Deduplication Pattern, Hermes Delivery Configuration (+7 more)

### Community 2 - "CCS Pain Chart Form"
Cohesion: 0.13
Nodes (15): Culver City Surgical Pain Chart Form 2026 (PI Cases, English), Field Structure, Pages, Pain Assessment Chart, Patient Information, Question 11, Question 12, Question 13 (+7 more)

### Community 3 - "Claude Code Config"
Cohesion: 0.20
Nodes (14): Agent Memory Vault — Master Index, Claude Code Agent — Vault Instructions, Hermes Agent — Vault Instructions, Session Auto-Resume at 5-Hour Reset, ccusage — Local Claude Usage / Session Window Tracking, Global Rules Apply to ALL Agents, Hermes: Persistent Cross-Run Dedup with seen_*.json, liteparse — Primary Document Parser (+6 more)

### Community 4 - "A-NATION Brand Colors"
Cohesion: 0.14
Nodes (13): 3. Color Palette, A-NATION Media — Brand Design Guidelines, anation-brand-guidelines (source file), Brand Voice Principles, 9. Digital Applications, Do Say, Don't Say, Iconography (+5 more)

### Community 5 - "A-NATION Brand Guidelines"
Cohesion: 0.14
Nodes (14): A-NATION Media Brand Design Guidelines, anation-claude-prompt-template, 10. Application Examples, Body Font Montserrat, 1. Brand Overview, Iconography, 5. Imagery & Iconography, Photography Style (+6 more)

### Community 6 - "Firecrawl API & Features"
Cohesion: 0.15
Nodes (13): API Reference, Configuration, Features, GET/POST scrape endpoint, How it works, License, Firecrawl-copycat, Quick Start (+5 more)

### Community 7 - "Memory Design Decisions"
Cohesion: 0.22
Nodes (11): ADR-Style Decision Format for Vault Decisions, Slash Command: /commit_obsidian, Principle: Enforcement Over Best-Effort Prompt Routines, Design Principle: Judgment in Slash Commands, Mechanism in Hooks, Knowledge Filing: Folder=Type, Tags=Domain, Slash Command: /save_obsidian, SessionEnd Hook — Auto Commit + Push Vault, SessionStart Hook — Auto Pull + Vault Inject (+3 more)

### Community 8 - "Global Agent Rules"
Cohesion: 0.22
Nodes (11): Agent Memory Vault, Claude Code Session Hooks (SessionStart/SessionEnd), Claude Code Slash Commands, Decision: Enforce Vault Load/Save via Hooks and Slash Commands, Knowledge Decisions README, Knowledge People README, Knowledge Preferences README, Knowledge Vault README (+3 more)

### Community 9 - "Knowledge Vault Structure"
Cohesion: 0.27
Nodes (10): Architecture (Approach 2 - HTML is the source), CCS Pain Chart Assets, CCS Pain Chart Browser Behavior, Culver City Surgical Pain Chart Form 2026 (PI Cases, English), Deploying Online (Vercel), CCS Pain Chart Field Structure, CCS Pain Chart Pages, CCS Pain Chart Form Graph README (+2 more)

### Community 10 - "Firecrawl Scraper"
Cohesion: 0.36
Nodes (8): build_pdf.py, main() (build_pdf.py), _make_form_xobject(), Open flat_print.pdf, build AcroForm overlay with Kids merge for shared names, overlay_form_fields(), PDF Form Generation, Python PDF Libraries, render_html_and_extract()

### Community 11 - "CCS Form Fields"
Cohesion: 0.32
Nodes (8): 5-Hour Token Window Reset, ccusage (Claude Usage Tracking Tool), Pacific Time Zone, Session Auto-Resume at 5-Hour Reset, Time Format Rule (12-Hour Pacific), Timezone Preference (Pacific Time), Global User Profile, Kade (User)

### Community 12 - "Obsidian Config"
Cohesion: 0.33
Nodes (5): BeautifulSoup, extract_metadata(), Extract page metadata, scraper.py, str

### Community 13 - "Design Systems"
Cohesion: 0.40
Nodes (4): How it works, License, Quick Start, Tech Stack

### Community 14 - "Session Management"
Cohesion: 0.67
Nodes (3): A-Nation Media Design System, Design Systems Vault README, Transform9 Design System

## Knowledge Gaps
- **95 isolated node(s):** `setup.sh script`, `Design Systems Folder`, `LibreOffice (soffice) Configuration`, `ImageMagick 7 Configuration`, `Hermes Delivery Configuration` (+90 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **8 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Firecrawl-copycat` connect `Firecrawl API & Features` to `A-NATION Brand Colors`?**
  _High betweenness centrality (0.014) - this node is a cross-community bridge._
- **Why does `A-NATION Media — Brand Design Guidelines` connect `A-NATION Brand Colors` to `Firecrawl API & Features`?**
  _High betweenness centrality (0.014) - this node is a cross-community bridge._
- **Why does `Claude Code Agent` connect `Multi-Agent System` to `CCS Form Fields`?**
  _High betweenness centrality (0.011) - this node is a cross-community bridge._
- **Are the 12 inferred relationships involving `Culver City Surgical Pain Chart Form 2026 (PI Cases, English)` (e.g. with `Pain Assessment Chart` and `Patient Information`) actually correct?**
  _`Culver City Surgical Pain Chart Form 2026 (PI Cases, English)` has 12 INFERRED edges - model-reasoned connections that need verification._
- **What connects `setup.sh script`, `Verification Economy (4-tier ladder)`, `Design Systems Folder` to the rest of the system?**
  _103 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Agent Memory Vault Structure` be split into smaller, more focused modules?**
  _Cohesion score 0.11067193675889328 - nodes in this community are weakly interconnected._
- **Should `CCS Pain Chart Form` be split into smaller, more focused modules?**
  _Cohesion score 0.13333333333333333 - nodes in this community are weakly interconnected._