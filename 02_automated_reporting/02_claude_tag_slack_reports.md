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
@Claude every day at 8am CT, summarize the last 48 hours of inbound receiving activity using the ShipBob MCP, plus all currently pending receiving orders. Use this format:

Received (in last 48 hours)
[Table] WRO # | PO | SKU | Quantity Expected | Received | Stowed | Summary

{Summary should include "No discrepancies" or "x units short" or "x units over received"}

Pending (All)
[Table] WRO # | PO | SKU | Quantity Expected | Status

Overall summary
{2-3 sentence summary of inbound health}
```

**What to expect**

Claude confirms the schedule back to you in the thread. From then on, the report posts to the channel automatically at that time every day, no one has to ask for it. You can adjust the schedule or the report format later by tagging Claude again with the change.

**Try it yourself**

Compare this to the Claude Routines version: which one fits your team better, a report that posts where your team already collaborates, or a routine that reaches you directly?
