# Gift With Purchase: First 1,000 Orders

**Use it when:** you want to surprise your first customers of the season with a free holiday gift, while supplies last. Your store listing doesn't change: the customer buys the product as usual, and ShipBob adds the gift to the box.

**Works in:** Claude, ChatGPT, Bobby. Part 2 uses Claude Desktop Routines.

**Changes data?** Yes. It adds the gift to orders, but only after you confirm (or, in part 2, only within the exact rule you approve).

## The example

Watches Inc runs a holiday promotion: the first 1,000 orders that include their best-selling watch get a free screen cleaning kit.

| | SKU | Name |
|---|---|---|
| Hero product (what the customer buys) | `WATCH-CLASSIC-40` | Classic 40mm Watch |
| Holiday gift (what ShipBob adds) | `GIFT-CLEANKIT-HOL` | Holiday Screen Cleaning Kit |

Replace these with your own SKUs. The gift needs to be a product in ShipBob with stock at your fulfillment centers.

## How it works

Your store sends orders for `WATCH-CLASSIC-40` to ShipBob as usual. Before the warehouse starts picking an order, the assistant adds 1 `GIFT-CLEANKIT-HOL` to it. It counts the orders that already have the gift, so it stops at exactly 1,000.

## Part 1: start the promotion

```
Using the ShipBob MCP, run a gift-with-purchase promotion.

Hero SKU: WATCH-CLASSIC-40
Gift SKU: GIFT-CLEANKIT-HOL, 1 unit per order
Limit: the first 1,000 orders containing the hero SKU
Promotion start: {Nov 26, 2026 00:00} {your time zone}

Step 1. Readiness check.
- Is there enough fulfillable stock of GIFT-CLEANKIT-HOL for 1,000 gifts? If not, how many can it cover?
- How many orders per day contained WATCH-CLASSIC-40 over the last 28 days, and roughly how many days until 1,000 orders at that pace?

Step 2. Count gifts already given: shipments purchased since the promotion start that contain both WATCH-CLASSIC-40 and GIFT-CLEANKIT-HOL. Remaining gifts = 1,000 minus that count. If remaining is 0, stop and tell me the promotion is complete.

Step 3. Find eligible shipments: purchased since the promotion start, containing WATCH-CLASSIC-40, not already containing GIFT-CLEANKIT-HOL, and not yet picked or shipped. Take the oldest purchases first, up to the remaining number.

Step 4. Show me a table: shipment ID, store order ID, purchase date, current items. Above it, one line: gifts given so far, gifts remaining, eligible shipments found. Stop and wait for my "yes".

Step 5. For each approved shipment, read its current line items and add GIFT-CLEANKIT-HOL quantity 1, keeping every existing item and quantity exactly as it is. Report successes, failures with the reason, and the new gifts-given total.

Rules: use only ShipBob MCP data. Never go over 1,000 gifts. Never remove or change the customer's items.
```

## Part 2: keep it running until 1,000

Orders keep arriving all weekend, and the gift has to be added before picking starts. Set up a routine so it happens without you. In Claude Desktop, go to **Routines** and paste:

```
Set up a routine that runs every {30 minutes}, starting {Nov 26, 2026 00:00} {your time zone}, including nights and weekends.

Each run, using the ShipBob MCP, follow the gift-with-purchase rule below.

Hero SKU: WATCH-CLASSIC-40
Gift SKU: GIFT-CLEANKIT-HOL, 1 unit per order
Limit: the first 1,000 orders containing the hero SKU, purchased since {Nov 26, 2026 00:00} {your time zone}

1. Count shipments since the start that contain both SKUs. If the count has reached 1,000, stop changing orders and report "Promotion complete".
2. Find shipments since the start that contain WATCH-CLASSIC-40, do not contain GIFT-CLEANKIT-HOL, and have not been picked or shipped. Oldest purchase first, never more than the gifts remaining.
3. I approve adding GIFT-CLEANKIT-HOL quantity 1 to those shipments without asking me each time, only under this exact rule. Keep every existing item and quantity exactly as it is. Change nothing else.
4. Report: gifts added this run, total gifts given, gifts remaining, gift stock left, and any failures with the reason.

If gift stock drops below the gifts remaining, add gifts only while stock lasts and warn me at the top of the report.
```

## Part 3: check progress or wrap up

```
Using the ShipBob MCP, give me the status of my gift-with-purchase promotion: hero SKU WATCH-CLASSIC-40, gift SKU GIFT-CLEANKIT-HOL, started {Nov 26, 2026 00:00} {your time zone}, limit 1,000.

One line: gifts given, gifts remaining, gift stock left. Then a table of gifts given per day. If the limit is reached, remind me to turn off the routine.
```

## What you get

- A readiness check before the first gift goes out: enough gift stock, and how long 1,000 orders should take.
- A preview of every order before it changes, in part 1.
- A running total in every report, so you always know how many gifts are left. The promotion stops itself at 1,000.

## Good to know

- **Timing matters.** A gift can only be added before the warehouse starts picking the order. Orders picked between runs are skipped and don't count toward the 1,000, so run the routine often during peak.
- **Your store listing doesn't change.** Customers see the watch they ordered. The gift is a surprise in the box, and the order total doesn't change.
- **Updating items replaces the whole list,** so the assistant reads each order's current items first and keeps them all.
- **Orders that contain a bundle** may need the gift added a different way. The assistant flags them instead of changing them.
- **Counting:** if a customer buys the cleaning kit themselves alongside the watch, that order counts toward the 1,000. For most promotions this is close enough. Tell the assistant if you need it to be stricter.
- **The routine changes orders without asking each time,** within the exact rule you approved. If your assistant still asks for confirmation, it lists the orders and waits for your "yes".

## Make it yours

- Gift only bigger orders: "containing WATCH-CLASSIC-40 and at least 2 units in total".
- Give different gifts in different weeks: run two promotions with different start dates and limits.
- Follow the gifted orders with [Order Watchlist](../reports/order-watchlist.md).
