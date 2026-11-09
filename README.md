# kwtSMS for AI coding agents

A Claude Code plugin marketplace from [kwtSMS](https://www.kwtsms.com), the SMS gateway in Kuwait. The `kwtsms` plugin
gives Claude Code:

- **SMS tools** through the [kwtSMS MCP server](https://github.com/kwtsms/kwtsms-mcp): send SMS, balance, Sender IDs,
  coverage, number checks and message status. Preview and test mode by default; nothing reaches a phone until you
  switch live sending on.
- **A kwtSMS skill**: Claude knows the kwtSMS API, phone number rules, Arabic and English part counting, test mode and
  error codes when it writes or fixes your integration code.

## What you can ask Claude Code

- "Here is my customer list. Write a short Arabic offer for the weekend sale and send it to everyone."
- "Text everyone in this sheet whose order is ready."
- "When the build finishes, text me. If the tests fail, send me an SMS."
- "What is my balance? Which Sender IDs do I have? Did my last message arrive?"
- "Add OTP login by SMS to this app with kwtSMS, and test it in test mode."

Numbers are fixed for you (Arabic digits, `+`, `00`, spaces, duplicates), messages are cleaned, and every send starts
as a preview with the number of messages and credits. Nothing reaches a phone until you switch live sending on.

## Install

```bash
claude plugin marketplace add kwtsms/kwtsms-ai
claude plugin install kwtsms@kwtsms
```

Claude Code asks for your kwtSMS API username and password (the password goes to secure storage, the AI never sees it),
your Sender ID, and whether live sending is allowed (off by default).

Get an API username and password from your kwtSMS account ([sign up](https://www.kwtsms.com/cportal/signup/)). Use a
dedicated API user for AI tools, not your main login.

## Use it

> "What is my kwtSMS balance?"
>
> "Preview an SMS 'Your order is ready' to 965XXXXXXXX"
>
> "Add OTP login by SMS to this Laravel app using kwtSMS"

For sending, Claude shows a preview first (numbers, parts, credits). Test sends are not delivered; their credits are
held until you delete them from the Queue in your kwtSMS account. Live sends need your setting and your confirmation.

## Other AI tools

- Any MCP client (Claude Desktop, Cursor, VS Code): use [kwtsms-mcp](https://github.com/kwtsms/kwtsms-mcp) directly.
- Command line and scripts: [kwtsms-cli](https://github.com/kwtsms/kwtsms-cli).
- The skill in `plugins/kwtsms/skills/kwtsms/` follows the open Agent Skills format and works in other agents that
  read `SKILL.md` files.

## Support

[kwtsms.com/support.html](https://www.kwtsms.com/support.html)

## License

MIT
