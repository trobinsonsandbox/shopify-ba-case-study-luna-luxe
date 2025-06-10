from pathlib import Path

# Define the content for the functional specification
functional_spec_content = """Functional Specification: Tier-Specific Fulfillment Instruction Email

Story Reference:  
User Story 002 – Fulfillment Instruction Emails

---

Objective

Automatically send an internal fulfillment email when a subscription order is placed, with clear instructions based on the product's subscription tier. This reduces manual effort, prevents packing errors, and enables the fulfillment team to act without reviewing each order manually.

---

Context

Luna Luxe Naturals offers three subscription tiers with different packaging requirements:

| Tier       | Packaging Details                                |
|------------|--------------------------------------------------|
| Mini       | Basic padded envelope, no inserts                |
| Essentials | Include “thank you” card, recyclable wrap        |
| Deluxe     | Include promo item + cold pack for serum         |

Instead of relying on the fulfillment team to open and interpret each order, we want to send them a tier-based instruction email immediately after the order is placed.

---

Trigger

Shopify Flow Trigger:  
Order Created

---

Conditions

1. Order must contain a subscription product
2. The order must have a tag matching one of:
   - Tier: Mini
   - Tier: Essentials
   - Tier: Deluxe

---

Actions

1. Generate a templated internal email that includes:
   - Order number
   - Customer name
   - Subscription tier
   - Tier-specific packing instructions
   - Order creation timestamp

2. Send email to: warehouse@lunaluxenaturals.com

Note: Email sending requires external integration (via webhook, Zapier, Klaviyo, or SendGrid API).

---

Example Email Template

Subject: 🧴 New Subscription Order – Tier: Deluxe – Order #{{order_number}}

Body:
Order ID: {{order_number}}
Customer: {{customer_name}}
Tier: Deluxe

📦 Fulfillment Instructions:
- Include bonus promo item
- Pack serum with cold gel insert
- Use branded mailer box

Created: {{order_timestamp}}

---

Tools & Integration Options

| Tool        | Role                                  |
|-------------|----------------------------------------|
| Shopify Flow | Detects order creation + tags         |
| Zapier       | Webhook receiver + Email action       |
| Klaviyo      | Alternate for templated transactional emails |
| SendGrid     | (Optional) API-based email dispatch   |

---

Flow Logic (Pseudocode)

Trigger: Order Created

If Order Tag = Tier: Mini
    → Send Email with Mini packing instructions

If Order Tag = Tier: Essentials
    → Send Email with Essentials instructions

If Order Tag = Tier: Deluxe
    → Send Email with Deluxe instructions

---

Assumptions

- Order tagging from User Story 1 is already in place and reliable
- Subscription tiers are mutually exclusive (only one tag per order)
- Fulfillment team has access to email and follows SOPs based on content
- Warehouse email address is monitored daily

---

Risks / Considerations

- Email delivery failure could delay fulfillment
- Tagging errors may result in incorrect instructions
- Shopify Flow does not send emails directly — external tool must be configured
- Tier instructions may evolve — email templates should be modular or updateable

---

Acceptance Criteria

- [ ] Orders with a subscription tier tag trigger an internal email to the warehouse
- [ ] Email contains the correct tier-specific instructions
- [ ] Emails are sent only for tagged (subscription) orders
- [ ] Email template is clear, actionable, and includes order metadata
- [ ] System is testable in a staging or sandbox environment before production use
"""

# Define the output file path
output_path = Path("/mnt/data/Fulfillment_Instruction_Email_Spec.txt")

# Write the content to the file
output_path.write_text(functional_spec_content)

# Return the file path for download
output_path.name
