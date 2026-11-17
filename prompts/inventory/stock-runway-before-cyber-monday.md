# Stock Runway Before Cyber Monday

**Use it when:** you want to know which SKUs will run out before Cyber Monday (Nov 30, 2026) or before the last holiday shipping days, while there is still time to act.

**Works in:** Claude (as an interactive artifact), ChatGPT, Bobby

**Changes data?** The report is read-only. The optional swap in part 2 changes orders, but only after you confirm.

**Part 1: the runway chart**

```
Using the ShipBob MCP, build a stock runway chart as an interactive artifact. Today is {today's date}. Time zone: {your time zone}.

1. For every active SKU, get the current fulfillable quantity and the average daily units shipped over the last 28 days.
2. Days left = fulfillable quantity divided by average daily units shipped. Skip SKUs with no units shipped in the last 28 days.
3. Draw a horizontal bar per SKU showing days left, with a vertical line at Cyber Monday (Nov 30, 2026) and a second line at Dec 15, 2026.
4. Color each bar: red if it runs out before Nov 30, amber if before Dec 15, green otherwise.
5. Below the chart, a table of red and amber SKUs: SKU, name, fulfillable units, average daily units, days left, run-out date, and inbound units already on open receiving orders.

Rules: use only ShipBob MCP data. If a SKU's sales history or inbound quantity is unavailable, mark it "n/a" instead of estimating. Note that peak sales usually run faster than the last 28 days, so treat these dates as the latest possible run-out dates.
```

**Part 2: swap in a substitute (optional)**

```
For SKU {SKU that is out of stock}, find my open shipments that are in an out-of-stock exception and contain it.

Show me the list first: shipment ID, store order ID, quantity of {SKU that is out of stock}. Then propose swapping it for {substitute SKU} at {quantity} each, and confirm that {substitute SKU} has enough fulfillable stock to cover all of them.

Wait for my "yes". Then update each shipment, keeping every other line item exactly as it is, and report successes and failures.
```

**What you get**

A chart that answers "will I make it to Cyber Monday?" for every SKU at a glance, with red and amber SKUs listed alongside any stock already on its way. Part 2 turns a stock-out into a fix you approve, instead of a pile of exception orders.

**Good to know**

- Updating line items replaces the whole list of items on a shipment, which is why part 2 says to keep every other item as it is. The assistant reads the current items first.
- Bundles can't be swapped this way. Swap the individual items instead.
- Only swap when your customer would be happy with the substitute, for example a 3-pack in place of a sold-out single.

**Make it yours**

- Use a 14-day average instead of 28 if sales picked up recently.
- Add "only SKUs in my top 50 by units" to keep the chart readable.
