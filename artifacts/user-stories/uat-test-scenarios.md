# UAT Test Scenarios
## Guest Checkout & Core Flows (Sample)

Business Analysts often support UAT by writing clear, business-oriented test scenarios.

---

### Scenario 1: Happy Path - Guest Checkout on Mobile
| Field | Detail |
|-------|--------|
| **Objective** | Verify a new visitor can complete a purchase as guest on mobile |
| **Preconditions** | Empty cart, user not logged in, product in stock |
| **Test Steps** | 1. Browse and add 2 items to cart<br>2. Proceed to checkout<br>3. Choose Continue as Guest<br>4. Enter email + valid shipping address<br>5. Select shipping method<br>6. Enter valid payment details<br>7. Submit order |
| **Expected Result** | Order confirmation displayed, confirmation email received, order visible in OMS with correct details |
| **Priority** | Critical |

---

### Scenario 2: Existing Email Detected
| Field | Detail |
|-------|--------|
| **Objective** | System correctly offers login when guest email matches existing account |
| **Preconditions** | Known customer email exists |
| **Test Steps** | 1. Add item to cart as guest<br>2. Enter existing customer email at checkout |
| **Expected Result** | Prompt offers option to log in; cart contents are preserved if user logs in |
| **Priority** | High |

---

### Scenario 3: Payment Declined
| Field | Detail |
|-------|--------|
| **Objective** | User receives clear feedback and can retry |
| **Preconditions** | Valid cart and shipping info |
| **Test Steps** | 1. Reach payment step<br>2. Enter details that trigger decline (test card)<br>3. Observe messaging<br>4. Retry with valid card |
| **Expected Result** | Clear decline message shown; no order created on decline; successful retry creates order |
| **Priority** | High |

---

### Scenario 4: Shipping Cost Visibility
| Field | Detail |
|-------|--------|
| **Objective** | Shipping options and costs appear before payment |
| **Test Steps** | 1. Enter valid address<br>2. Observe shipping section before payment fields |
| **Expected Result** | At least one shipping method with price and estimated date is shown; total updates on selection |
| **Priority** | Critical |

---

### Notes for UAT Coordination
- Provide test data packs (emails, addresses, test payment methods)
- Define entry/exit criteria with Product Owner
- Log defects with clear business impact and steps to reproduce
