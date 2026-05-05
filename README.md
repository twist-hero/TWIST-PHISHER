# TWISTPHISHER - ADVANCED CYBERSECURITY AWARENESS & PHISHING SIMULATION FRAMEWORK

TWISTPHISHER is a modular, all-in-one cybersecurity training toolkit designed for defensive security education, red-team simulation, and awareness training environments.

**Fully self-contained and locally operated.** No external API dependencies, no manual binary sourcing required. The framework automatically provisions and configures the required Cloudflare tunnel if it is not already present, ensuring seamless deployment and zero-friction setup.
---

## Features

- **33 High-Fidelity Phishing Page Templates**  Includes realistic replicas of widely recognized platforms such as Instagram, Facebook, Google, Netflix, PayPal, Steam, and more for controlled awareness training environments.
- **Multi-Channel Tunneling Support**   Flexible deployment via Cloudflare, Ngrok, or local host. Required Cloudflare components are automatically fetched and configured when absent.
- **Real-Time Visitor Intelligence** Captures and analyzes session metadata including IP address, geolocation (city, region, country), ISP, organization, and risk indicators such as VPN or hosting provider detection.
- **Advanced Device Fingerprinting**  Automatically identifies client devices and operating systems, including iOS, Android, Windows, macOS, and Linux, using User-Agent analysis.
- **Instant Credential Simulation Capture**   Demonstrates real-time submission handling where entered credentials are immediately displayed within the training dashboard for analysis purposes.d.
- **Integrated Spear-Phishing Simulation Module**   Supports controlled email-based social engineering simulations using SMTP services such as Gmail, Outlook, Yahoo, or custom servers.
-**Pre-Built Email Scenario Templates**
  Includes four core training templates (Password Reset, Security Alert, Shared Document, Invoice Notice), designed for awareness training scenarios. (Templates are AI-generated and intended for educational refinement.)
**Mandatory Educational Safety Banner**
  All generated emails include a clearly visible “EDUCATIONAL DEMONSTRATION ONLY” warning to ensure ethical usage compliance.
**Session Analytics Dashboard**
  Provides structured session insights including runtime duration, unique visitor count, and total simulated credential submissions for training evaluation.
---

PHP – Powers the local web server responsible for serving the training interfaces and handling form submissions.
CURL – Used for network requests, including geolocation lookups and SMTP/email-related operations.
PYTHON 3 – Handles structured JSON parsing and processing of IP intelligence data from external lookup services.
NGROK (Optional) – Provides an alternative secure tunneling option for exposing the local environment during testing sessions.

Automated Dependencies

No manual installation of Cloudflare binaries is required.
The framework automatically fetches and configures cloudflared on first execution if it is not already available.

---

## Installation

```bash
git clone https://github.com/whoamitang/Blackeye
cd twistphisher
bash twistphisher.sh
```

That's it. The only file you need to run is `twistphisher.sh`.

---

## Usage

Run:

```bash
bash twistphisher.sh
```

From the main menu, pick a phishing page (e.g. `01` for Instagram) or `E` for the email crafter.

If you chose a page, select a tunnel method:

1. **Cloudflare** — public URL via Cloudflare's free tunnel.
2. **Ngrok** — public URL via ngrok.
3. **Localhost** — only accessible on your machine.

Copy the displayed URL and send it to your test subject (yourself, a colleague, or a consenting student).

When someone opens the link and enters credentials, you'll see a real-time breakdown in your terminal.

Press `Ctrl+C` to stop the server and view a quick session summary.

---

## Email Crafter

1. Select `E` from the main menu.
2. Provide your SMTP details.
3. Choose a template.
4. Fill in target details and phishing URL.
5. Send or save a draft.

---

## How It Works

### Phishing Page Mode

- PHP built-in server (`php -S`) hosts the chosen page on `localhost:3333`.
- Tunnel exposes the port publicly.
- Visitors are logged to `ip.txt`.
- Credentials are written to `usernames.txt`.
- Captured credentials are appended to `master_creds.log`.

### Email Crafter Mode

- Generates HTML templates in `templates/`.
- Replaces placeholders like `{{TARGET_NAME}}` and `{{PHISH_LINK}}`.
- Uses `curl` SMTP requests to send mail.
- Success only reported on SMTP `250` response.

---

## Important Notes

- This tool is for education only.
- Never use it without explicit informed consent.
- Gmail users need 2FA + App Password.
- Cloudflared is downloaded from official releases.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Cloudflare tunnel fails | Ensure internet access. |
| SMTP test fails | Wrong credentials or wrong port. |
| Emails go to spam | Ask the recipient to check spam. |
| No visitor info shown | IP lookup may fail, credentials still log. |

---

## Legal Disclaimer

TWIST PHISHER is strictly intended for authorized cybersecurity training, educational purposes, and controlled laboratory environments only. Any use of this software against individuals, systems, or networks without explicit prior consent is strictly prohibited and may violate local, national, or international laws.

The end user bears full responsibility for ensuring compliance with all applicable regulations and laws governing their jurisdiction. The developers and contributors assume no liability or responsibility for any misuse, damage, or unlawful activity resulting from the use of this tool.

This framework must only be deployed in legally sanctioned and ethically approved security testing environments.

---

## Credits


### Phishing Page Authors

- Instagram — `not_twist`
- Facebook, Google, Snapchat, Twitter, Microsoft — Social Fish (`not_twist`)
- PayPal, eBay, CryptoCurrency, Verizon, Dropbox, Adobe ID, Shopify, Messenger, Twitch, MySpace, Badoo, VK, Yandex, DeviantArt — `@suljot_gjoka`

### v3.x Extensions

Spear-phishing email module, SMTP integration, geolocation enrichment, tunnel method selection, visitor deduplication, device detection, session summary, and educational disclaimers.

---

Yes this README.md was AI generated except this line... maybe.
