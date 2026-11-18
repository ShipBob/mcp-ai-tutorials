# Peak War Room

**Use it when:** you start your day during peak and want one screen that tells you what needs action.

**Works in:** Claude (as an interactive dashboard), ChatGPT, Bobby

**Changes data?** No. Read-only.

**The prompt**

```
Using the ShipBob MCP, build my peak morning brief as an interactive artifact. Time zone: {your time zone, e.g. America/Chicago}. "Yesterday" means the full previous calendar day in that time zone.

Top row, five tiles, each with one number and one line on what to do about it:
1. Orders in: orders imported yesterday, compared with the same weekday last week.
2. Shipped: shipments shipped yesterday, and how many of them shipped on time.
3. Stuck: shipments currently on hold or in exception, split by reason.
4. Low stock: active SKUs with fewer than 7 days of stock left at the last 28 days' average daily units shipped.
5. Inbound: receiving orders that arrived or completed yesterday, plus any open ones past their expected date.

Below the tiles:
- A "Needs action today" list, most urgent first, max 10 rows. Each row says what is wrong, how many orders or SKUs it affects, and the next step in plain words.
- A small table of stuck shipments grouped by hold or exception reason, with counts and the oldest one in days.
- A low stock table: SKU, name, fulfillable units, average daily units, days left. Sort by days left, shortest first.

Rules:
- Only use data returned by the ShipBob MCP. If a number is not available, show "n/a" and say why in one line. Never estimate.
- Keep it to one screen. Whole numbers, no decimals except for days left (one decimal).
```

**What you get**

A single dashboard with five tiles across the top and a short, ranked to-do list underneath. Stuck orders come grouped by reason, so you can see straight away whether it's one problem (for example a batch of invalid addresses) or many small ones.

See an example: [sample report (PDF)](samples/peak-war-room-sample.pdf), made with fictional data for Watches Inc.

**Make it yours**

- Change "fewer than 7 days" to match your reorder lead time.
- Add a sixth tile for a channel you care about: "Orders in from TikTok Shop yesterday".
- Pair it with [Night Shift Watch](../automations/night-shift-watch.md) so the same brief is waiting for you every morning.

**Next step**

Anything in the "Stuck" tile can be worked through with [Resolve Stuck Orders](../actions/resolve-stuck-orders.md). Anything in "Low stock" goes to [Stock Runway Before Cyber Monday](../inventory/stock-runway-before-cyber-monday.md).
