# Re-route Expensive Orders

**Use it when:** some unshipped orders are going to ship from a fulfillment center far from the customer, and a closer one has the stock.

**Works in:** Claude, ChatGPT, Bobby

**Changes data?** Yes, but only after you confirm.

**The prompt**

```
Using the ShipBob MCP, find my shipments that have not started picking yet and are assigned to a fulfillment center far from the customer.

Step 1. List the fulfillment centers I have access to and where they are.

Step 2. For each unshipped shipment that has not started picking, compare the destination state with my fulfillment centers. Flag the shipment if another of my fulfillment centers is clearly closer to the customer.

Step 3. For every flagged shipment, check that the closer fulfillment center has enough fulfillable inventory for every item in the shipment. Drop any shipment where it does not.

Step 4. Show me a table: shipment ID, store order ID, destination state, current fulfillment center, suggested fulfillment center, items, and "stock confirmed". Group it by suggested fulfillment center.

Step 5. Stop and wait. Only after I reply "yes" for a group, reassign those shipments to the suggested fulfillment center. Then report successes, failures, and the reason for each failure.
```

**What you get**

A short list of orders that could ship from a closer warehouse, each one already checked for stock at the new location. Nothing moves until you approve.

**Good to know**

- Reassigning a shipment does not check stock at the new fulfillment center by itself. That's why step 3 checks stock first: without it, a moved shipment could land in an out-of-stock exception.
- Shipments that are being picked, packed, or already shipped can't be reassigned.
- This moves individual orders. To move inventory itself between fulfillment centers before peak, plan an inbound shipment with the [WRO tutorial](../../01_inbound_and_wro/01_creating_a_wro.md).

**Make it yours**

- Focus on your largest orders: "only shipments with 3 or more units".
- Run [Cost and Zone Map](../reports/cost-and-zone-map.md) first to see which states drive the most far-zone orders.
