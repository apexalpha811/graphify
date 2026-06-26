# Graph Report - .  (2026-06-25)

## Corpus Check
- 43 files · ~115,919 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 308 nodes · 789 edges · 16 communities (12 shown, 4 thin omitted)
- Extraction: 99% EXTRACTED · 1% INFERRED · 0% AMBIGUOUS · INFERRED: 9 edges (avg confidence: 0.79)
- Token cost: 18,000 input · 1,800 output

## Community Hubs (Navigation)
- [[_COMMUNITY_DocuPipe Frontend Pipeline|DocuPipe Frontend Pipeline]]
- [[_COMMUNITY_Cloudflare Pages Functions API|Cloudflare Pages Functions API]]
- [[_COMMUNITY_Dev Server Core|Dev Server Core]]
- [[_COMMUNITY_Architecture Concepts|Architecture Concepts]]
- [[_COMMUNITY_Dev Server Dashboard & Module API|Dev Server Dashboard & Module API]]
- [[_COMMUNITY_Dev Server DocuPipe Client|Dev Server DocuPipe Client]]
- [[_COMMUNITY_CF Pages Preview Builders|CF Pages Preview Builders]]
- [[_COMMUNITY_Dev Server Preview Builders|Dev Server Preview Builders]]
- [[_COMMUNITY_Domain Concepts & CPT Codes|Domain Concepts & CPT Codes]]
- [[_COMMUNITY_Package Configuration|Package Configuration]]
- [[_COMMUNITY_FireCrawl URL Config|FireCrawl URL Config]]
- [[_COMMUNITY_Claude Launch Config|Claude Launch Config]]
- [[_COMMUNITY_Claude Settings|Claude Settings]]
- [[_COMMUNITY_Appeals Data|Appeals Data]]
- [[_COMMUNITY_Orphan Settings|Orphan Settings]]

## God Nodes (most connected - your core abstractions)
1. `handleApi()` - 31 edges
2. `handleApi()` - 28 edges
3. `config()` - 21 edges
4. `isLive()` - 17 edges
5. `isLive()` - 14 edges
6. `hasSupabase()` - 13 edges
7. `supabaseRequest()` - 13 edges
8. `api()` - 13 edges
9. `commitPreviewToDashboard()` - 13 edges
10. `callJson()` - 12 edges

## Surprising Connections (you probably didn't know these)
- `.firecrawl/dashboard.md — scraped snapshot of CCS dashboard UI (overview KPIs, nav)` --references--> `DocuPipe module schema — configurable extraction unit linking DocuPipe schema to Stedi target and dashboard section`  [INFERRED]
  .firecrawl/dashboard.md → data/docupipe-modules.json
- `functions/[[path]].js — Cloudflare Pages catch-all API handler` --references--> `20260616000000_eligibility.sql — Supabase migration: patients, eligibility_checks, eligibility_batches, work_queue tables`  [INFERRED]
  functions/[[path]].js → supabase/migrations/20260616000000_eligibility.sql
- `launch.json — debug config for ccs-dashboard-docupipe` --references--> `server.js — Node.js local dev server (mirrors Cloudflare Pages function logic)`  [EXTRACTED]
  .claude/launch.json → server.js
- `functions/[[path]].js — Cloudflare Pages catch-all API handler` --implements--> `Supabase-or-file fallback — modules and records fall back to JSON file or seed when Supabase creds absent`  [EXTRACTED]
  functions/[[path]].js → server.js
- `package.json — project manifest with Wrangler/Cloudflare Pages scripts` --references--> `server.js — Node.js local dev server (mirrors Cloudflare Pages function logic)`  [EXTRACTED]
  package.json → server.js

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **DocuPipe intake pipeline: upload → standardize → Stedi preview → dashboard insert** — lib_docupipe, functions_path_handler, data_docupipe_modules, concept_docupipe_module, concept_stedi_target, lib_data_appeals [INFERRED 0.90]
- **ERA denial → appeal letter generation → dashboard appeal record** — lib_stedi, lib_ai_generate_appeal_letter, lib_data_appeals, concept_carc_rarc, concept_appeal_letter_agentic_flow [INFERRED 0.85]
- **Supabase persistence: patients, eligibility_checks, eligibility_batches, work_queue, docupipe_imports, docupipe_modules** — supabase_eligibility_sql, functions_path_handler, server_js, concept_supabase_fallback [EXTRACTED 1.00]
- **DocuPipe to Stedi Claim Submission Pipeline** — concept_docupipe_api, concept_docupipe_modules, index_html_dashboard_spa, concept_stedi_837p, concept_stedi_837i, concept_dashboard_records_table, concept_supabase_persistence [EXTRACTED 0.95]
- **Cloudflare Pages Production API Stack** — concept_cloudflare_pages, concept_functions_path_js, concept_supabase_persistence, concept_stedi_api, concept_docupipe_api [EXTRACTED 0.95]
- **Critical API Bug Patterns and Fixes** — concept_payer_api_response_structure, concept_supabase_auth_pattern, concept_docupipe_upload_payload, tasks_lessons_project_lessons [INFERRED 0.85]

