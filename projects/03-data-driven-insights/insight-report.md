# Customer Churn Insight Report

**Period Analyzed**: Last 12-18 months  
**Audience**: Retention leadership, Product, Customer Success  
**Author**: Business Analyst

---

## Executive Summary

Churn has increased 2.4 percentage points year-over-year. The largest opportunity lies in the first 90 days after signup and among customers showing sharp engagement drops. Three prioritized interventions are recommended, with estimated impact ranges.

---

## Key Findings

### 1. Early-Life Churn Dominates
- Customers who cancel within the first 90 days account for **47% of all churn events**.
- Early churners show significantly lower product engagement in weeks 2-6 compared with retained peers.
- Acquisition channel matters: paid social cohorts have ~1.6x higher early churn than organic or referral.

### 2. Engagement Drop is a Strong Leading Indicator
- Customers whose activity dropped >50% month-over-month had an observed churn rate **3.1x higher** than stable users in the subsequent 60 days.
- Complete cessation of logins for 21+ days preceded 38% of churn events.

### 3. Support Experience Correlates with Retention
- Customers with >=2 unresolved or low-CSAT tickets in a quarter churned at nearly twice the average rate.
- Time-to-first-response on critical tickets showed a clear relationship with later retention.

### 4. Plan & Price Sensitivity
- Customers on the entry-level plan who experienced a price increase or feature restriction showed elevated churn in the following 45 days.
- Higher-tier customers are more sensitive to reliability and feature gaps than to price.

---

## Segmented Risk View (Simplified)

| Segment | Approx. % of Base | Relative Churn Risk | Suggested Focus |
|---------|-------------------|---------------------|-----------------|
| New (0-90 days) + Low engagement | 12% | Very High | Onboarding & activation |
| Existing + Sharp engagement drop | 8% | High | Proactive outreach |
| Multiple support issues | 5% | High | Success intervention |
| Stable high-engagement | 45% | Low | Maintain & expand |
| Other | 30% | Medium | Monitor |

---

## Recommendations (Prioritized)

### Recommendation 1: Strengthen Activation in First 45 Days
- Define a clear activated state (e.g., key features used + second session within 14 days).
- Trigger in-app guidance and success outreach for users missing activation milestones.
- **Expected impact**: 10-18% relative reduction in early churn.

### Recommendation 2: Engagement-Drop Early Warning System
- Operationalize the >50% drop and 21-day inactivity signals into a shared risk list.
- Pair with playbooks for Customer Success (check-in, value reinforcement, or offer).
- **Expected impact**: Recover 15-25% of at-risk accounts that currently churn silently.

### Recommendation 3: Close the Loop on Support Pain
- Flag accounts with repeated or low-CSAT tickets for proactive success review.
- Track support-driven save rate as a success metric.
- **Expected impact**: Measurable reduction in churn among the high-support cohort.

---

## Proposed Success Metrics

| Metric | Baseline | Target (6 months) |
|--------|----------|-------------------|
| Overall monthly churn rate | X% | X - 0.8 to 1.2 pp |
| 90-day retention | Y% | +4 to 7 pp |
| % of churn preceded by engagement alert | - | >= 60% of preventable churn flagged |
| Activation rate (new customers) | Z% | +10 pp |

---

## Next Steps
1. Validate findings with Data Science / BI (statistical significance & segment stability).
2. Socialize recommendations with Product and Customer Success leads.
3. Define experiment design for Recommendation 1 and 2.
4. Build the monitoring dashboard (see separate requirements).
