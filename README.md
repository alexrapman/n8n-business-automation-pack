# n8n Business Automation Pack

Landing page and free sample for the **n8n Business Automation Pack** — 12 ready-to-import workflows for leads, invoices, appointments, reviews, orders, reports, support triage, content scheduling, backups and error alerts.

- Product page: https://smallbizautomation.gumroad.com/l/n8n-business-pack
- Price: €49 launch (regular €79)
- Stack: n8n + Google Sheets + Gmail + Telegram
- Tested on: n8n 2.35.3

## What is in this repository

| Path | Purpose |
| --- | --- |
| `index.html` | Self-contained landing page (GitHub Pages root) |
| `assets/` | Cover and real n8n canvas screenshot |
| `free/01-lead-capture-form.json` | Free sample workflow, importable in n8n |
| `free/README.md` | Setup notes for the free workflow |

## Free workflow

`free/01-lead-capture-form.json` is the lead capture flow from the paid pack:

Form Trigger → Normalize Lead → Google Sheets (append) → Gmail confirmation → Telegram notification.

To run it you need a Google Sheets spreadsheet with a `Leads` tab and the columns listed in `free/README.md`, plus Gmail and Telegram credentials. Replace `YOUR_SHEET_ID`, `YOUR_EMAIL@example.com` and `YOUR_TELEGRAM_CHAT_ID` before importing.

## Local preview

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## License

The landing page text and images are © SmallBiz Automation. The free workflow JSON is provided for evaluation under the same single-business terms as the paid pack: use it in your own business or client projects; do not resell or redistribute it as a template pack.

Independent product. Not affiliated with n8n GmbH, Google or Telegram.
