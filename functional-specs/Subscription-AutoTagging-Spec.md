# Functional Specification: Auto-Tag Orders Based on Subscription Tier

**Story Reference:**  
[User Story 001 – Auto-Tag Subscription Tier](../epics-and-user-stories/User-Story-001-Auto-Tag-Subscription-Tier.md)

---

## Objective

Automate the tagging of incoming orders based on the subscription product tier (Mini, Essentials, Deluxe) to improve fulfillment accuracy, enable tier-specific workflows, and reduce manual sorting by staff.

---

## Context

Luna Luxe Naturals offers tiered monthly skincare subscriptions. Each tier requires a different fulfillment workflow. Currently, staff manually identify the tier of each order based on product selection. Automating the tagging of orders based on subscription tier enables faster, more accurate processing and supports downstream workflows like onboarding emails, reporting, and escalations.

---

## Business Logic Summary

| Product Tier | Product Tags/Keywords      | Resulting Order Tag |
|--------------|----------------------------|----------------------|
| Mini         | `subscription-mini`        | `Tier: Mini`         |
| Essentials   | `subscription-essentials`  | `Tier: Essentials`   |
| Deluxe       | `subscription-deluxe`      | `Tier: Deluxe`       |

> Note: Products are tagged in Shopify using product tags. This logic depends on consistent use of these tags across subscription items.

---

## Trigger

**Shopify Flow Trigger**:  
`Order Created`

---

## Conditions

1. Loop through all line items in the order
2. If **any** line item has a product tag matching a known subscription tier:
   - Apply the corresponding order tag:
     - “Tier: Mini”
     - “Tier: Essentials”
     - “Tier: Deluxe”

---

## Actions

1. Add the appropriate **order tag** based on product tier
2. (Optional/future) Trigger downstream workflows via tag (e.g., email flows, packing SOPs, reports)

---

## Tools & Dependencies

| Tool              | Purpose                                                 |
|-------------------|----------------------------------------------------------|
| Shopify Flow      | Trigger on order creation, evaluate line item tags       |
| Shopify Admin     | Define product tags at the item level                    |
| (Optional) Zapier | For extended logic or email triggers beyond Shopify Flow |

---

## Mock Shopify Flow Logic

```plaintext
Trigger: Order Created

For each line item in Order:
    If Product Tag = "subscription-mini":
        Add Order Tag = "Tier: Mini"
    Else if Product Tag = "subscription-essentials":
        Add Order Tag = "Tier: Essentials"
    Else if Product Tag = "subscription-deluxe":
        Add Order Tag = "Tier: Deluxe"
```

🔗 Related Diagram: [Swimlane – Order Fulfillment Tagging](../workflow-diagrams/Swimlane-Order-Fulfillment-Tagging.md)

## Assumptions

1. All subscription products are tagged consistently in Shopify

2. Shopify Flow is enabled and operational

3. Orders may contain both subscription and non-subscription products

4. Only one tier tag is applied per order (based on first matched product)

## Risks / Considerations

1. Inconsistent or missing product tags may lead to incorrect tagging

2. Orders with multiple subscription tiers may need more complex logic

3. Shopify Flow has limited logic branching; advanced flows may require Zapier or a custom app

4. Manual QA may be needed to validate flow after initial deployment

## Acceptance Criteria

1. Orders with tagged subscription products receive the correct tier-based order tag automatically

2. Orders without any subscription products do not receive a tier tag

3. Tag is visible in the Shopify order detail view

4. Only one tier tag is applied per order

5. Logic is documented and testable in sandbox prior to deployment


