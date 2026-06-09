# Setup Guide

## Prerequisites

- n8n (self-hosted or [cloud](https://n8n.io/cloud))
- Google account
- Gemini API key (free)

---

## Step 1: Google Sheets

Create 3 sheets:

| Sheet | Columns |
|-------|---------|
| **SWE Applications** | name, email, role, resumeUrl, processed |
| **BDM Applications** | name, email, role, resumeUrl, processed |
| **Master Hiring** | name, email, role, resumeUrl, sourceSheet, sourceRow, applied_at, status, score, classification, summary, strengths, concerns, recommendation, email_status |

Share all sheets with your Google service account email.

---

## Step 2: Google Forms

Create 2 forms:

| Form | Fields |
|------|--------|
| **SWE Application** | Name, Email, Resume upload (file) |
| **BDM Application** | Name, Email, Resume upload (file) |

Link each form to its respective sheet:
- Form → Responses → Link to Sheets → Create new sheet

---

## Step 3: Google Cloud Project

1. [console.cloud.google.com](https://console.cloud.google.com) → New Project
2. Enable APIs: Google Sheets API, Google Drive API
3. Credentials → Create OAuth 2.0 Client ID → Desktop app
4. Download JSON → rename to `client_secret.json`

---

## Step 4: n8n Credentials

### Google Sheets OAuth2
- n8n → Settings → Credentials → Add → Google Sheets OAuth2 API
- Paste client ID and secret from `client_secret.json`
- Sign in with Google → authorize

### Gmail SMTP
- Gmail → Security → 2-Step Verification → On
- App passwords → Generate → Mail → Device: n8n
- Copy 16-character password
- n8n → Credentials → SMTP
- Host: `smtp.gmail.com`, Port: `587`, User: your Gmail, Pass: app password

### Gemini API
- [Google AI Studio](https://aistudio.google.com/app/apikey) → Create API key
- Store in workflow or environment variable

---

## Step 5: Import Workflows

1. n8n → Workflows → Import from File
2. Select `workflows/hiring-ai-screening.json`
3. Select `workflows/hiring-email-dispatcher.json`
4. Map credentials in each node (click red dots)

---

## Step 6: Environment Variables

Copy `.env.example` to `.env` and fill:

```bash
GEMINI_API_KEY=your_key
MASTER_SHEET_ID=your_master_sheet_id
MANAGER_EMAIL=sulemanaizaz48@gmail.com
SMTP_USER=your_gmail@gmail.com
SMTP_PASS=your_16_char_app_password
