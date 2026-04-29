# WebForm-Report-Analyzer

AI-powered form analyzer for SpecTec AMOS™ workflows.

## What it does

Converts forms from multiple input formats into structured output:

| Input | Mode | Output |
|---|---|---|
| PDF, PNG, JPG, BMP, GIF, WEBP | ✦ AI Vision | SurveyJS JSON **or** HTML Report |
| PDF with AcroForm fields | 📝 Text Parse | SurveyJS JSON |
| PowerBuilder DataWindow `.txt` | ⚙ PB Source | SurveyJS JSON |

## Output types

- **`{ } WebForm`** — SurveyJS JSON schema, saved to `archive/webforms/{client}/`
- **`</> Report`** — Styled HTML report, saved to `archive/reports/{client}/`

## Archive structure

```
archive/
├── webforms/
│   ├── GNMTC/
│   │   └── vessel_inspection.surveyjs.json
│   └── HYPROC/
│       └── purchase_order.surveyjs.json
└── reports/
    ├── GNMTC/
    │   └── crankshaft_deflection.html
    └── HYPROC/
        └── machinery_inspection.html
```

## Local development

```bash
git clone https://github.com/AntoninoMaione/WebForm-Report-Analyzer.git
cd WebForm-Report-Analyzer
# Edit index.html
git add -A && git commit -m "your message" && git push
# Cloudflare Pages auto-deploys on push to main
```

## Deployment

Hosted on **Cloudflare Pages** — auto-deploys from `main` branch root.

- Production URL: `https://webform-report-analyzer.pages.dev`
- Build command: *(none — static HTML)*
- Root directory: `/`

## API Key

The Anthropic API key is stored in **browser localStorage only** (`wfra_apikey`). It is never committed to this repository.

## GitHub Token for Archive

A GitHub PAT with `repo` scope is required to push output files to the archive.
The app stores it in localStorage (`wfra_ghtoken`) automatically on first save.
