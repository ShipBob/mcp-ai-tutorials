# Automated Inbound Reports with Claude Tag + Slack

**What you'll learn**

How to set up Claude Tag in Slack, then use it to get the same daily inbound receiving report as the Claude Routines tutorial, but posted to a Slack channel your team already watches, by tagging @Claude.

**Prerequisites**

- [Connect Claude Desktop](../00_getting_started/01_connect_claude_desktop.md) completed
- A Slack workspace where you're a Primary Owner or Owner (only owners can set up Claude Tag)

**Setting up Claude Tag**

[Claude Tag](https://support.claude.com/en/articles/15594475-what-is-claude-tag) is Anthropic's own Slack integration: tag @Claude in a channel and it works using your organization's connected tools, including ShipBob MCP, under its own workspace identity, not any one person's account.

Setup is a one-time, admin-only job:

1. A Primary Owner or Owner installs Claude Tag into your Slack workspace and provisions Claude's workspace identity.
2. Connect ShipBob MCP the same way you'd connect any other tool, so Claude Tag can query your live fulfillment data.
3. Choose where Claude Tag can work: organization-wide, specific public channels, or a private channel for sensitive work.
4. Optional: set a spend limit per channel or for the whole workspace, with alerts at 75% and 95% usage, so costs stay predictable.

Once that's done, anyone in an enabled channel can just tag @Claude, no separate install per person.

For a walkthrough of this setup, see [this video from Anthropic/Claude itself](https://www.youtube.com/watch?v=JhipXUs1Y98).

**The prompt**

In the Slack channel where you want the report, tag Claude and ask it to set up a recurring post:

```
@Claude every day at 8am CT, using the ShipBob MCP, post the last 48 hours of inbound receiving activity plus all currently pending receiving orders. Write it for an inbound ops manager scanning Slack on their phone, so keep it tight and lead with what needs action.

Title it: Inbound Receiving Report - {date} ({start} to {end} CT)

At a glance
One line, no table: WROs received, WROs with discrepancies, units short, units over, pending WROs, oldest pending in days.

1. Needs review - received with discrepancies
[Table] WRO # | SKU | Expected | Received | Stowed | Delta Recv | Delta Stow
Delta Recv = Received minus Expected. Delta Stow = Stowed minus Received. Show both signed (+3, -12) and use 0 when they match.
Sort by largest absolute delta first. One row per SKU, grouped by WRO. Put the PO and facility in a short line under each WRO group rather than in the table.

2. Pending - not yet received
[Table] WRO # | SKU | Expected | Status | Days Open
Sort oldest first. Flag anything open more than 7 days with a warning emoji next to Days Open.

3. Received clean - no discrepancies
One line per WRO, not a table: WRO #, SKU count, total units received. No per-SKU detail unless something is off.

4. Overall summary
2-3 sentences on inbound health: receipt accuracy trend, anything stuck, and the single most important thing to act on today.

Formatting rules
- Keep tables to 7 columns or fewer so they stay readable in Slack on mobile. Never wrap a table in a code block.
- If a section has no rows, write "None" instead of an empty table. Never invent or estimate data. If a field is unavailable from the MCP, put "n/a" and say so in the summary.
- Use plain whole numbers, no decimals. Do not add sections beyond the four above.
```

**What to expect**

Claude confirms the schedule back to you in the thread. From then on, the report posts to the channel automatically at that time every day, no one has to ask for it. You can adjust the schedule or the report format later by tagging Claude again with the change.

The report is exception-first: the "at a glance" line tells the channel whether anyone needs to read further, discrepancies come before clean receipts, and aging pending WROs are flagged. It is also narrower than the [Claude Routines version](01_claude_routines.md), because wide tables wrap badly in Slack on mobile. PO and facility move to a line under each WRO group, and clean receipts collapse to one line per WRO instead of a per-SKU table.

**Try it yourself**

Compare this to the Claude Routines version: which one fits your team better, a report that posts where your team already collaborates, or a routine that reaches you directly?
