# Mystery Box Bundle

**Use it when:** you launch a new holiday product on your website, like a mystery box or gift set, made of items you already stock. ShipBob turns the new SKU into a bundle, so every order for the box ships its contents. No new inventory needed.

**Works in:** Claude, ChatGPT, Bobby. Part 2 uses Claude Desktop Routines.

**Changes data?** Yes. It converts the new product into a bundle, but only after you confirm (or, in part 2, only within the exact rule you approve).

## The example

Watches Inc launches a Holiday Mystery Box for $79. Inside: a leather strap and a travel pouch, two items they already stock at ShipBob.

| | SKU | Name |
|---|---|---|
| New product on the website | `HOLIDAY-MYSTERY-BOX-26` | Holiday Mystery Box 2026 |
| SKU A | `STRAP-LEATHER-BRN-20` | Leather Strap, Brown, 20mm |
| SKU B | `POUCH-TRAVEL-WATCH` | Watch Travel Pouch |

Replace these with your own SKUs. SKU A and SKU B need to be products in ShipBob with stock.

## How it works

1. **On your store:** create the new listing with SKU `HOLIDAY-MYSTERY-BOX-26`. ShipBob can't create listings on Shopify, Amazon or other platforms. You create the listing; ShipBob handles everything after the order arrives.
2. **ShipBob picks it up:** once your store syncs to ShipBob, a new product with that SKU appears in ShipBob, with no stock of its own.
3. **The assistant converts it into a bundle** of 1 `STRAP-LEATHER-BRN-20` + 1 `POUCH-TRAVEL-WATCH`. From then on, every order for the mystery box ships both items.

Order matters here: any box orders that arrive before step 3 have nothing to pick and land in exception. Convert the bundle before you announce the box, and use part 2 so it happens on its own.

## Part 1: set up the bundle now

```
Using the ShipBob MCP, set up my mystery box as a bundle.

New product SKU: HOLIDAY-MYSTERY-BOX-26
Bundle contents: STRAP-LEATHER-BRN-20 x 1, POUCH-TRAVEL-WATCH x 1

Step 1. Find the product with SKU HOLIDAY-MYSTERY-BOX-26 in ShipBob. If it isn't there yet, tell me it hasn't synced from my store and stop.

Step 2. Check it is safe to convert: it is not already a bundle, and it has no stock of its own. If either check fails, explain and stop.

Step 3. Check the contents: confirm both SKUs exist, show the fulfillable stock of each, and tell me how many complete mystery boxes I can ship with today's stock.

Step 4. Show me the plan: product to convert, contents and quantities, boxes I can ship. Stop and wait for my "yes".

Step 5. Convert HOLIDAY-MYSTERY-BOX-26 into a bundle with those contents, then read it back and confirm the bundle contents.

Step 6. Check for shipments containing HOLIDAY-MYSTERY-BOX-26 that are in exception, and list them so I know whether any orders arrived before the bundle existed.
```

## Part 2: create the bundle automatically

Set this up before you publish the listing. The routine watches for the new SKU and converts it as soon as it arrives in ShipBob, so you don't have to time it. In Claude Desktop, go to **Routines** and paste:

```
Set up a routine that runs every {15 minutes} until I turn it off.

Each run, using the ShipBob MCP, look for these new products and turn them into bundles:

| New SKU | Contents |
|---|---|
| HOLIDAY-MYSTERY-BOX-26 | STRAP-LEATHER-BRN-20 x 1, POUCH-TRAVEL-WATCH x 1 |

For each row:
1. If the new SKU does not exist in ShipBob yet, do nothing.
2. If it exists, is not already a bundle, and has no stock of its own, I approve converting it into a bundle with exactly the contents in the table, without asking me each time. Change nothing else.
3. If it is already a bundle, check that its contents match the table. If they don't, warn me and do not change it.

Report only when something happens: a bundle was created, a bundle doesn't match, or shipments containing the new SKU are in exception. Include how many complete boxes current stock of the contents can ship.
```

## Part 3: how many boxes can I still ship?

```
Using the ShipBob MCP, check my mystery box bundle HOLIDAY-MYSTERY-BOX-26.

1. Confirm it is a bundle and list its contents.
2. For each item inside, show fulfillable stock.
3. Tell me how many complete boxes I can still ship and which item runs out first.
4. Count mystery box orders over the last 7 days, and at that pace, estimate the day I run out.
```

## What you get

- A bundle in ShipBob, created the moment your new listing arrives, with no manual timing.
- A clear count of how many boxes your current stock can ship, and which item will run out first.
- An early warning if any box orders arrived before the bundle was ready.

## Good to know

- **Stock syncs back to your store.** A bundle's available stock is limited by its scarcest item, so your store may show the box as sold out when either item runs out. Watch part 3 during peak.
- **Only convert new, empty products.** The prompts refuse to convert a product that already has its own stock, so your existing products stay untouched.
- **More than one box?** Add a row per box to the table in part 2, for example a small and a large box with different contents.
- **The routine converts without asking each time,** within the exact table you approved. If your assistant still asks for confirmation, it shows the plan and waits for your "yes".

## Make it yours

- Make it a real mystery: pick the contents with [Stock Runway Before Cyber Monday](../inventory/stock-runway-before-cyber-monday.md), choosing items with plenty of stock so the box helps clear slower sellers.
- Ship the box to creators too: once the bundle exists, ask the assistant to create gifting orders using `HOLIDAY-MYSTERY-BOX-26` for a list of recipients, with a preview before anything is created.
