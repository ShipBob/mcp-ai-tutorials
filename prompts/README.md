# Prompt Library

Copy-paste prompts for running your ShipBob business with an AI assistant connected to the ShipBob MCP. Each prompt has its own page: when to use it, the prompt itself, what you get back, and how to adjust it.

New here? Connect first: [Claude Desktop](../00_getting_started/01_connect_claude_desktop.md) or [ChatGPT](../00_getting_started/03_connect_chatgpt.md).

**Getting ready for Black Friday and Cyber Monday?** Start with the [Peak 2026 collection](peak-2026/).

## Reports

| Prompt | Answers | Changes data? |
|---|---|---|
| [Peak War Room](reports/peak-war-room.md) | What needs my attention this morning? | No |
| [On-Time Ship Scorecard](reports/on-time-ship-scorecard.md) | Are we shipping on time, and where are we slipping? | No |
| [Cost and Zone Map](reports/cost-and-zone-map.md) | Where do my orders go, and what does each zone cost me? | No |
| [Tracking Upload Status](reports/tracking-upload-status.md) | Has every shipped order's tracking reached my store? | No |
| [Order Watchlist](reports/order-watchlist.md) | Where are the orders I care most about right now? | No |

## Actions

| Prompt | Does | Changes data? |
|---|---|---|
| [Resolve Stuck Orders](actions/resolve-stuck-orders.md) | Sorts held and exception orders by fix, then fixes the ones you approve | Yes, after you confirm |
| [Re-route Expensive Orders](actions/reroute-expensive-orders.md) | Moves far-zone orders to a closer fulfillment center that has the stock | Yes, after you confirm |

## Inventory

| Prompt | Answers | Changes data? |
|---|---|---|
| [Stock Runway Before Cyber Monday](inventory/stock-runway-before-cyber-monday.md) | Which SKUs run out before Nov 30, and what do I swap in? | Optional swap, after you confirm |

## Gifting

| Prompt | Does | Changes data? |
|---|---|---|
| [Gift With Purchase: First 1,000 Orders](gifting/gift-with-purchase.md) | Adds a free holiday gift to the first 1,000 orders of a hero product, then stops | Yes, after you confirm |
| [Mystery Box Bundle](gifting/mystery-box-bundle.md) | Turns a new SKU from your website into a ShipBob bundle of items you already stock | Yes, after you confirm |

## Automations

| Prompt | Does | Changes data? |
|---|---|---|
| [Night Shift Watch](automations/night-shift-watch.md) | Checks your operation overnight and over the holiday weekend | No |

## How these prompts are written

A few rules run through every prompt here. Borrow them when you write your own.

- **Say the time zone.** "Yesterday" means different things in New York and Los Angeles. Every prompt names one; swap in yours.
- **Ask for "n/a", never guesses.** Each prompt tells the assistant to mark missing data as unavailable instead of estimating it.
- **Lead with exceptions.** Reports open with what needs action, then the healthy numbers.
- **Look before you change.** Any prompt that changes orders, products, or holds shows you the exact list first and waits for your "yes". Nothing changes until you confirm. Routines that keep a promotion running act on their own, but only within the exact rule you approve when you set them up.
- **Placeholders are in braces.** Replace anything like `{hero SKU}` or `{your time zone}` before you send.

## Works in

These prompts are written for any assistant connected to the ShipBob MCP: Claude (Desktop, web, or Claude Code), ChatGPT, and Bobby inside the ShipBob dashboard. Prompts that ask for an **interactive artifact** produce a visual dashboard in Claude; in other assistants you get the same content as a formatted report.
