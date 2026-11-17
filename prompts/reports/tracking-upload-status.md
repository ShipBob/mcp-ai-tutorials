# Tracking Upload Status

**Use it when:** customers are asking "where is my order?" and you want to confirm that tracking for every shipped order made it back to your store.

**Works in:** Claude, ChatGPT, Bobby

**Changes data?** No. Read-only.

**The prompt**

```
Using the ShipBob MCP, check tracking for shipments shipped in the last 3 days. Time zone: {your time zone}.

1. At a glance, one line: shipments shipped, shipments with a tracking number, shipments still awaiting the first carrier scan after 24 hours, and shipments whose tracking has not been marked as uploaded to my store (if that status is available).
2. Table: shipments shipped more than 24 hours ago that are still awaiting a carrier scan. Columns: store order ID, shipment ID, shipped date, carrier, tracking number, fulfillment center. Oldest first.
3. Table: shipments whose tracking has not been marked as uploaded to my store, grouped by sales channel, with counts and the oldest one.
4. Two-sentence summary: is this a carrier scanning delay or a store sync problem, and what should I do first?

Rules: use only ShipBob MCP data. If tracking upload status is not available, say so in one line instead of guessing.
```

**What you get**

A short check that separates two different problems: packages the carrier hasn't scanned yet, and tracking that hasn't synced back to your store. Each needs a different fix, so the summary tells you which one you're looking at.

**Make it yours**

- Change "24 hours" to "48 hours" on weekends, when carrier scans are slower.
- Add "only for orders over {order value}" to focus on high-value orders.
