# WebForm-Report-Analyzer — Development Roadmap

> *Migrated and updated from WebFormAnalyzer*

## Phase 1 — Research & Evaluation ✅ *completed*

- [x] Evaluate SurveyJS as replacement for jQuery FormBuilder
- [x] Define project structure and architecture
- [x] Document SurveyJS components, licensing, integration path
- [x] Evaluate PDF parsing libraries (pdf.js selected — client-side)
- [x] Identify reference PDF form templates (AMOS inspection forms)

---

## Phase 2 — Demo App ✅ *completed — live at webform-report-analyzer.pages.dev*

### 2.1 — Input modes
- [x] PDF upload with drag-and-drop
- [x] pdf.js integration for client-side PDF parsing
- [x] AcroForm field extraction (Text Parse mode)
- [x] AI Vision mode — PDF/image → Claude API → JSON
- [x] PowerBuilder DataWindow source parser (PB Source mode)
- [x] Image support: PNG, JPG, BMP, GIF, WEBP

### 2.2 — Output types
- [x] SurveyJS JSON schema (WebForm mode)
- [x] Styled HTML report (Report mode)
- [x] Output type toggle in UI
- [x] Download to local disk

### 2.3 — Preview & Archive
- [x] SurveyJS live preview (WebForm mode)
- [x] HTML iframe preview (Report mode)
- [x] GitHub archive push (PAT token, per-client folders)
- [x] API key persistence in localStorage
- [x] Client name autocomplete (localStorage history)

### 2.4 — Infrastructure
- [x] GitHub repo: AntoninoMaione/WebForm-Report-Analyzer
- [x] Cloudflare Pages auto-deploy from main branch
- [x] Local clone at C:\WebForm-Report-Analyzer\

---

## Phase 3 — AMOS Integration Design *(planned Q3 2026)*

- [ ] Map SurveyJS JSON schema storage to AMOS DB schema
- [ ] Design REST API endpoints for schema CRUD
- [ ] Design form response storage (flat table for BI)
- [ ] Define user roles: form designer vs. form user
- [ ] Pilot with 2–3 real AMOS form templates (GNMTC, HYPROC)
- [ ] Performance and security review

---

## Phase 4 — Production *(planned Q4 2026 – Q1 2027)*

- [ ] Deploy SurveyJS Form Library in AMOS frontend
- [ ] Deploy Survey Creator for admin users
- [ ] Migrate existing jQuery FormBuilder forms to SurveyJS JSON
- [ ] Connect response tables to BI dashboards
- [ ] User training and documentation

---

## Timeline

| Phase | Status | Target |
|---|---|---|
| Phase 1 — Research | ✅ Done | Q1 2026 |
| Phase 2 — Demo App | ✅ Done | Q2 2026 |
| Phase 3 — Integration Design | 🔵 Planned | Q3 2026 |
| Phase 4 — Production | 🔵 Planned | Q4 2026 – Q1 2027 |