## Communities (16 total, 4 thin omitted)

### Community 0 - "DocuPipe Frontend Pipeline"
Cohesion: 0.08
Nodes (62): appeals.js — in-memory APPEALS_DATA store, activeModuleDraft(), api(), applySchemaOverrides(), autoImportPreview(), bind(), bindImportToggle(), chooseSchema() (+54 more)

### Community 1 - "Cloudflare Pages Functions API"
Cohesion: 0.12
Nodes (59): appMode(), buildStediPreview(), callJson(), config(), createModule(), dashboardSectionForStoredTarget(), dashboardTargetForStedi(), defaultJsonSchema() (+51 more)

### Community 2 - "Dev Server Core"
Cohesion: 0.09
Nodes (20): buildStediPreview(), config, DASHBOARD_RECORDS_FILE, fs, http, mockDocuments, mockJobs, mockStandardizations (+12 more)

### Community 3 - "Architecture Concepts"
Cohesion: 0.16
Nodes (24): Cloudflare Pages Functions (Production Host), Supabase dashboard_records Table, DocuPipe API, DocuPipe Intake Modules, DocuPipe Upload Payload Shape (document.file.contents), Eligibility Section (270/271) Full Rebuild, Cloudflare Pages Functions API Router, Stedi Payer API Response Structure Bug Pattern (+16 more)

### Community 4 - "Dev Server Dashboard & Module API"
Cohesion: 0.21
Nodes (24): createModule(), dashboardSectionForStoredTarget(), dashboardTargetForStedi(), defaultJsonSchema(), deleteDashboardRecord(), deleteModule(), findModule(), handleApi() (+16 more)

### Community 5 - "Dev Server DocuPipe Client"
Cohesion: 0.19
Nodes (22): callJson(), docupipeHeaders(), getDocupipeDocument(), getDocupipeJob(), getDocupipeSchema(), getExtension(), getStandardization(), isLive() (+14 more)

### Community 6 - "CF Pages Preview Builders"
Cohesion: 0.22
Nodes (20): addDays(), buildAttachmentPreview(), buildClaimPreview(), buildEligibilityPreview(), buildEligibilityRequest(), buildEraPreview(), buildProviderPreview(), compactDate() (+12 more)

### Community 7 - "Dev Server Preview Builders"
Cohesion: 0.22
Nodes (20): addDays(), buildAttachmentPreview(), buildClaimPreview(), buildEligibilityPreview(), buildEligibilityRequest(), buildEraPreview(), buildProviderPreview(), compactDate() (+12 more)

### Community 8 - "Domain Concepts & CPT Codes"
Cohesion: 0.12
Nodes (15): Appeal letter agentic flow — Stedi MCP search/eligibility/ERA then Claude API draft then 275 submit, CARC/RARC denial codes — healthcare claim adjustment reason codes extracted from ERA and used to generate appeals, DocuPipe module schema — configurable extraction unit linking DocuPipe schema to Stedi target and dashboard section, Mock/live mode pattern — APP_MODE env var gates real API calls vs in-memory mocks throughout server and functions, Stedi EDI target types — professionalClaim837P, eligibility270, appealsFromEra, claimAttachment275, providerEnrollment, Supabase-or-file fallback — modules and records fall back to JSON file or seed when Supabase creds absent, CPT_DB, .firecrawl/dashboard.md — scraped snapshot of CCS dashboard UI (overview KPIs, nav) (+7 more)

### Community 9 - "Package Configuration"
Cohesion: 0.14
Nodes (13): description, engines, node, main, name, private, scripts, cf:deploy (+5 more)

### Community 10 - "FireCrawl URL Config"
Cohesion: 0.50
Nodes (3): data, links, success

## Knowledge Gaps
- **46 isolated node(s):** `version`, `configurations`, `allow`, `success`, `links` (+41 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **4 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `functions/[[path]].js — Cloudflare Pages catch-all API handler` connect `Domain Concepts & CPT Codes` to `DocuPipe Frontend Pipeline`?**
  _High betweenness centrality (0.137) - this node is a cross-community bridge._
- **What connects `version`, `configurations`, `allow` to the rest of the system?**
  _47 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `DocuPipe Frontend Pipeline` be split into smaller, more focused modules?**
  _Cohesion score 0.07884615384615384 - nodes in this community are weakly interconnected._
- **Should `Cloudflare Pages Functions API` be split into smaller, more focused modules?**
  _Cohesion score 0.11912568306010929 - nodes in this community are weakly interconnected._
- **Should `Dev Server Core` be split into smaller, more focused modules?**
  _Cohesion score 0.09 - nodes in this community are weakly interconnected._
- **Should `Domain Concepts & CPT Codes` be split into smaller, more focused modules?**
  _Cohesion score 0.12418300653594772 - nodes in this community are weakly interconnected._
- **Should `Package Configuration` be split into smaller, more focused modules?**
  _Cohesion score 0.14285714285714285 - nodes in this community are weakly interconnected._