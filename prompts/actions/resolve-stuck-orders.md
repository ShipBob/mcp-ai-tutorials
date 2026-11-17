# Resolve Stuck Orders

**Use it when:** orders are sitting on hold or in exception and you want them moving again before the peak backlog grows.

**Works in:** Claude, ChatGPT, Bobby

**Changes data?** Yes, but only after you confirm each batch.

**The prompt**

```
Using the ShipBob MCP, find all my shipments that are currently on hold or in exception.

Step 1. Group them by reason and show one table: reason, number of shipments, oldest in days, and the fix for that reason. Use these fixes:
- Manual hold or auto processing pause: release the hold.
- Invalid address: show me each address so I can correct it. Do not change addresses without my corrected version.
- Out of stock: show which SKUs are short, and whether another in-stock SKU could be swapped in.
- Any other reason: explain what it means and what I need to do, in one line.

Step 2. Stop and wait. Do not change anything until I reply with which groups to fix.

Step 3. For each group I approve, show me the exact shipment IDs you will change, then wait for my "yes" before making the change. After each batch, report how many succeeded, how many are still on hold for another reason, and any errors.
```

**What you get**

First, a single table that turns a long list of stuck orders into a handful of groups, each with its fix. Then nothing happens until you choose. When you approve a group, you see exactly which shipments change before anything is touched.

**Good to know**

- Releasing holds only removes holds you or your team placed (manual holds and auto processing pauses). Holds placed for operational reasons, like an invalid address, stay until the underlying problem is fixed. The report tells you when a released shipment is still held for another reason.
- Shipments that are already being picked or packed can't be changed. The assistant will say so instead of failing quietly.

**Make it yours**

- Limit it to one fulfillment center or one channel: "only shipments from my Amazon channel".
- Run it twice a day during Black Friday weekend so holds never sit overnight.
