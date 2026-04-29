# WebForm-Report-Analyzer — Architecture Overview

> *Migrated from WebFormAnalyzer · Updated to reflect Phase 2 implementation*

## Problem Statement

AMOS™ includes many form templates originally designed as PDF files. When these templates need to be digitized for in-app data collection, they are currently re-built manually inside jQuery FormBuilder — a slow, error-prone process.

**WebForm-Report-Analyzer** automates this conversion pipeline:

```
PDF / Image / PB DataWindow source
         ↓
AI Vision · Text Parse · PB Source parser
         ↓
SurveyJS JSON Schema (WebForm)  OR  HTML Report
         ↓
Live Preview · Download · Archive on GitHub
```

---

## Input Modes

| Mode | Input | API Key | Engine |
|---|---|---|---|
| ✦ AI Vision | PDF, PNG, JPG, BMP, GIF, WEBP | Required | Claude API (vision) |
| 📝 Text Parse | PDF with AcroForm fields | Not required | pdf.js annotations |
| ⚙ PB Source | PowerBuilder DataWindow `.txt` | Not required | Client-side regex parser |

## Output Types

| Type | Format | Archive path |
|---|---|---|
| `{ } WebForm` | SurveyJS JSON | `archive/webforms/{client}/` |
| `</> Report` | Styled HTML | `archive/reports/{client}/` |

---

## High-Level Data Flow

```
1. User selects input mode and drops file
         ↓
2. File is parsed / rendered
   - AI Vision: PDF rendered to JPEG via pdf.js → sent to Claude API
   - Text Parse: AcroForm widgets extracted via pdf.js annotations
   - PB Source: DataWindow table/column/compute parsed by regex
         ↓
3. Output generated (JSON schema or HTML report)
         ↓
4a. Live preview rendered (SurveyJS or iframe)
4b. Download to local disk
4c. Optional: push to GitHub archive via API
```

---

## SurveyJS Question Type Mapping

| Source field | SurveyJS type |
|---|---|
| Text input (single line) | `text` |
| Text area / long char | `comment` |
| Checkbox / boolean | `boolean` |
| Radio group | `radiogroup` |
| Dropdown with choices | `dropdown` |
| Date field | `text` (inputType: date) |
| Matrix / table | `matrixdropdown` |
| Section header | `panel` |

---

## Technology Stack

| Layer | Technology |
|---|---|
| PDF rendering | pdf.js 3.11 (client-side) |
| AI analysis | Anthropic Claude API (claude-haiku / sonnet / opus) |
| PB parsing | Vanilla JS regex (client-side, no dependencies) |
| Form preview | SurveyJS Form Library 1.9 (jQuery) |
| Hosting | Cloudflare Pages (auto-deploy from GitHub `main`) |
| Archive storage | GitHub Contents API (PAT token, repo scope) |

---

## Repository Structure

```
WebForm-Report-Analyzer/
├── index.html              ← single-file app (~50KB)
├── README.md
├── .gitignore
├── docs/
│   ├── architecture.md     ← this file
│   ├── roadmap.md
│   └── surveyjs-research.md
├── samples/
│   └── input/              ← sample PDF/image forms for demo
└── archive/
    ├── webforms/           ← SurveyJS JSON outputs by client
    └── reports/            ← HTML report outputs by client
```
