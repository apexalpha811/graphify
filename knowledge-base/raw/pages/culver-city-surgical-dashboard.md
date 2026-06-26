# Culver City Surgical Dashboard (DocuPipe)

Source: `raw/GRAPH_REPORT_culver-city-surgical-2026-06-25.md`
Last graphify run: 2026-06-25 | 308 nodes · 789 edges · 16 communities

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

## Community Map

| Community | Nodes | Role |
|-----------|-------|------|
| DocuPipe Frontend Pipeline | 65 | lib/docupipe.js + lib/data/appeals.js — all frontend intake logic |
| Cloudflare Pages Functions API | 61 | functions/[[path]].js — production API handler |
| Dev Server Core | 25 | server.js config, file system, mock data |
| Architecture Concepts | 24 | Conceptual nodes: Supabase schema, DocuPipe API, CF Pages host |
| Dev Server Dashboard & Module API | 24 | Dashboard record + DocuPipe module CRUD in server.js |
| Dev Server DocuPipe Client | 22 | DocuPipe HTTP client proxy in server.js |
| CF Pages Preview Builders | 20 | buildClaimPreview, buildEligibilityPreview, etc. in functions |
| Dev Server Preview Builders | 20 | Same builders mirrored in server.js |
| Domain Concepts & CPT Codes | 18 | CPT_DB, CARC/RARC, Stedi EDI targets, mock/live mode pattern |
| Package Configuration | 14 | package.json / Wrangler scripts |

Key observation: CF Pages Functions (community 1) and Dev Server (communities 2/4/5) are near-mirror images — same functions duplicated across both runtimes.

## Key Architectural Patterns

**Mock/live mode gate:** `APP_MODE=live` env var + Stedi API key gate all real API calls. Dev runs in mock mode with `mockDocuments`, `mockJobs`, `mockStandardizations`. Production on CF Pages auto-detects live mode.

**Supabase-or-file fallback:** Dashboard records and DocuPipe modules fall back to JSON file (`DASHBOARD_RECORDS_FILE`) or seed data when Supabase credentials are absent. This is the `hasSupabase()` guard pattern.

**DocuPipe intake pipeline:** upload → standardize → Stedi preview → `commitPreviewToDashboard()` — the full 4-step flow is a hyperedge in the graph.

**ERA-to-appeal flow:** Stedi 835 → CARC/RARC extraction → `generateAppealLetter.js` → appeal record — documented as planned agentic flow (Claude API + Stedi MCP).

## Surprising Connections

- `.firecrawl/dashboard.md` (scraped UI snapshot) inferred to reference DocuPipe module schema — the UI nav reflects module config
- `functions/[[path]].js` inferred to reference the Supabase eligibility migration — CF functions are the runtime that exercises those tables
- `launch.json` explicitly references `server.js` — the debug config is wired to the dev server

## Hyperedges (Group Relationships)

1. **DocuPipe intake pipeline** — lib_docupipe, functions_path_handler, data_docupipe_modules, concept_docupipe_module, concept_stedi_target, lib_data_appeals
2. **ERA denial → appeal** — lib_stedi, lib_ai_generate_appeal_letter, lib_data_appeals, concept_carc_rarc, concept_appeal_letter_agentic_flow
3. **Supabase persistence** — eligibility migration SQL, functions handler, server.js, supabase_fallback concept
4. **DocuPipe → Stedi claim submission** — docupipe_api, docupipe_modules, index_html_dashboard_spa, stedi_837p, stedi_837i, dashboard_records_table
5. **CF Pages production stack** — cloudflare_pages, functions_path_js, supabase_persistence, stedi_api, docupipe_api
6. **Critical API bug patterns** — payer_api_response_structure, supabase_auth_pattern, docupipe_upload_payload, tasks/lessons.md

## Known Issues / Knowledge Gaps

- 46 isolated nodes (config fragments, settings stubs) — low connectivity, not architectural
- DocuPipe Frontend Pipeline (community 0) cohesion score 0.08 — very large community, candidate for splitting if refactoring
- CF Functions and Dev Server communities are near-duplicate — suggests code could be unified into a shared module

## Tech Stack

- Frontend: vanilla JS SPA in `index.html` (no framework)
- Backend: Cloudflare Pages Functions (`functions/[[path]].js`) + Node.js dev server (`server.js`)
- Persistence: Supabase (Postgres) via `supabaseRequest()`, JSON file fallback
- External APIs: Stedi (837 claims, 270/271 eligibility, 835 ERA, 275 attachments, 277 status), DocuPipe (document intake), NPPES NPI registry
- Deploy: Cloudflare Pages (`wrangler pages deploy`)
