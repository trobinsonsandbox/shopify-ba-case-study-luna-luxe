# Flowchart: Fulfillment Instruction Email Workflow

```mermaid
flowchart TD
    A[Order Created] --> B{Does order contain a subscription product?}
    B -- No --> C[Do nothing]
    B -- Yes --> D{Which subscription tier?}

    D -- Mini --> E[Apply Tag: Tier Mini]
    D -- Essentials --> F[Apply Tag: Tier Essentials]
    D -- Deluxe --> G[Apply Tag: Tier Deluxe]

    E --> H[Trigger email: Mini packing instructions]
    F --> I[Trigger email: Essentials packing instructions]
    G --> J[Trigger email: Deluxe packing instructions]

    H & I & J --> K[Send email to warehouse@lunaluxenaturals.com]
