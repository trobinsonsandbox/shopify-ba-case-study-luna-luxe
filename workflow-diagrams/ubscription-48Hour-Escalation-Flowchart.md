# Flowchart: 48-Hour Escalation for Unfulfilled Subscription Orders

```mermaid
flowchart TD
    A[Scheduled Trigger (Every 6 Hours)] --> B[Search Shopify Orders]
    B --> C{Is order older than 48 hours?}
    C -- No --> G[Skip – Order too recent]
    C -- Yes --> D{Is order unfulfilled?}
    D -- No --> G
    D -- Yes --> E{Has Tier Tag?}
    E -- No --> G
    E -- Yes --> F[Send Escalation Email to Support]
    F --> H[Log to Escalation Tracker (optional)]
```
