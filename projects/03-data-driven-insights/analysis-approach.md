# Analysis Approach & Sample SQL

## 1. Problem Framing

**Business Question**: Why is churn increasing and which customers should we focus retention efforts on?

**Hypotheses Explored**
1. Newer customers (first 90 days) churn at a significantly higher rate.
2. Customers with declining engagement (logins, feature usage) in the prior 30 days are at elevated risk.
3. Support ticket volume and unresolved issues correlate with higher churn.
4. Price-sensitive segments react strongly to plan changes or competitors.

---

## 2. Data Sources (Fictionalized)

| Source | Key Entities | Notes |
|--------|--------------|-------|
| Customer dimension | customer_id, signup_date, plan, region, acquisition_channel | |
| Subscription events | start, cancel, plan_change timestamps | |
| Engagement events | logins, feature_usage, session duration | Last 12 months |
| Support tickets | ticket_id, created, resolved, category, CSAT | |

---

## 3. Sample Analytical Queries

### 3.1 Overall Churn Rate by Cohort (Signup Month)

```sql
SELECT
    DATE_TRUNC('month', c.signup_date) AS cohort_month,
    COUNT(DISTINCT c.customer_id) AS customers,
    COUNT(DISTINCT CASE WHEN s.cancel_date IS NOT NULL THEN c.customer_id END) AS churned,
    ROUND(
        COUNT(DISTINCT CASE WHEN s.cancel_date IS NOT NULL THEN c.customer_id END) * 100.0
        / COUNT(DISTINCT c.customer_id), 2
    ) AS churn_rate_pct
FROM customers c
LEFT JOIN subscriptions s ON c.customer_id = s.customer_id
WHERE c.signup_date >= CURRENT_DATE - INTERVAL '18 months'
GROUP BY 1
ORDER BY 1;
```

### 3.2 Early Churn (within first 90 days)

```sql
SELECT
    CASE
        WHEN s.cancel_date IS NOT NULL
         AND s.cancel_date <= c.signup_date + INTERVAL '90 days' THEN 'Churned_0_90'
        ELSE 'Retained_or_Later'
    END AS early_churn_flag,
    COUNT(*) AS customers,
    ROUND(AVG(engagement.logins_30d), 1) AS avg_logins_last_30d
FROM customers c
JOIN subscriptions s ON c.customer_id = s.customer_id
LEFT JOIN (
    SELECT customer_id, COUNT(*) AS logins_30d
    FROM engagement_events
    WHERE event_type = 'login'
      AND event_date >= CURRENT_DATE - INTERVAL '30 days'
    GROUP BY 1
) engagement ON c.customer_id = engagement.customer_id
GROUP BY 1;
```

### 3.3 Engagement Drop as Leading Indicator

```sql
WITH monthly_engagement AS (
    SELECT
        customer_id,
        DATE_TRUNC('month', event_date) AS month,
        COUNT(*) AS events
    FROM engagement_events
    WHERE event_date >= CURRENT_DATE - INTERVAL '6 months'
    GROUP BY 1, 2
),
engagement_trend AS (
    SELECT
        customer_id,
        SUM(CASE WHEN month = DATE_TRUNC('month', CURRENT_DATE - INTERVAL '1 month') THEN events ELSE 0 END) AS events_last_month,
        SUM(CASE WHEN month = DATE_TRUNC('month', CURRENT_DATE - INTERVAL '2 month') THEN events ELSE 0 END) AS events_prev_month
    FROM monthly_engagement
    GROUP BY 1
)
SELECT
    CASE
        WHEN events_prev_month > 0 AND events_last_month * 1.0 / events_prev_month < 0.5 THEN 'Sharp_Drop'
        WHEN events_last_month = 0 AND events_prev_month > 0 THEN 'Stopped'
        ELSE 'Stable_or_Up'
    END AS engagement_status,
    COUNT(*) AS customers,
    AVG(CASE WHEN s.cancel_date IS NOT NULL THEN 1 ELSE 0 END) AS observed_churn_rate
FROM engagement_trend e
LEFT JOIN subscriptions s ON e.customer_id = s.customer_id
GROUP BY 1
ORDER BY observed_churn_rate DESC;
```

---

## 4. Analytical Notes

- All queries are illustrative and written in standard SQL (compatible with PostgreSQL / BigQuery style).
- In a real engagement these would be refined with data engineers and validated against known figures.
- Privacy and data minimization principles applied (no PII in analysis layer).
