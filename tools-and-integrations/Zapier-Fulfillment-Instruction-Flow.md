# Zapier Flow Map: Tier-Based Fulfillment Email

```mermaid
graph TD
    A[Shopify: New Order Created] --> B{Check if order contains subscription tag}
    B -- No --> C[Exit - No email sent]
    B -- Yes --> D[Formatter: Extract Tier from Order Tag]
    D --> E{Which tier?}
    E -- Tier: Mini --> F[Email by Zapier: Mini Instructions Template]
    E -- Tier: Essentials --> G[Email by Zapier: Essentials Instructions Template]
    E -- Tier: Deluxe --> H[Email by Zapier: Deluxe Instructions Template]
    F & G & H --> I[Warehouse receives email with packing instructions]
```

## 🧩 Component Summary

| Step | Tool | Description |
|------|------|-------------|
| A | Shopify (Trigger) | Order created webhook |
| B | Filter (Zapier) | Check for tag: Tier: Mini, Essentials, or Deluxe |
| D | Formatter (Zapier) | Parse tag to identify tier |
| F/G/H | Email by Zapier (or Gmail/SendGrid) | Send customized instructions |
| I | N/A | Email lands in warehouse@lunaluxenaturals.com inbox |
