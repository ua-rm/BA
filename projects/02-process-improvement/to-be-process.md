# To-Be Order Fulfillment Process & Recommendations

## Design Principles
1. Minimize manual handoffs and data re-entry
2. Make status visible to all actors in near real-time
3. Automate the happy path; design clear exception paths
4. Preserve human judgment only where it adds value

---

## Proposed High-Level To-Be Flow

```
1. Order paid -> automatically flows into WMS with allocation
2. System performs stock check & soft allocation
3. If available -> pick list generated & prioritized automatically
4. Warehouse executes guided pick/pack (scan-based)
5. On pack complete -> shipping label auto-generated via carrier integration
6. Tracking number written back to OMS automatically
7. Customer notified in near real-time
8. Exceptions routed to a single queue with SLA and ownership
```

---

## Key Process Changes

| Area | As-Is | To-Be | Benefit |
|------|-------|-------|---------|
| Stock check & allocation | Manual + spreadsheet | Automated in WMS/OMS integration | Speed + accuracy |
| Exception handling | Email / Slack | Centralized exception queue with status | Visibility + accountability |
| Tracking update | Manual entry | System-to-system integration | Eliminate errors & delay |
| Prioritization | Ad-hoc | Rules-based (SLA, VIP, ship-by date) | Consistency |
| Customer communication | Reactive / manual | Event-driven automated notifications | Lower support volume |

---

## Recommended RACI (Future State)

| Activity | Inventory | Warehouse | Shipping | Customer Service | System |
|----------|-----------|-----------|----------|------------------|--------|
| Soft allocation | C | I | I | I | R/A |
| Pick & Pack execution | I | R/A | I | I | C |
| Exception resolution | C | C | C | R | A (routing) |
| Carrier booking & label | I | C | R | I | A |
| Tracking sync & notify | I | I | C | I | R/A |

---

## Prioritized Recommendations

### Quick Wins (0-3 months)
1. **Implement automated tracking write-back** from carrier / shipping system to OMS  
   -> Eliminates PP-03, reduces notification delay
2. **Create a single exception queue** (instead of email) with basic SLA  
   -> Addresses PP-02 and improves ownership
3. **Define and publish order prioritization rules**  
   -> Reduces PP-05

### Medium-Term (3-9 months)
4. **Deepen OMS <-> WMS integration** for allocation and status  
   -> Major reduction in PP-01 and cycle time
5. **Introduce scan-based pick confirmation** and guided workflows  
   -> Improves accuracy and enables better metrics
6. **Event-driven customer notifications** (order confirmed, shipped, exception)  
   -> Directly attacks support ticket volume

### Longer-Term
7. Real-time inventory visibility dashboard for CS and Operations
8. Predictive exception detection (address issues, stock risk)

---

## Expected Outcomes

| Metric | Current | Target (9 months) |
|--------|---------|-------------------|
| Avg. Order-to-Ship | 38 hours | <= 24 hours |
| Exception rate | 18% | <= 10% |
| Manual touches per order | 4-6 | <= 2 |
| Where is my order tickets | ~220/week | <= 130/week |
