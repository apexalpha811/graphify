# Culver City Surgical Dashboard (DocuPipe)

Source: `raw/GRAPH_REPORT_culver-city-surgical-2026-06-26.md`
Last graphify run: 2026-06-26 | 399 nodes · 861 edges · 30 communities

## What This Project Is

A single-page Cloudflare Pages app (`index.html` + `functions/[[path]].js`) for ambulatory surgery center (ASC) billing and revenue cycle management. Features: claim creation (837P/837I), eligibility verification (270/271), ERA/835 remittance inbox, DocuPipe document intake, provider/payer/location management, appeals, attachments, COB, enrollments.

Local dev uses `server.js` (Node.js) which mirrors the CF Pages function logic identically — same `handleApi()`, same preview builders, same mock/live mode gate.

## God Nodes (Core Abstractions)

- `handleApi()` — 31 edges (CF functions) + 28 edges (server) — central router for all API traffic
- `config()` — 21 edges — environment/mode config read by everything
- `isLive()` — 17 + 14 edges — gates all real Stedi/Supabase calls
- `hasSupabase()` — 13 edges
- `supabaseRequest()` — 13 edges
- `api()` — 13 edges (DocuPipe frontend)
- `commitPreviewToDashboard()` — 13 edges
- `callJson()` — 12 edges

## Community Map (30 communities)

| Community | Nodes | Role |
|-----------|-------|------|
| Dev Server API | 91 | server.js — full local API mirror |
| Cloudflare Pages API | 81 | functions/[[path]].js — production handler |
| DocuPipe & Lib Layer | 65 | lib/docupipe.js, lib/data — frontend intake logic |
| EDI Transaction Types | 34 | 837P/I, 270/271, 835, DEMO mode concepts |
| API & Integration Lessons | 24 | tasks/lessons.md — integration gotchas |
| Claim Lifecycle Concepts | 18 | Appeal flow, CARC/RARC, Stedi targets, mock/live |
| Infrastructure & Persistence | 15 | CF Pages, Supabase, DocuPipe API, Stedi host |
| Package Config | 14 | package.json / Wrangler scripts |
| Endpoint Audit Trail | 6 | Stedi endpoint completeness rules |
| Location & NPI Module | 4 | NPI proxy, global click handler fix, location CRUD |

Key observation: CF Pages Functions and Dev Server are near-mirror communities (81 vs 91 nodes) — same functions duplicated across both runtimes.

## Key Architectural Patterns

**Mock/live mode gate:** `APP_MODE=live` env var + Stedi API key gate all real API calls. Dev runs in mock mode with `mockDocuments`, `mockJobs`, `mockStandardizations`. Production on CF Pages auto-detects live mode.

**Supabase-or-file fallback:** Dashboard records and DocuPipe modules fall back to JSON file (`DASHBOARD_RECORDS_FILE`) or seed data when Supabase credentials are absent. This is the `hasSupabase()` guard pattern.

**DocuPipe intake pipeline:** upload → standardize → Stedi preview → `commitPreviewToDashboard()` — the full 4-step flow is a hyperedge in the graph.

**ERA-to-appeal flow:** Stedi 835 → CARC/RARC extraction → `generateAppealLetter.js` → appeal record — documented as planned agentic flow (Claude API + Stedi MCP).

**All selects default blank:** As of 2026-06-26, the select renderer in both create and edit modals prepends a blank option to every dropdown field — operators must make an explicit choice.

## Surprising Connections

- `.firecrawl/dashboard.md` (scraped UI snapshot) inferred to reference DocuPipe module schema — the UI nav reflects module config
- `functions/[[path]].js` inferred to reference the Supabase eligibility migration — CF functions are the runtime that exercises those tables
- `launch.json` explicitly references `server.js` — the debug config is wired to the dev server
- Playwright UI snapshots link back to `index.html` — the snapshot files capture actual UI state during dev sessions

## Hyperedges (Group Relationships)

1. **DocuPipe intake pipeline** — lib_docupipe, functions_path_handler, data_docupipe_modules, concept_docupipe_module, concept_stedi_target, lib_data_appeals
2. **ERA denial → appeal** — lib_stedi, lib_ai_generate_appeal_letter, lib_data_appeals, concept_carc_rarc, concept_appeal_letter_agentic_flow
3. **Supabase persistence** — eligibility migration SQL, functions handler, server.js, supabase_fallback concept
4. **DocuPipe → Stedi claim submission** — docupipe_api, docupipe_modules, index_html_dashboard_spa, stedi_837p, stedi_837i, dashboard_records_table
5. **CF Pages production stack** — cloudflare_pages, functions_path_js, supabase_persistence, stedi_api, docupipe_api
6. **DocuPipe 404 retry pattern** — standardization_404_retry, job_poll_404_retry, retry_branch_hygiene
7. **Stedi endpoint completeness** — endpoint_label_outcomes, stedi_lifecycle_artifacts, cross_module_endpoint

## Known Issues / Knowledge Gaps

- 12 thin communities (singleton/pair nodes) — isolated config fragments
- Dev Server and CF Pages communities are near-duplicate — candidate for shared module extraction
- DocuPipe & Lib Layer cohesion 0.08 — large community, could split if lib/ grows further

## Tech Stack

- Frontend: vanilla JS SPA in `index.html` (no framework)
- Backend: Cloudflare Pages Functions (`functions/[[path]].js`) + Node.js dev server (`server.js`)
- Persistence: Supabase (Postgres) via `supabaseRequest()`, JSON file fallback
- External APIs: Stedi (837 claims, 270/271 eligibility, 835 ERA, 275 attachments, 277 status), DocuPipe (document intake), NPPES NPI registry
- Deploy: Cloudflare Pages (`wrangler pages deploy`)
