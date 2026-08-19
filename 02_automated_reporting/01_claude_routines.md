# Automated Inbound Reports with Claude Routines

**What you'll learn**

How to get a daily inbound receiving report delivered automatically using Claude Routines, no Slack required.

**Prerequisites**

- [Connect Claude Desktop](../00_getting_started/01_connect_claude_desktop.md) completed

**The prompt**

In Claude Desktop, go to **Routines** in the sidebar, then paste this into the "What do you want automated?" box:

![Claude Desktop's Routines panel with the "What do you want automated?" box](../shared/screenshots/shipbob-mcp-claude-routines-panel.png)

```
Set up a routine that runs every day at 8am CT. Using the ShipBob MCP, report on the last 48 hours of inbound receiving activity plus all currently pending receiving orders. Write it for an inbound ops manager who has two minutes to read it and needs to know what to chase today.

Title it: Inbound Receiving Report - {date} ({start} to {end} CT)

At a glance
One line, no table: WROs received, WROs with discrepancies, units short, units over, pending WROs, oldest pending in days.

1. Needs review - received with discrepancies
[Table] WRO # | PO | SKU | Expected | Received | Stowed | Delta Recv | Delta Stow | Facility
Delta Recv = Received minus Expected. Delta Stow = Stowed minus Received. Show both signed (+3, -12) and use 0 when they match.
Sort by largest absolute delta first. One row per SKU, grouped by WRO.

2. Pending - not yet received
[Table] WRO # | PO | SKU | Expected | Status | Days Open | Facility
Sort oldest first. Flag anything open more than 7 days with a warning emoji next to Days Open.

3. Received clean - no discrepancies
[Table] WRO # | PO | SKU | Expected | Received | Stowed
Keep this one compact. If there are more than 10 rows, show a per-WRO roll-up instead of per-SKU rows.

4. Overall summary
2-3 sentences on inbound health: receipt accuracy trend, anything stuck, and the single most important thing to act on today.

Formatting rules
- If a section has no rows, write "None" instead of an empty table. Never invent or estimate data. If a field is unavailable from the MCP, put "n/a" and say so in the summary.
- Use plain whole numbers, no decimals, and keep SKU names short enough that columns stay aligned.
- Do not add sections beyond the four above.
```

**What to expect**

Claude creates a routine that runs on the schedule you gave it, without you needing to open Claude Desktop and ask each time. You'll see the routine listed under your scheduled routines, and can edit or delete it the same way.

The report is deliberately exception-first: the "at a glance" line tells you whether you need to read further, discrepancies come before clean receipts, and aging pending WROs are flagged. If your team cares about something else, tell Claude to swap a column or reorder a section, the structure holds.

You can extend this further: connect an email or Slack MCP, and the same routine can deliver the report straight to your inbox or a Slack channel instead of just sitting in your routines list.

**Try it yourself**

Compare this to the Claude Tag + Slack version up next: which one fits your team better, a routine that reaches you directly, or a report that posts where your team already collaborates?
