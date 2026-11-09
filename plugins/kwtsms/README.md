# kwtSMS plugin

Send SMS from Claude through [kwtSMS](https://www.kwtsms.com), the SMS gateway in Kuwait, and get help writing kwtSMS
integrations.

## What it adds

- **SMS tools** (the [kwtsms-mcp](https://github.com/kwtsms/kwtsms-mcp) server, version 0.1.2, started with
  `npx -y kwtsms-mcp@0.1.2`): send SMS, balance, Sender IDs, coverage, number checks and message status.
- **A kwtSMS skill**: campaigns to a customer list, customer notices, alerts to yourself, SMS login codes (OTP),
  Arabic and English message writing, and what each kwtSMS error code means.

## What it sends and where

The SMS tools call only the kwtSMS API at `https://www.kwtsms.com/API/` (send, balance, senderid, coverage,
validate, status), with your API username and password, the numbers and the message you ask for. Nothing else is
sent anywhere. The password is stored as a sensitive setting and is never shown to the model.

## Safe by default

Every send starts as a preview (numbers, SMS parts, credits). Test messages are not delivered. Live sending works only
after you turn it on in the plugin settings, and each live send needs a confirmation. Limits per call, per hour and per
day apply, and only Kuwait numbers are allowed until you change the settings.

## Set up

1. Open a free kwtSMS account: https://www.kwtsms.com/cportal/signup/
2. Copy your API username and API password from the API Information page of your account.
3. Install: `claude plugin install kwtsms --marketplace kwtsms/kwtsms-ai`, then `/plugin configure kwtsms@kwtsms`.

The SMS tools need Node.js 18 or newer and work in Claude Code and in Cowork sessions on your computer. On claude.ai
chat only the skill loads. Support: https://www.kwtsms.com/support.html. License: MIT.
