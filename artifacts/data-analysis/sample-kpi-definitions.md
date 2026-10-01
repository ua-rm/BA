# Sample KPI Definitions Catalog

Clear, agreed definitions prevent misalignment between business, analytics, and leadership.

---

## Retention & Churn

| KPI | Definition | Formula / Logic | Cadence | Owner |
|-----|------------|-----------------|---------|-------|
| Monthly Churn Rate | Percentage of customers who cancel in the month relative to active customers at the start of the month | (Cancellations in month) / (Active customers at month start) x 100 | Monthly | Retention Lead |
| Gross Retention | Revenue retained from existing customers (excluding expansion) | (Starting ARR - Churned ARR - Contraction) / Starting ARR | Monthly | Finance + CS |
| Net Revenue Retention | Includes expansion | (Starting ARR + Expansion - Churn - Contraction) / Starting ARR | Monthly | Finance |
| 90-Day Retention | % of a signup cohort still active 90 days later | Active on day 90 / Cohort size | Weekly snapshot | Growth |

---

## Engagement

| KPI | Definition | Formula / Logic | Cadence | Owner |
|-----|------------|-----------------|---------|-------|
| DAU / MAU | Stickiness ratio | Daily Active Users / Monthly Active Users | Daily | Product |
| Activation Rate | % of new users reaching a defined aha moment within time window | Activated users / New signups (in window) | Daily | Growth / Product |
| Feature Adoption | % of active users who used a specific feature in period | Users with >=1 event of feature / Active users | Weekly | Product |

---

## Support & Experience

| KPI | Definition | Formula / Logic | Cadence | Owner |
|-----|------------|-----------------|---------|-------|
| First Response Time | Median time from ticket creation to first agent response | Median(first_response_timestamp - created_timestamp) | Daily | Support |
| CSAT | Average customer satisfaction score on closed tickets | Average of survey scores (1-5 or 1-10) | Weekly | Support |
| Ticket Reopen Rate | % of closed tickets reopened within 7 days | Reopened tickets / Closed tickets | Weekly | Support |

---

## Notes for Analysts
- Always document the exact filters (e.g., exclude test accounts, internal users, free trials if appropriate).
- Align on timezone and as-of timing for point-in-time metrics.
- Version the definitions when logic changes and communicate the change.
