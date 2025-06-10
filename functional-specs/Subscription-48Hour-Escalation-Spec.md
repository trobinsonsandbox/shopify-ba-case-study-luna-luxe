from pathlib import Path

# Define the content of the 48-hour escalation functional spec
spec_content = """Functional Specification: 48-Hour Escalation for Unfulfilled Subscription Orders

Story Reference:  
User Story 003 – 48-Hour Escalation

---

Objective

Identify subscription orders that have not been fulfilled within 48 hours of placement and escalate them to the customer support team for follow-up. This ensures timely communication with customers and helps reduce refund requests or negative reviews.

---

Context

Luna Luxe Naturals offers subscription products that customers expect to be fulfilled within 48 hours. Currently, there is no automated way to monitor unfulfilled orders. Support staff rely on manual checks, which leads to missed delays.

This feature will proactively flag orders that are older than 48 hours and still unfulfilled, and send a notification to the support team.

---

Trigger

Scheduled Automation Trigger:  
Runs every 6 hours (or daily) via Zapier or Make.com

---

Conditions

1. Order was created more than 48 hours ago
2. Order status is still "Unfulfilled"
3. Order contains a tag:
   - Tier: Mini, Tier: Essentials, or Tier: Deluxe (i.e., a subscription order)

---

Actions

1. Generate alert message with:
   - Order ID
   - Customer name
   - Time since order was placed
   - Subscription tier (if available)
   - Order creation timestamp
2. Send alert to:
   - support@lunaluxenaturals.com
   - Optional: Slack channel or dashboard flag

---

Example Email Alert

Subject: ⚠️ Escalation Alert: Subscription Order Unfulfilled After 48 Hours

Body:
Order #11092 has not been fulfilled within 48 hours.

Customer: Olivia Fernandez  
Tier: Essentials  
Created: 2025-06-10 2:14 PM  
Time Elapsed: 52.5 hours

Please contact fulfillment or follow up with the customer directly.

---

Tools & Automation Flow

Tool      | Purpose
----------|------------------------------------------------
Shopify   | Source of order data + tags
Zapier    | Scheduled polling (Search Orders + Filter)
Email/Slack | Send escalation notification
Google Sheets (Optional) | Track escalated orders

---

Flow Logic (Pseudocode)

Trigger: Every 6 hours

Search: Orders where:
  - Fulfillment status = "Unfulfilled"
  - Order age > 48 hours
  - Order tag includes any "Tier:" tag

For each matching order:
  → Send email/slack message to support
  → (Optional) Log to spreadsheet for reporting

---

Assumptions

- Shopify tags are consistently applied by earlier automations
- Time of order creation is accurate and accessible
- Fulfillment status is not manually overridden incorrectly
- Support team checks email or Slack regularly

---

Risks / Considerations

- High order volume may generate false positives if fulfillment is delayed by design
- Notification fatigue if too many alerts are generated
- Manual exceptions may need to be added to suppress alerts for known delayed orders
- Shopify Flow cannot handle time-based logic natively — needs Zapier, Make.com, or custom app

---

Acceptance Criteria

- [ ] Orders unfulfilled after 48 hours are flagged automatically
- [ ] Notifications include correct order and customer info
- [ ] Alerts are sent to designated support contact(s)
- [ ] Only subscription orders are included
- [ ] System can be tested in sandbox with delayed orders
"""

# Define the path for the output file
output_file = Path("/mnt/data/Subscription_48Hour_Escalation_Spec.txt")

# Write the content to the file
output_file.write_text(spec_content)

# Return the file name for download
output_file.name
