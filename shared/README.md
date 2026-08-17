# Shared Assets

Files referenced by more than one tutorial live here instead of being duplicated.

Currently tracked:

- `screenshots/`: screenshots referenced from tutorial docs. Add new screenshots here and link to them with a relative path, e.g. `![Connectors settings](../shared/screenshots/connectors-active.png)`. GitHub strips inline CSS from rendered markdown, so borders are baked into the image itself rather than styled: `magick input.png -bordercolor "#D0D7DE" -border 6 output.png`.
- `sample-packing-slip.pdf`: a fictional manufacturer's packing slip ("Your Manufacturer Inc.") linked from [`01_inbound_and_wro/01_creating_a_wro.md`](../01_inbound_and_wro/01_creating_a_wro.md), so readers can practice the by-packing-slip method without a real one on hand.
