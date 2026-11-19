# n8n automation demos

Three small, importable n8n workflows. Each one is a plain JSON export you can import into any n8n instance (Settings > Import from File) and wire to your own credentials.

Built by Copper Tone Technologies (Baton Rouge, LA). These are reference workflows, not claims about client results.

## Workflows

| File | What it does | Credentials you supply |
|---|---|---|
| `workflows/lead-intake-llm-sheet.json` | Webhook receives a lead, normalizes the fields, OpenAI classifies it (category, urgency, one-line summary), appends a row to a Google Sheet, responds 200. | OpenAI API key, Google Sheets OAuth, a sheet ID |
| `workflows/webhook-openai-email-draft.json` | Webhook receives a customer message, OpenAI drafts a plain reply, saves it as a Gmail draft for human review. Nothing is sent automatically. | OpenAI API key, Gmail OAuth |
| `workflows/scheduled-postgres-report.json` | Cron every Monday 08:00, runs a weekly totals query on Postgres, formats it in a Code node, emails the report over SMTP. | Postgres connection, SMTP account |

## How to use one

1. Import the JSON into n8n.
2. Open each node with empty credentials and attach your own accounts.
3. Replace placeholders (`YOUR_SHEET_ID`, `owner@example.com`, table names) with your values.
4. Run once manually with test data before activating.

## Notes

- No workflow sends anything to a third party without a node you can see and remove.
- The email workflow creates drafts only; a human reviews before anything goes out.
- Queries and prompts are meant to be edited. They are starting points, not finished products.
