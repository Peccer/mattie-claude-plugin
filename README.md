# Mattie for Claude

Mattie finds a moment when your group of friends can all meet, and afterwards keeps track of who paid what. This plugin connects Claude to the Mattie server and adds a skill that walks Claude through the whole flow: make a group, ask everyone when they can, pick the best time, send a calendar invite (with the outing's WhatsApp group link if you have one), and settle the costs.

Mattie is free to use. If it saves you a WhatsApp thread of 200 messages, you can [buy me a coffee](https://buymeacoffee.com/master.your.tasks).

## What's in this plugin

| Part | What it does |
|---|---|
| `.mcp.json` | Adds the remote MCP server `https://mattie.taskmastergpt.nl/mcp` (Streamable HTTP, OAuth sign-in with Google) |
| `skills/plan-with-friends` | Tells Claude how to use Mattie's tools, including how to read calendar screenshots itself |

The plugin has no code of its own. It runs nothing on your computer.

## Install

In Claude Code:

```
/plugin marketplace add Peccer/mattie-claude-plugin
/plugin install mattie@mattie
```

In Claude (web, desktop or mobile) you can also add Mattie as a connector by URL: `https://mattie.taskmastergpt.nl/mcp`.

The first time Claude uses a Mattie tool, you sign in with Google. Mattie only gets your name and e-mail address.

Setup guide, troubleshooting and more examples: <https://mattie.taskmastergpt.nl/en/claude>.

## Example prompts

- "Find an evening next week, Friday or Saturday, 3 hours, when my climbing crew is free."
- "Who still has to answer for the dinner?"
- "Here's a screenshot of Bob's calendar, put it in for him."
- "Make an invite for Saturday 19:00 at Café de Klok, here's our WhatsApp group: https://chat.whatsapp.com/..."
- "Split Saturday's costs: I paid €84 for dinner for all four of us, Anna paid €24 for drinks for her and Bob."

## Data and privacy

What the plugin sends, and where:

- **Only to Mattie** (`mattie.taskmastergpt.nl`), and only what a tool needs: group names, friends' names and e-mail addresses, the request window, busy times, cost entries, and the details of an invite (title, place, time, WhatsApp group link). Mattie never gets your conversation with Claude.
- **Calendars:** a friend's calendar is read only after that friend says yes on their own link, for one request, and only free/busy (no titles, places or guests). Google Calendar, Outlook (personal accounts) and Apple iCloud work; an iCloud app-specific password is typed on Mattie's page, never in the chat, and forgotten after the one read. Shared availability is deleted within 72 hours.
- **Screenshots:** Claude reads them, not Mattie. Claude sends only the busy times you checked, never the image.
- **Invites:** Mattie stores nothing for an invite; it lives in the link itself. Mattie never contacts WhatsApp: the group link is only put in the invite.
- **Costs:** Mattie keeps the score and shows who pays whom. It never moves money. Cost lists are deleted 90 days after the last change.
- **Delete everything:** ask Claude "delete my Mattie account", or go to Account on the website.

Full policy: <https://mattie.taskmastergpt.nl/en/privacy> (English) or <https://mattie.taskmastergpt.nl/privacy> (Dutch, leading). Terms: <https://mattie.taskmastergpt.nl/en/terms> (English) or <https://mattie.taskmastergpt.nl/voorwaarden> (Dutch).

## Languages

Mattie's pages (the group link your friends open, the consent and cost pages, the website) are in Dutch and English. Every page has an NL / EN switch at the top, and a friend's browser language decides the first view. The setup guide is also available in Dutch: <https://mattie.taskmastergpt.nl/claude>.

## Support

Questions or a security issue: see <https://mattie.taskmastergpt.nl/.well-known/security.txt> or the contact link on <https://mattie.taskmastergpt.nl>.

## License

MIT
