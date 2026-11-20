# AI Lead Qualification, Summarization & Google Sheets Automation with n8n

An automated lead-intake and qualification workflow built with **n8n** that captures incoming customer inquiries via a `POST` webhook, analyzes them with AI (`HOT` vs. `LOW`) and generates a concise summary, formats the payload with JavaScript, and logs structured records into **Google Sheets**.

## Key Features

- **Automated Webhook Ingestion:** Captures incoming lead data (`name`, `contact`, `message`) in real time.
- **AI Intent Classification & Summary:** Analyzes inquiry context to classify leads (`HOT` or `LOW`) and produces a clear 1-sentence summary.
- **Structured Data Transformation:** Uses a JavaScript node to clean, validate, and structure fields along with a timestamp.
- **Google Sheets Logging:** Automatically appends structured rows (`name`, `contact`, `message`, `lead_status`, `ai_summary`, `timestamp`) for easy tracking.
- **Scalable Architecture:** Ready to extend with instant alerts, automated follow-ups, or CRM integrations.

## Workflow Architecture

1. **Webhook (`POST`)**: Receives incoming lead payload (`name`, `contact`, `message`).
2. **Basic LLM Chain + Google Gemini Chat Model**: Evaluates lead intent (`HOT` or `LOW`) and generates a concise summary (`ai_summary`).
3. **Code in JavaScript**: Cleans, validates, and structures output fields along with a `timestamp`.
4. **Google Sheets (`Append row in sheet`)**: Appends the processed lead record into the target spreadsheet.

## Output Schema (Google Sheets Columns)

- `name`
- `contact`
- `message`
- `lead_status` (`HOT` | `LOW`)
- `ai_summary`
- `timestamp`

## Setup & Usage

1. Import the workflow JSON (`My workflow 2.json`) into your **n8n** instance.
2. Configure your **Google Gemini** credential and **Google Sheets** credential.
3. Select your target Google Sheet document and worksheet, then verify column mapping.
4. Publish/activate the workflow and send a `POST` request to the Webhook URL with sample lead data.
5.
