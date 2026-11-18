# On-Time Ship Scorecard

**Use it when:** you want to know whether orders are leaving the warehouse on time, and where they are slipping, before volume spikes.

**Works in:** Claude (as an interactive artifact), ChatGPT, Bobby

**Changes data?** No. Read-only.

**The prompt**

```
Using the ShipBob MCP, build an on-time ship scorecard for the last 30 days as an interactive artifact. Time zone: {your time zone}.

1. Headline: on-time ship % for the last 30 days, and for the last 7 days next to it, so I can see the direction.
2. A daily line chart of on-time ship % for the last 30 days.
3. A table by fulfillment center: shipments, on-time %, late shipments. Worst on-time % first.
4. A table by sales channel with the same columns.
5. The 3 days with the lowest on-time %, with the shipment count for each, so I can see whether low days were high-volume days.

Finish with two sentences: where on-time performance is weakest, and one thing to check before Black Friday.

Rules: use only ShipBob MCP data. If on-time status is unavailable for a slice, mark it "n/a" instead of estimating.
```

**What you get**

A scorecard with the 30-day and 7-day on-time rates side by side, a daily trend line, and breakdowns by fulfillment center and channel. The two-sentence summary points at the weakest spot.

See an example: [sample report (PDF)](samples/on-time-ship-scorecard-sample.pdf), made with fictional data for Watches Inc.

**Make it yours**

- Change the window to "since November 1" to watch peak as it happens.
- Ask for a weekly version and pin it as your baseline, then compare against it during Black Friday week.
- In Bobby or ChatGPT, ask for "the same scorecard as a table" if you don't need the chart.
