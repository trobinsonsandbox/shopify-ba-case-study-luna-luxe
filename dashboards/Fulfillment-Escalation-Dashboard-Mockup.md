# Dashboard Mockup: Fulfillment & Escalation Tracking

```mermaid
graph TD
    A1[📦 Total Subscription Orders This Week] --> ROOT
    A2[✅ Fulfilled < 48 Hrs] --> ROOT
    A3[⚠️ Orders Escalated 48 Plus Hrs Unfulfilled] --> ROOT
    A4[📉 Avg Fulfillment Time Hrs] --> ROOT
    A5[🟠 Response Time to Escalation Hrs] --> ROOT
    A6[🟥 At-Risk Orders > 72 Hrs] --> ROOT
    A7[📊 Escalation Trend – Last 30 Days] --> ROOT
    A8[📋 Last 5 Escalated Orders Log] --> ROOT

    subgraph Dashboard Widgets
        direction LR
        A1
        A2
        A3
        A4
        A5
        A6
        A7
        A8
    end

    ROOT[🎛️ Fulfillment & Escalation Dashboard]
```
