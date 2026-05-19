# ODC Plan Review Report Generator

**One Dream Community** — AI-powered NDIS Plan Review Report tool for Support Coordinators.

---

## What This Tool Does

Support Coordinators upload therapy, medical, and clinical reports for a participant. The AI (Claude) reads every document, applies its knowledge of NDIS standards and pricing, and generates a comprehensive draft Plan Review Report covering:

- Executive Summary
- Plan Performance rating
- Progress against current NDIS Goals
- Allied Health & Therapy recommendations (with NDIS categories + estimated costs)
- Gaps & Unmet Needs (prioritised: Critical / High / Medium / Low)
- Recommendations for Next Plan
- Support Categories table (current vs requested allocation + rationale)
- Health, Housing, Daily Living, Community, Capacity Building narrative sections
- Participant Voice & SC Observations
- Compliance & Safeguarding flags

All report sections are **editable** in-browser, and the final report can be **printed to PDF** or **copied as plain text**.

---

## Quick Start

### Option 1 — Open directly in browser (simplest)
```
Double-click index.html
```
Works immediately. No setup required.

### Option 2 — Serve locally
```bash
npx serve .
# or
python3 -m http.server 8080
```
Then open `http://localhost:8080`

### Option 3 — GitHub Pages
1. Push this repo to GitHub
2. Go to Settings → Pages → Source → `main` branch, `/ (root)`
3. Your tool is live at `https://yourusername.github.io/repo-name`

---

## Setup: API Key

This tool calls the Anthropic Claude API. You need an API key:

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Create an API key under **API Keys**
3. Paste it into the **API Key** field in the top navigation bar of the tool

> **Privacy:** The key is stored in `sessionStorage` only — it is never saved to disk, never sent anywhere except the Anthropic API, and is cleared when the browser tab is closed.

### Estimated cost per report
| Document volume | Estimated cost |
|---|---|
| 1–3 documents | ~$0.05 – $0.10 |
| 4–8 documents | ~$0.10 – $0.20 |
| 8+ large PDFs | ~$0.20 – $0.40 |

---

## How to Use

### Step 1 — Participant Information
Fill in participant name, NDIS number, DOB, diagnosis, plan dates, your name as SC, plan management type, current NDIS goals (one per line), and any additional notes.

### Step 2 — Upload Reports
Drag and drop or click to upload clinical documents. Supported file types:
- **PDF** (preferred) — therapy reports, assessments, medical summaries
- **Images** — JPG, PNG (scanned documents, referral letters)

The tool auto-detects document categories from filenames. You can also manually select from the dropdown:
- Occupational Therapy Report
- Speech Pathology Report
- Physiotherapy Report
- Psychology / Behaviour Support Report
- Medical Summary
- Dietitian Report
- Functional Capacity Assessment
- Previous NDIS Plan
- Plan Management Statement
- Allied Health Other
- Other

### Step 3 — Generate
Review the summary and click **Generate Report**. The AI will read all documents and produce the report (typically 20–60 seconds depending on document size).

### Step 4 — Review & Export
Review the generated report. Click **✏️ Edit** on any section to modify text. When ready:
- **🖨️ Print / Save PDF** — browser print dialog (select "Save as PDF")
- **📋 Copy as Text** — plain text for pasting into Word or another system

---

## NDIS Knowledge Built In

The system prompt embeds:

- **NDIS Act 2013** and associated Rules
- **NDIS Practice Standards** — including Support Coordination Standard 2.6
- **NDIS Pricing Arrangements & Price Limits 2024–25** — all 16 support categories and registration groups
- **NDIS Quality and Safeguards Commission** requirements
- Gap identification framework (missing assessments, AT, housing, carer sustainability, safeguarding)
- Professional third-person language and NDIS terminology standards

---

## Privacy & Data

- Files are sent directly from your browser to the Anthropic API using your own API key
- Files are **not** stored on any ODC server
- Anthropic's data handling is governed by their [Privacy Policy](https://www.anthropic.com/privacy)
- The API key is stored in `sessionStorage` only (cleared on tab close)
- Do not share your API key

---

## Customisation

To update NDIS pricing or add sections, edit the `NDIS_SYSTEM_PROMPT` constant inside `index.html`. The JSON structure returned by the AI is defined there — adding a field to the prompt and to the `Report` component will surface it in the UI.

---

## Support

Built for One Dream Community by ODC Operations.  
For issues or feature requests, contact your ODC system administrator.
