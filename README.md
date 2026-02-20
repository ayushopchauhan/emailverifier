# Free Email Verifier for n8n

A self-hosted email verification system that runs inside n8n without API keys or monthly subscriptions.

## What it does
It runs 12 checks on every email address to determine if it is safe to send to:
*   **Syntax & Typo Detection:** Catches `gmial.com` and suggests `gmail.com`.
*   **Disposable Email Check:** Detects throwaway addresses (local DB + API).
*   **DNS Analysis:** Checks MX, SPF, and DMARC records.
*   **SMTP Handshake:** Connects to the mail server to verify the mailbox exists (without sending email).
*   **Microsoft API:** Verifies Outlook/Live/Hotmail accounts via Azure AD.
*   **Gravatar:** Checks for profile pictures as a trust signal.

## How to use the Free Version
1.  Download `email_verifier_free.json` from this repository.
2.  Import it into your n8n instance.
3.  Create a Google Sheet with two tabs: `Input` and `Results`.
4.  Add emails to the `Input` tab (Column A).
5.  Connect your Google Sheets credentials in n8n.
6.  Run the workflow.

**Requirements:** Self-hosted n8n on a VPS with Port 25 outbound open (Hetzner, Contabo, DigitalOcean, etc.). AWS/GCP/Azure usually block this port.

---

## ⚡ Upgrade to Pro

I also built a Pro version for users who need to verify larger lists automatically.

**[Get the Pro Version on Gumroad ($19)](https://ayushopchauhan.gumroad.com/l/emailverifierpro)**

### Free vs. Pro

| Feature | Free Version | Pro Version |
| :--- | :--- | :--- |
| **Interface** | Google Sheets | Telegram Bot |
| **Capacity** | 200 emails / run | 2,000+ emails / run |
| **Rate Limiting** | Fixed (15s delay) | **Smart Adaptive** (3s/12s/20s) |
| **SMTP Method** | Single Check | **Batch Verification** |
| **Retries** | No | **Auto-Retry Loop** (catches false negatives) |
| **Reports** | Manual | **Auto-generated CSVs** |
| **Setup** | Manual | Automated |

The Pro version includes the full workflow JSON, a Telegram bot interface, and a detailed setup guide.

**[View Pro Version Details](https://ayushopchauhan.gumroad.com/l/emailverifierpro)**
