# Free workflow: Lead capture form

This is workflow **01** from the paid **n8n Business Automation Pack**. It captures a quote request, stores the lead in Google Sheets, sends the lead a confirmation email and pings your team on Telegram.

```
Form Trigger → Normalize Lead → Google Sheets (append) → Gmail (confirmation) → Telegram (alert)
```

## What you need

- n8n 1.80+ (built and tested on 2.35.3)
- A Google Sheets spreadsheet
- Gmail OAuth2 credential
- Telegram bot token and a chat ID
- About 10 minutes

## 1. Create the sheet

Create a tab named **Leads** with these exact headers in row 1:

| name | email | phone | service | message | source | created_at |
| --- | --- | --- | --- | --- | --- | --- |

Column names are case-sensitive. `created_at` is filled by the workflow.

## 2. Replace the placeholders

The JSON contains three placeholders. Replace all of them before importing:

| Placeholder | Replace with |
| --- | --- |
| `YOUR_SHEET_ID` | The long ID from your Google Sheets URL: `/spreadsheets/d/<ID>/edit` |
| `YOUR_EMAIL@example.com` | The address that should receive the internal lead alert |
| `YOUR_TELEGRAM_CHAT_ID` | Your Telegram chat ID (see below) |

You can edit the JSON in a text editor, or use the paid pack's `scripts/configure.mjs`. For a single file, a text editor is enough.

## 3. Import into n8n

1. Open n8n → **Workflows** → **Import from File**.
2. Select `01-lead-capture-form.json`.
3. Open each red-badged node and connect the credential:
   - **Save Lead** → Google Sheets OAuth2
   - **Send Confirmation** → Gmail OAuth2
   - **Notify Team** → Telegram
4. In **Save Lead**, confirm the Document ID and Sheet Name (`Leads`).
5. In **Notify Team**, confirm the chat ID.

## 4. Test with the form

1. Click **Test workflow**.
2. Open the Form Trigger URL shown in the node.
3. Submit a test entry.
4. Check the execution: the row appears in **Leads**, the confirmation email is sent, and the Telegram message arrives.

If the form gives `Expected multipart/form-data`, you are posting with `curl -d`; use a browser or `curl -F` instead.

## Telegram chat ID

1. Create a bot with **@BotFather** and copy the token.
2. Send `/start` to your bot.
3. Open `https://api.telegram.org/bot<TOKEN>/getUpdates`.
4. Use `result[0].message.chat.id` as the chat ID. Group IDs are negative.

## What this free workflow does not include

The paid pack adds 11 more workflows, the 9-tab spreadsheet template, 8 sample CSV files, the setup script, and seven guides (setup, credentials, sheet schema, workflow reference, testing, customization, troubleshooting):

**https://smallbizautomation.gumroad.com/l/n8n-business-pack**

Support: justpilugames@gmail.com
