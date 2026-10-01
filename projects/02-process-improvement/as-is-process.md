# As-Is Order Fulfillment Process

## Process Overview

**Trigger**: Order successfully paid in e-commerce system  
**End**: Order marked as Shipped and tracking sent to customer  
**Primary Actors**: Customer Service, Warehouse Operations, Inventory Control, Shipping Coordinator

---

## High-Level Current Flow

```
1. Order arrives in OMS (Order Management System)
2. Customer Service manually reviews high-value or flagged orders
3. Inventory Control checks stock (often via spreadsheet + WMS)
4. If stock available -> Warehouse picks & packs
5. If stock issue -> Manual email / Slack escalation
6. Shipping Coordinator books carrier & generates label
7. Tracking number manually entered back into OMS
8. Customer receives confirmation (sometimes delayed)
```

---

## Detailed Swimlane (Text Representation)

| Step | Customer Service | Inventory Control | Warehouse | Shipping Coordinator |
|------|------------------|-------------------|-----------|----------------------|
| 1. Order received | Reviews flagged orders | - | - | - |
| 2. Stock check | - | Checks WMS + spreadsheet | - | - |
| 3. Allocation | - | Reserves stock (manual) | - | - |
| 4. Pick list | - | - | Receives paper / system pick list | - |
| 5. Pick & Pack | - | - | Executes pick & pack | - |
| 6. Exception | Receives escalation email | Investigates | Holds order | - |
| 7. Ship | - | - | Stages packed order | Books carrier, prints label |
| 8. Update system | - | - | - | Manually updates OMS with tracking |
| 9. Notify customer | May send manual update | - | - | - |

---

## Identified Pain Points

| ID | Pain Point | Impact | Frequency |
|----|------------|--------|-----------|
| PP-01 | Manual stock verification across systems | Delays, errors | Daily |
| PP-02 | Email/Slack-based exception handling | Lost requests, slow resolution | Multiple times/day |
| PP-03 | Manual tracking number entry | Data entry errors, delayed customer notification | Every order |
| PP-04 | No real-time visibility of order status | High volume of where is my order tickets | Ongoing |
| PP-05 | Inconsistent prioritization of orders | VIP / expedited orders sometimes delayed | Weekly |
| PP-06 | Paper-based or fragmented pick lists | Inefficient warehouse movement | Daily |

---

## Metrics (Current State)

| Metric | Current Value | Notes |
|--------|---------------|-------|
| Avg. Order-to-Ship time | 38 hours | Target desired: < 24 hours |
| % Orders with exceptions | 18% | Mostly stock or address issues |
| Manual touches per order | 4-6 | High cost of coordination |
| Customer Where is my order tickets | ~220 / week | Significant support load |
