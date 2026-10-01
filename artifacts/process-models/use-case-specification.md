# Use Case Specification
## UC-01: Complete Guest Checkout

---

### 1. Use Case Details
| Field             | Value                     |
|-------            |-------                    |
| **Use Case ID**   | UC-01                     |
| **Name**          | Complete Guest Checkout   |
| **Actor(s)**      | Guest Customer (1), 
                        Payment Gateway (2), 
                        Notification Service (2)|
| **Priority**      | High (Must Have)          |
| **Source**        | BRD BR-01, 
                        Workshop 2025-03-05     |

---

### 2. Description
A visitor who is not logged in can purchase items in their cart without creating an account. The system collects necessary shipping and payment information, processes the payment, creates an order, and sends a confirmation.

---

### 3. Preconditions
- Cart contains at least one in-stock item
- User is not authenticated (or chooses Continue as Guest)

---

### 4. Postconditions
**Success**
- Order is created and confirmed
- Payment is captured (or authorized per business rules)
- Confirmation email is sent to the provided address
- Inventory is reserved / decremented

**Failure**
- Cart remains intact
- User is informed of the specific issue (payment declined, address invalid, etc.)

---

### 5. Main Success Scenario
1. User selects Checkout from cart
2. System presents guest checkout option
3. User enters email and shipping address
4. System validates address and displays available shipping methods with prices and ETAs
5. User selects shipping method
6. System updates order total
7. User enters payment details
8. System processes payment via gateway
9. System creates order and sends confirmation email
10. System displays order confirmation page

---

### 6. Alternative & Exception Flows
**A1 - User has existing account (email match)**
- At step 3, system detects existing account and offers login without losing cart
- User may continue as guest or log in

**E1 - Payment declined**
- At step 8, gateway returns decline
- System displays clear message and allows retry or alternative payment method
- Order is not created

**E2 - Item becomes out of stock during checkout**
- System detects stock issue before payment
- Informs user and offers to remove item or cancel

---

### 7. Business Rules
- Guest orders are linked to email address for support and future account creation
- Same validation rules apply to guest and registered users for address and payment
- Confirmation email must contain order number, items, total, and estimated delivery

---

### 8. Non-Functional Considerations
- Checkout steps should feel progressive (minimize full page reloads)
- Payment handling must remain PCI compliant (no raw card data stored)
- Mobile usability required
