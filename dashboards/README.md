# 📊 Dashboards & Reporting – Luna Luxe Subscription Workflow

This folder contains data visualization and performance tracking artifacts designed to support the Luna Luxe Naturals Shopify automation case study. It showcases the use of dashboards and reporting to monitor fulfillment operations, manage SLA compliance, and surface escalation trends.

---

## 🧩 Contents

| File Name                                      | Description |
|-----------------------------------------------|-------------|
| `Fulfillment-Escalation-Dashboard-Mockup.md`  | Mermaid diagram of the dashboard layout and widget structure |
| `PowerBI-DataModel-Subscription-Fulfillment.txt` | Blueprint for implementing the dashboard in Power BI, including tables, measures, and visuals |
| `LunaLuxe_PowerBI_Data.zip`                   | Simulated CSV data (`Orders.csv`, `EscalationLogs.csv`) for testing Power BI dashboards |
| `README.md`                                   | Overview of this folder and its contents |

---

## 📊 Dashboard Metrics & KPIs

The Power BI dashboard model includes:

- Total subscription orders
- Fulfillment SLA tracking (<48 hrs)
- Escalated orders (>48 hrs)
- At-risk orders (>72 hrs)
- Average fulfillment and response times
- Escalation trend analysis
- Log of latest escalated orders

---

## 📁 Data Sources

| Table            | Source                   |
|------------------|---------------------------|
| `Orders.csv`     | Simulated Shopify orders |
| `EscalationLogs.csv` | Simulated Zapier-based escalation alerts |

These CSVs are zipped in `LunaLuxe_PowerBI_Data.zip` for easy import into Power BI Desktop.

---

## 🛠 How to Use

1. Unzip the data files locally
2. Load `Orders.csv` and `EscalationLogs.csv` into Power BI
3. Create relationships on `OrderID`
4. Add DAX measures (see blueprint file)
5. Design dashboard visuals using the mockup as a guide

---

## 📌 About This Portfolio

This dashboard is part of a larger business analyst portfolio project focused on Shopify automation and operations optimization for small ecommerce brands. It demonstrates experience in:

- KPI definition
- Escalation logic
- Report building in Power BI
- Workflow translation into visual insights

