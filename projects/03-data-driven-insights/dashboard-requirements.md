# Dashboard Requirements
## Customer Retention & Churn Monitoring

**Purpose**: Provide leadership and operational teams with an always-on view of churn health, leading indicators, and the impact of retention initiatives.

**Primary Users**: Head of Retention, Customer Success Managers, Product Managers, Executive sponsors

---

## 1. Dashboard Pages / Views

### View A - Executive Overview
- Overall churn rate (monthly & trailing 3-month)
- Trend vs. target
- New vs. existing customer churn split
- Top 3 risk segments by volume and rate
- High-level impact of active retention programs (if measurable)

### View B - Leading Indicators
- % of customers with sharp engagement drop (last 30 days)
- % of new customers missing activation milestones
- Support ticket volume & unresolved rate among at-risk cohorts
- Early warning list size and coverage

### View C - Segment Deep Dive
- Churn rate by acquisition channel, plan, region, tenure band
- Cohort retention curves (selectable cohorts)
- Ability to filter and export segment lists for action

### View D - Initiative Tracker (optional phase 2)
- Active experiments / plays
- Target vs. actual retention lift
- Status and owner

---

## 2. Key Metrics & Definitions

| Metric | Definition | Refresh |
|--------|------------|---------|
| Monthly Churn Rate | Customers who canceled in month / Customers active at start of month | Daily |
| 90-Day Retention | % of cohort still active 90 days after signup | Daily |
| Activation Rate | % of new customers reaching defined activation criteria within 14/30 days | Daily |
| Engagement Drop Rate | % of active customers with >50% drop in key events MoM | Daily |
| At-Risk Coverage | % of eventual churners who appeared on risk list >=14 days prior | Weekly |

---

## 3. Filters & Interactivity

- Date range
- Customer tenure band
- Plan / tier
- Acquisition channel
- Region
- At-risk flag (Yes/No)

---

## 4. Non-Functional Requirements

- Data latency: <= 24 hours for core metrics; near real-time preferred for risk lists
- Access control: Role-based (Executives see aggregate; CSMs see their book of business)
- Export: CSV of filtered customer lists for outreach
- Mobile-friendly summary view for executives

---

## 5. Open Questions for Data / BI Team
- Exact definition and source of activation events
- Historical depth available for cohort analysis
- Preferred BI tool and existing semantic layer
