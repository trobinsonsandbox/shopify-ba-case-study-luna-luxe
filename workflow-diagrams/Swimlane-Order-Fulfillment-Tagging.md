# Swimlane Diagram: Order Fulfillment Tagging Workflow

```mermaid
%% Mermaid does not support classic swimlanes directly,
%% but this vertical layout approximates role-based flow.

%% Roles: Customer, Shopify Flow, Fulfillment Team

sequenceDiagram
    participant Customer
    participant ShopifyFlow
    participant FulfillmentTeam

    Customer->>ShopifyFlow: Places Order
    ShopifyFlow->>ShopifyFlow: Check line items for subscription tags
    alt No subscription product
        ShopifyFlow-->>ShopifyFlow: Do nothing
    else Subscription product found
        ShopifyFlow->>ShopifyFlow: Determine product tier
        ShopifyFlow->>ShopifyFlow: Apply tier tag to order
        ShopifyFlow-->>FulfillmentTeam: Order appears in dashboard with tag
    end
