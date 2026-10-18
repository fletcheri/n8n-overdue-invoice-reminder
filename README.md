# Overdue Invoice Reminder (Lite): free n8n workflow for Australian businesses

One polite overdue-invoice email, sent automatically a week after the due date, unless you've marked it paid.

- Webhook in (`/webhook/invoice-lite/invoice`) with invoice number, name, email, amount and due date (`YYYY-MM-DD` or `DD/MM/YYYY`)
- One email `reminderDaysOverdue` (default 7) days after the due date, weekdays inside your hours, with A$ amount and your payment details
- Mark paid via `/webhook/invoice-lite/paid` (or send `status: "paid"`) and nothing is sent
- One-click unsubscribe link and your business name in every email (Spam Act 2003)
- Works with any SMTP mailbox; daily cap and optional webhook secret

## Setup (about 15 minutes)
1. n8n → **Import from file** → `workflow/overdue-invoice-reminder-lite.n8n.json`.
2. Open **Decide** and set `businessName`, `payment`, `publicBaseUrl` (`https://<your-n8n>/webhook/invoice-lite`) and `email.from`.
3. On **Send email (SMTP)**, add an SMTP credential (Gmail app password, Microsoft 365, or your host).
4. Activate. POST `{"invoiceNumber":"INV-1","name":"Jo","email":"jo@example.com","amountDue":220,"dueDate":"01/11/2026"}` to `https://<your-n8n>/webhook/invoice-lite/invoice`, and `{"invoiceNumber":"INV-1"}` to `/webhook/invoice-lite/paid` when it's paid.

## Want more?
The **Pro pack** adds:
- **Xero sync**: unpaid invoices and contacts pulled automatically; reminders stop when paid in Xero
- 4 escalating stages (courtesy, due, firm, final) by email **and SMS**, with a pay-online button
- "Reply PAID" handling with owner alert, STOP handling, and DISPUTE holds
- contact limits in line with the ACCC/ASIC debt collection guideline (3/week, 10/month), Saturday hours and public holidays
- owner escalation at 21 days, a status page with overdue totals
- Twilio or ClickSend, dry-run mode
- debt-collection compliance notes, setup docs and test scripts

**Want the full Australian version?** The Overdue Invoice Reminder Pack (Pro) adds Xero sync, SMS, four stages, PAID replies and guideline-based contact limits. Store link coming soon; questions to aussieflows@mail.grokbot.com.

[Notify me when Pro is out](mailto:aussieflows@mail.grokbot.com?subject=Notify%20me%20-%20Overdue%20Invoice%20Reminder%20Pack).

## More free AU workflows
Other free n8n workflows for Australian small businesses (MIT, same setup style):
- [Missed-Call Text-Back](https://github.com/fletcheri/n8n-missed-call-textback): text back missed callers in seconds
- [Google Review Request](https://github.com/fletcheri/n8n-google-review-request): one honest Google review ask after each job
- [Quote Follow-Up](https://github.com/fletcheri/n8n-quote-follow-up): a polite follow-up SMS after you send a quote
- [Booking Reminder](https://github.com/fletcheri/n8n-booking-reminder): a reminder SMS before each booking

MIT licence. Not legal or financial advice.
