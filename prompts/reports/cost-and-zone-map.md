# Cost and Zone Map

**Use it when:** you want to see where your orders ship to, which shipping zones cost you the most, and whether your inventory sits in the right fulfillment centers for peak.

**Works in:** Claude (as an interactive artifact), ChatGPT, Bobby

**Changes data?** No. Read-only.

**The prompt**

```
Using the ShipBob MCP, analyze my last 60 days of shipped orders and build a cost and zone report as an interactive artifact.

1. Headline tiles: total fulfillment cost, cost per order, and average shipping zone.
2. A bar chart of the share of orders by shipping zone (zone 1 to zone 8), with cost per order shown for each zone.
3. A US map shaded by share of orders per destination state.
4. A table by fulfillment center: orders shipped, average zone, cost per order.
5. "Far zone hot spots": the 5 destination states that most often ship zone 6 or higher, with order counts and the fulfillment center they currently ship from.

End with a short recommendation: which fulfillment center would bring the most far-zone orders closer, and which top 5 SKUs by units shipped to those states I would need to stock there.

Rules: use only ShipBob MCP data. Cost figures are top-line totals, not component splits. If any figure is unavailable, mark it "n/a" and do not estimate.
```

**What you get**

A one-page view of your shipping footprint: how orders spread across zones, what each zone costs, and the states that drive your far-zone shipping. The closing recommendation names a fulfillment center and the SKUs that would need to be stocked there.

**Make it yours**

- Narrow it to one channel: "only orders from my Shopify store".
- Swap 60 days for "last November" to see last year's peak footprint.

**Next step**

To move stock between fulfillment centers ahead of peak, start an inbound plan with the [WRO tutorial](../../01_inbound_and_wro/01_creating_a_wro.md).
