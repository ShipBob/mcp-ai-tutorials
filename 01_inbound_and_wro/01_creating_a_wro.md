# Creating and Managing your Inbound / WRO

**What you'll learn**

Two ways to create a warehouse receiving order (WRO) in ShipBob: by describing the shipment in a prompt, or by attaching a manufacturer's packing slip (a PDF) and letting Claude read it.

**Prerequisites**

- [Connect Claude Desktop](../00_getting_started/01_connect_claude_desktop.md) completed
- For the packing slip method: a packing slip PDF from your manufacturer, or use the [sample packing slip](../shared/sample-packing-slip.pdf) to practice with

**The prompt**

**Way 1: By prompt**

Tell Claude the shipment details directly:

```
Create a warehouse receiving order (WRO) at the Moreno Valley Hub, with an estimated delivery date of August 30, 2026. PO is PO-2026-08-20-1. Include:

- 100 units of SKU SWAG-SHIRT-BLACK (Swag Shirt - Black)
- 120 units of SKU SWAG-SHIRT-GREEN (Swag Shirt - Green)
- 140 units of SKU HOODIE-BLACK (Premium Hoodie - Black)

All items are single SKU only and pack type is pallets.
```

**Way 2: By packing slip**

1. Start a new chat in Claude Desktop.
2. Attach the packing slip PDF to your message (no manufacturer PDF on hand? Use this [sample packing slip](../shared/sample-packing-slip.pdf)).
3. Ask:

```
Create a warehouse receiving order (WRO) from this packing slip. Match the SKUs to my existing products where you can, and flag anything you can't match.
```

**What to expect**

Either way, Claude extracts the SKUs and quantities and either creates the WRO directly or shows you a summary to confirm before creating it. Anything it can't confidently match to an existing product gets flagged for you to resolve manually.

**Try it yourself**

Try a prompt or a packing slip with a SKU that doesn't exist in your catalog yet, and see how Claude flags it instead of guessing.
