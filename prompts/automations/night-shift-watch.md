# Night Shift Watch

**Use it when:** you want your operation checked while you're offline, especially across the Thanksgiving to Cyber Monday weekend, so Saturday morning doesn't start with a backlog nobody saw on Friday night.

**Works in:** Claude Desktop (Routines). Also works as a scheduled message in Slack with Claude Tag, see [Automated Reporting](../../02_automated_reporting/).

**Changes data?** No. Read-only. It reports; you decide.

**The prompt**

In Claude Desktop, go to **Routines** and paste this into the "What do you want automated?" box. The [Claude Routines tutorial](../../02_automated_reporting/01_claude_routines.md) shows where that is.

```
Set up a routine that runs every day at {6am} {your time zone}, including weekends and holidays. Using the ShipBob MCP, check what changed since the last run and write a night shift report for someone who has one minute to read it.

Title it: Night Shift Watch - {date}

At a glance
One line: new holds, new exceptions, SKUs that crossed into low stock, receiving orders that arrived, shipments still awaiting a carrier scan after 24 hours.

1. New holds and exceptions since the last run
[Table] Reason | Shipments | Oldest (hours) | What to do

2. Low stock alerts
SKUs that now have fewer than {7} days of stock at the last 28 days' average daily units shipped.
[Table] SKU | Name | Fulfillable | Days left

3. Inbound
Receiving orders that arrived, partially arrived or completed since the last run.
[Table] WRO # | PO | Status | Units expected | Units received

4. Carrier scans
Shipments shipped more than 24 hours ago that are still awaiting a first carrier scan, grouped by carrier, with counts.

5. One thing to do first
One sentence.

Rules
- If a section has nothing new, write "Nothing new" instead of an empty table.
- Never invent or estimate data. If something is unavailable from the MCP, write "n/a" and say so.
- Do not change any orders, products or holds. This routine only reports.
```

**What you get**

A short report waiting for you every morning, holidays included. Each section tells you only what changed overnight, so an all-quiet night takes ten seconds to read.

**Make it yours**

- Add a second run at {6pm} on Black Friday and Cyber Monday.
- Send it to email or Slack by connecting their MCPs, as described in [Automated Reporting](../../02_automated_reporting/).
- When the report shows stuck orders, open [Resolve Stuck Orders](../actions/resolve-stuck-orders.md).
