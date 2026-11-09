# kwtSMS

Send SMS from Claude through [kwtSMS](https://www.kwtsms.com), the Kuwaiti SMS gateway. Tell Claude what to send and to
whom, in English or Arabic: it writes the message, fixes the numbers, shows you the cost, and sends when you approve.
It also helps developers build SMS and OTP into their apps.

kwtSMS delivers to Zain, Ooredoo, stc and Virgin in Kuwait and to more than 200 countries, with your own Sender ID.

## What it adds

- **SMS tools** (the open source [kwtsms-mcp](https://github.com/kwtsms/kwtsms-mcp) server, version 0.2.1):
  - `preview_sms`: checks the numbers, cleans the message, counts SMS parts and credits. Sends nothing.
  - `send_test_sms`: test send, not delivered to any phone.
  - `send_sms`: real SMS, only when you switch live sending on. Claude asks you before each one.
  - `get_balance`, `list_sender_ids`, `check_coverage`, `validate_numbers`, `get_message_status`.
- **A kwtSMS skill**: campaigns to a customer list, customer notices, alerts to yourself, SMS login codes (OTP),
  Arabic and English messages that fit in one SMS, and what each kwtSMS error code means.

## Example prompts

- "What is my kwtSMS balance, and which Sender IDs do I have?"
- "Here is my customer list. Write a short Arabic offer for the weekend sale and show me the preview and the cost."
- "Text everyone in this sheet whose order is ready. Keep it to one SMS."
- "When the build finishes, text me the result."
- "Add SMS login codes (OTP) to this app with kwtSMS, and test it in test mode."

## What it sends and where

The SMS tools call only the kwtSMS API at `https://www.kwtsms.com/API/` (send, balance, senderid, coverage,
validate, status), with your API username and password, the numbers and the message you ask for. Nothing else is
sent anywhere, and nothing is stored. The password is kept as a sensitive setting and is never shown to the model.
Privacy policy: https://www.kwtsms.com/privacy.html

## Safe by default

- Every send starts as a preview: numbers, SMS parts and credits.
- Test messages are not delivered. Their credits are held until you delete them from the Sending Queue in your kwtSMS
  account.
- Real sending works only after you turn on "Allow live sending" in the plugin settings, and Claude asks you before
  each real send.
- Limits per call, per hour and per day, and Kuwait numbers only, until you change them.
- Your Sender ID is fixed in the settings: Claude cannot pick another one.

## Set up in 3 steps

1. Open a free kwtSMS account: https://www.kwtsms.com/cportal/signup/
2. Copy your API username and API password from the API Information page of your account. They are not your mobile
   number or your account login. Use a separate API user for AI tools.
3. Add the plugin and enter them in its settings:
   - Claude app: Customize, Plugins, find kwtSMS, add it.
   - Claude Code: `claude plugin install kwtsms --marketplace kwtsms/kwtsms-ai`, then `/plugin configure kwtsms@kwtsms`.

Then ask: "What is my kwtSMS balance?"

## Where it works

The SMS tools run on your computer and need Node.js 18 or newer: they work in Claude Code and in Cowork sessions on
your computer. In claude.ai chat only the skill loads.

## Troubleshooting

- **ERR003, wrong username or password**: use the API username and password from the API Information page. Stop and
  check them before trying again: repeated wrong-password calls from one address get that address blocked. If that
  happened, fix the password and contact kwtSMS support to unblock it.
- **Test message did not arrive**: test sends are never delivered. Turn on live sending for real SMS.
- **"Live sending is switched off"**: turn on "Allow live sending" in the plugin settings.
- **A send was refused for a limit**: the limits protect you from a mistake. Raise them in the plugin settings:
  numbers per send, numbers per hour, credits per day, allowed country codes.
- **The tools do not appear**: install Node.js 18 or newer from https://nodejs.org, then restart Claude.

## بالعربي

أرسل رسائل SMS من Claude عبر kwtSMS. اكتب ما تريد إرساله ولمن، فيكتب الرسالة ويصحح الأرقام ويعرض عدد النقاط قبل
الإرسال، ولا يرسل إلا بموافقتك. الإرسال التجريبي لا يصل إلى الهاتف، والإرسال الفعلي متوقف حتى تفعّله من الإعدادات.
افتح حساباً مجانياً على https://www.kwtsms.com/cportal/signup/ ثم انسخ اسم المستخدم وكلمة المرور من صفحة تفاصيل
البوابة في حسابك.

## Support

Help: https://www.kwtsms.com/support.html | FAQ: https://www.kwtsms.com/faq/ |
API reference: https://www.kwtsms.com/api-documentation.html | Issues: https://github.com/kwtsms/kwtsms-ai/issues

## License

MIT, (c) kwtSMS (BoxLink Center).
