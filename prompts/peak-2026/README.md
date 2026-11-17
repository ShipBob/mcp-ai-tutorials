# Peak 2026 Prompt Pack

Eleven prompts to get your ShipBob operation through Thanksgiving (Nov 26), Black Friday (Nov 27) and Cyber Monday (Nov 30), in the order we walk through them in the webinar. Paste any of them into Claude, ChatGPT, or Bobby once your assistant is connected to the ShipBob MCP.

Not connected yet? [Connect Claude Desktop](../../00_getting_started/01_connect_claude_desktop.md) or [connect ChatGPT](../../00_getting_started/03_connect_chatgpt.md) first. It takes about two minutes.

## 1. Your BFCM war room fits in one chat window

Start every peak day with one screen that tells you what needs action.

| Prompt | What you get | Changes data? |
|---|---|---|
| [Peak War Room](../reports/peak-war-room.md) | Orders in, shipped, stuck, low stock and inbound, with a ranked to-do list | No |
| [On-Time Ship Scorecard](../reports/on-time-ship-scorecard.md) | On-time ship % by day, fulfillment center and channel | No |
| [Cost and Zone Map](../reports/cost-and-zone-map.md) | Where your orders go, what each zone costs, and where inventory should sit | No |
| [Tracking Upload Status](../reports/tracking-upload-status.md) | Carrier scan delays vs tracking that never reached your store | No |
| [Order Watchlist](../reports/order-watchlist.md) | A traffic-light view of the orders you care about most | No |

Then act on what the war room shows you:

| Prompt | What it does | Changes data? |
|---|---|---|
| [Resolve Stuck Orders](../actions/resolve-stuck-orders.md) | Groups held and exception orders by fix, then fixes the groups you approve | Yes, after you confirm |
| [Re-route Expensive Orders](../actions/reroute-expensive-orders.md) | Moves far-zone orders to a closer fulfillment center that has the stock | Yes, after you confirm |

## 2. Agents that work the BFCM night shift

Don't lose Saturday morning to a backlog nobody saw on Friday night.

| Prompt | What it does | Changes data? |
|---|---|---|
| [Night Shift Watch](../automations/night-shift-watch.md) | A report every morning, holidays included, covering only what changed overnight | No |

## 3. Will you run out before Cyber Monday?

| Prompt | What it does | Changes data? |
|---|---|---|
| [Stock Runway Before Cyber Monday](../inventory/stock-runway-before-cyber-monday.md) | Days of stock left per SKU against Nov 30 and Dec 15, plus an optional substitute swap | Optional, after you confirm |

## 4. Gift season, automated

| Prompt | What it does | Changes data? |
|---|---|---|
| [Gift With Purchase: First 1,000 Orders](../gifting/gift-with-purchase.md) | Customers buy product A as usual; the first 1,000 orders also get a free holiday gift | Yes, after you confirm |
| [Mystery Box Bundle](../gifting/mystery-box-bundle.md) | A new mystery box SKU on your website becomes a ShipBob bundle of SKU A + SKU B, automatically | Yes, after you confirm |

## Before you start

- **Swap in your time zone and placeholders.** Anything in braces, like `{hero SKU}`, needs your value.
- **Nothing changes without your "yes".** Every prompt that changes data shows you the exact list first and waits. The two gifting routines are the one exception: they act on their own, but only within the exact rule you approve when you set them up.
- **Try one prompt on a quiet morning first**, so you know what "normal" looks like before peak volume arrives.

Looking for inbound and receiving prompts? See [Inbound and WRO](../../01_inbound_and_wro/) and the daily inbound report in [Automated Reporting](../../02_automated_reporting/).
