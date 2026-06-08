# AI-Powered Hiring Automation

Fully automated hiring pipeline built with n8n. Screens Software Engineer & Business Development Manager candidates using Google Gemini AI, detects resume fraud, and dispatches personalized emails.

#  Demo
[Link to your Loom video]

#  Architecture
https://drive.google.com/file/d/1dNIKN2Y6by8WDI7MNz6x7F9IJ-_HM0zg/view?usp=sharing
https://drive.google.com/file/d/1m7QBFGNPLWJL20mOzXhkmh3duaLfmTWN/view?usp=sharing
https://drive.google.com/file/d/1MZ1jT0QUZR0V1RU2qUFPPJgd2C9oG-Dk/view?usp=sharing
https://drive.google.com/file/d/1y_ZndXUdkGu9j9-ty1zMS8vWV-GcZ8_F/view?usp=sharing


# Workflows

| Workflow | Purpose | Trigger |
|----------|---------|---------|
| `hiring-ai-screening.json` | Download resumes, validate files, AI screening, fraud detection | Schedule (every 15 min) |
| `hiring-email-dispatcher.json` | Send interview/rejection emails, manager alerts | Schedule (every 15 min) |

#  Setup

# Prerequisites
- n8n (self-hosted or cloud)
- Google Gemini API key (free tier)
- Google Sheets (3 sheets: SWE, BDM, Master)
- Gmail account (for SMTP)

# Installation
1. Import both JSON files into n8n
2. Configure credentials:
   - Google Sheets OAuth2
   - Gmail SMTP
   - Gemini API key
3. Update environment variables (see `.env.example`)
4. Activate both workflows

### Environment Variables
GEMINI_API_KEY=your_key_here
MASTER_SHEET_ID=your_google_sheet_id
MANAGER_EMAIL=abc@gmail.com
