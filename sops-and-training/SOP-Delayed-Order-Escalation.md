from pathlib import Path

# Recreate the SOP content after the code environment was reset
sop_content = """SOP: Responding to 48-Hour Unfulfilled Subscription Order Alerts

Purpose:  
Ensure all unfulfilled subscription orders older than 48 hours are followed up on quickly and professionally, reducing customer dissatisfaction and refund risk.

---

When to Use This SOP

Use this SOP any time an alert is received from the automation system (Zapier, Slack, or email) indicating that a subscription order has gone unfulfilled for more than 48 hours.

Alerts are sent to: support@lunaluxenaturals.com

---

Step-by-Step Instructions

Step 1: Review the Alert

Check the escalation alert details, which include:
- Order ID
- Customer name
- Subscription tier (if provided)
- Order creation time
- Time elapsed since order

Example:
Order #11092 has not been fulfilled within 48 hours.
Customer: Olivia Fernandez
Tier: Essentials
Created: 2025-06-10 2:14 PM
Time Elapsed: 52.5 hours

---

Step 2: Check Fulfillment Status in Shopify

1. Go to the Shopify Admin
2. Search by Order ID
3. Confirm whether the order is still unfulfilled
   - If already fulfilled → No action needed, mark alert as resolved
   - If still unfulfilled → Continue to next step

---

Step 3: Contact the Fulfillment Team

Use the following email template:

Subject: 🚨 Urgent: Order #{{order_number}} Not Fulfilled After 48 Hours

Body:
Hi team,

Order #{{order_number}} for customer {{customer_name}} (Tier: {{tier}}) has not been fulfilled after 48 hours. Please prioritize this order and confirm once it has been shipped.

Thanks,  
Support Team

---

Step 4: (Optional) Contact the Customer

If the fulfillment team does not respond within 24 hours or if the item is urgently needed:

Use this customer-facing message:

Subject: Update on Your Luna Luxe Order

Body:
Hi {{customer_name}},

We’re following up to let you know your subscription order #{{order_number}} is currently delayed. Our team is working to ship it out as quickly as possible and we’ll confirm once it's on the way.

Thank you for your patience and for being a valued customer.

– The Luna Luxe Naturals Team

---

Step 5: Log the Escalation (Optional)

If using Google Sheets or a CRM:

Log the following:
- Order #
- Customer name
- Alert received time
- Resolution action (e.g., “Confirmed fulfilled,” “Followed up with fulfillment,” “Customer notified”)

---

Responsibilities

Role         | Responsibility
-------------|--------------------------------------------------
Virtual Assistant / Support Rep | Act on alerts and initiate communication
Fulfillment Team | Review and ship delayed orders promptly
Store Owner (optional) | Escalate unresolved issues or issue refunds

---

Version History

Version | Date       | Author             | Notes
--------|------------|--------------------|----------------------
1.0     | 2025-06-09 | Tabiatha Robinson  | Initial draft
"""

# Define the file path
output_path = Path("/mnt/data/SOP_Delayed_Order_Escalation.txt")

# Write the SOP content to the file
output_path.write_text(sop_content)

# Return the file name
output_path.name
