---
name: plan-with-friends
description: Plan a meet-up with a group of friends through Mattie - find a time everyone can make, read calendar screenshots the user shares, and split the costs afterwards. Use when the user wants to find a moment with friends, asks who can make it, shares a screenshot of a calendar for an outing, or wants to settle who pays whom.
---

# Plan a meet-up with Mattie

Mattie's tools come from the `mattie` MCP server in this plugin. The first call asks the user to sign in with Google.

## Find a time

1. `list_groups`. If there is no group yet, `create_group` with the friends' names and e-mail addresses (ask for them; never guess an e-mail).
2. `request_availability` with the window, duration, earliest/latest time and weekdays the user wants. Give the user `share_url` to post in the group chat. It is shown only once.
3. Later, `get_request_status` shows who answered. `find_meeting_times` gives the windows when everyone (or `min_attendees`) can make it.
4. If someone joined the group later, use `add_to_request`. The user corrects their own answer with `update_my_availability`.

Calendars are read only after each person says yes on their own link, and consent covers one request. For a new search, start a new request.

On that link each friend picks Google Calendar, Outlook (personal accounts) or Apple iCloud, or ticks the moments that suit them. For iCloud, the friend creates an app-specific password at account.apple.com (Sign-In and Security, App-Specific Passwords) and types it on Mattie's page. Never ask for an Apple ID password or app-specific password in the chat, and if someone pastes one, tell them not to share it here and to use the link instead. Many iPhone users actually keep their calendar in Google or Outlook (Settings, Calendar, Accounts); then that button is easier.

## Language

Mattie's tools answer in English; talk to the user in their own language. The pages behind the links (group link, consent, cost list) are in Dutch and English: they follow each friend's browser language, and every page has an NL / EN switch at the top. If a friend says the page is in the wrong language, point them to that switch. Invitation e-mails that Mattie sends are in Dutch with the English text below.

## Calendar screenshots

When the user shares a screenshot of a calendar (their own, or one a friend sent them):

1. Read it yourself. List every appointment that falls inside the request window as a start and end time, in the request's local time. Leave out titles, places and other people's names.
2. Show the list to the user and ask if it is right. Fix what they correct.
3. Call `submit_busy_times` with `request_id`, the `busy` list and, for a friend, `person`. An empty list means free the whole window.

Mattie never sees the image. You can fill in for a friend only while that friend hasn't answered yet; an answer someone gave themself can't be overwritten.

## Split the costs

After the outing, `start_costs` makes a cost list with one link for the group chat. Use `add_expense` for who paid how much for whom, `get_costs` for balances and who pays whom, and `record_payment` once someone has paid back. Mattie only keeps the score. It never moves money. Each person can add their own Tikkie or bunq.me link with `set_my_payment_link`.

## Deleting data

Tools that delete something (`delete_group`, `cancel_request`, `delete_cost_list`, `delete_my_account`) need a clear yes from the user first.
