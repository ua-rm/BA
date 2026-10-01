# Sample Data Dictionary
## Customer & Order Domain (Excerpt)

| Entity     | Attribute            | Data Type     | Description                   | Source System  | Notes / Business Rules |
|--------    |-----------           |-----------    |-------------                  |--------------- |------------------------|
| Customer   | customer_id          | UUID / BIGINT | Unique customer identifier    | CRM / Identity | Surrogate key          |
| Customer   | email                | VARCHAR(255)  | Primary email address         | Identity       | Unique, required for 
                                                                                                        guest orders          |
| Customer   | signup_date          | DATE          | Date account was created      | Identity       | Null for pure guest 
                                                                                                        orders until account 
                                                                                                        created               |
| Customer   | acquisition_channel  | VARCHAR(50)   | How the customer was acquired | Marketing      | Values: organic, 
                                                                                                        paid_social, referral, 
                                                                                                        email, etc.           |
| Order      | order_id             | UUID / BIGINT | Unique order identifier       | OMS           |                         |
| Order      | customer_id          | UUID / BIGINT | Link to customer 
                                        (nullable for pure guest)                   | OMS           |                         |
| Order      | order_status         | VARCHAR(30)   | Current status                | OMS           | Enum: pending, paid, 
                                                                                                        processing, shipped, 
                                                                                                        delivered, cancelled  |
| Order      | created_at           | TIMESTAMP     | Order creation timestamp      | OMS           | UTC                     |
| Order      | total_amount         | DECIMAL(12,2) | Final amount charged          | OMS           | Includes tax & shipping |
| Order Line | order_id             | UUID / BIGINT | Parent order                  | OMS           |                         |
| Order Line | product_id           | UUID / BIGINT | Product ordered               | Catalog       |                         |
| Order Line | quantity             | INTEGER       | Quantity ordered              | OMS           | > 0                     |
| Order Line | unit_price           | DECIMAL(10,2) | Price at time of order        | OMS           | Snapshot, not live price|
| Engagement | customer_id          | UUID / BIGINT |                               | Events DB     |                         |
| Engagement | event_type           | VARCHAR(50)   | login, view_product, 
                                                        add_to_cart, etc.           | Events DB     | Controlled vocabulary   |
| Engagement | event_date           | TIMESTAMP     | When the event occurred       | Events DB     | UTC                     |

---

### Usage Notes for Analysts
- Always confirm whether guest orders are later linked to a customer_id when an account is created.
- Price fields should reflect the amount at time of transaction (Point-in-time), not current catalog price.
- Status values should be aligned across OMS, WMS, and analytics layers.
