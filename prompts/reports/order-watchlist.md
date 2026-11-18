# Order Watchlist

**Use it when:** a handful of orders matter more than the rest (VIP customers, wholesale, large orders, influencer sends) and you want to follow just those.

**Works in:** Claude (as an interactive artifact), ChatGPT, Bobby

**Changes data?** No. Read-only.

**The prompt**

```
Using the ShipBob MCP, build my order watchlist as an interactive artifact. Time zone: {your time zone}.

Watch these orders: {pick one: "orders placed in the last 7 days with {N} or more units" / "these store order IDs: {ID, ID, ID}" / "all B2B orders from the last 14 days"}.

For each order show one row: store order ID, recipient city and state, purchase date, current status, last tracking event and its time, and target delivery date if available.

Add a status pill to every row:
- Red: on hold, in exception, or delivery exception.
- Amber: shipped more than 3 days ago and not delivered, or not shipped yet and older than 2 days.
- Green: delivered, or moving normally.

Sort red first, then amber, then green. Above the table, one line: how many orders are red, amber and green.

Rules: use only ShipBob MCP data. If a field is unavailable, show "n/a".
```

**What you get**

A traffic-light list of the orders you care about most, with problems at the top. You stop checking orders one by one and only open the red and amber ones.

**Make it yours**

- Save your watch rule and rerun it every morning, or add it to [Night Shift Watch](../automations/night-shift-watch.md).
- During a gift promotion, watch the orders that received the gift: "orders containing {gift SKU} since {start date}". See [Gift With Purchase](../gifting/gift-with-purchase.md).
