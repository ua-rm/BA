# User Stories & Acceptance Criteria
## E-Commerce Modernization - Prioritized Backlog

**Prioritization Method**: MoSCoW  
**Format**: As a [persona], I want [goal] so that [benefit]  
**Acceptance Criteria**: Given / When / Then

---

## Epic 1: Streamlined Checkout

### US-001 - Guest Checkout (Must Have)
**As a** first-time or infrequent shopper,  
**I want** to complete my purchase without creating an account,  
**so that** I can buy quickly and with less friction.

**Acceptance Criteria**
- Given I am on the cart page and not logged in  
  When I click Checkout  
  Then I am taken to a guest checkout flow that does not require account creation
- Given I complete guest checkout successfully  
  When the order is confirmed  
  Then I receive an order confirmation email with a link to create an account (optional)
- Given I am in guest checkout  
  When I provide an email that already has an account  
  Then the system offers me the option to log in without losing cart contents

**Story Points**: 8 | **Priority**: Must

---

### US-002 - Progressive Checkout Steps (Must Have)
**As a** customer,  
**I want** the checkout process to feel continuous and low-effort,  
**so that** I am less likely to abandon my cart.

**Acceptance Criteria**
- Given I am in checkout  
  When I complete shipping information  
  Then I automatically progress to payment without a full page reload (or with minimal perceived load)
- Given I am on any checkout step  
  When I click Back  
  Then previously entered information is retained
- Given I have items in my cart  
  When I view the checkout summary  
  Then I can see item details, quantities, prices, shipping estimate, and tax estimate before payment

**Story Points**: 13 | **Priority**: Must

---

### US-003 - Visible Shipping Options Early (Must Have)
**As a** customer,  
**I want** to see available shipping methods and estimated delivery dates before entering payment details,  
**so that** I can make an informed decision and avoid surprises.

**Acceptance Criteria**
- Given I have entered a valid shipping address  
  When the address is validated  
  Then available shipping options with price and estimated delivery date are displayed
- Given multiple shipping options exist  
  When I select one  
  Then the order total updates immediately to reflect the selected shipping cost

**Story Points**: 5 | **Priority**: Must

---

## Epic 2: Improved Product Discovery

### US-004 - Recently Viewed Products (Should Have)
**As a** returning visitor,  
**I want** to easily see products I recently viewed,  
**so that** I can continue my shopping journey without searching again.

**Acceptance Criteria**
- Given I have viewed one or more product detail pages in the current or previous session  
  When I visit the homepage or a category page  
  Then a Recently Viewed section displays up to 8 products
- Given I clear my browser data or explicitly clear history  
  When I return  
  Then recently viewed items are no longer shown

**Story Points**: 5 | **Priority**: Should

---

### US-005 - Recommended Products (Should Have)
**As a** shopper,  
**I want** to see personalized product recommendations,  
**so that** I can discover relevant items more easily.

**Acceptance Criteria**
- Given I am viewing a product detail page  
  When the page loads  
  Then a You may also like section shows at least 4 related products based on category / co-purchase data
- Given insufficient recommendation data exists  
  When the section would otherwise be empty  
  Then popular products from the same category are shown as fallback

**Story Points**: 8 | **Priority**: Should

---

## Epic 3: Mobile Experience

### US-006 - Mobile-Optimized Checkout (Must Have)
**As a** mobile shopper,  
**I want** the checkout experience to be easy to complete on my phone,  
**so that** I do not abandon due to usability issues.

**Acceptance Criteria**
- Given I am on a device with viewport width <= 768px  
  When I go through checkout  
  Then all form fields, buttons, and summary information are fully usable without horizontal scrolling
- Given I am using a mobile device  
  When I tap form fields  
  Then the correct keyboard type is presented (email, numeric, etc.)
- Given I am on mobile  
  When I reach the payment step  
  Then the primary call-to-action remains visible (sticky or easily reachable)

**Story Points**: 8 | **Priority**: Must

---

## Summary Backlog View

| ID | Title | Priority | Points | Epic |
|----|-------|----------|--------|------|
| US-001 | Guest Checkout | Must | 8 | Checkout |
| US-002 | Progressive Checkout | Must | 13 | Checkout |
| US-003 | Shipping Options Early | Must | 5 | Checkout |
| US-006 | Mobile-Optimized Checkout | Must | 8 | Mobile |
| US-004 | Recently Viewed | Should | 5 | Discovery |
| US-005 | Recommended Products | Should | 8 | Discovery |

**Total Must-Have Points**: 34  
**Total Should-Have Points**: 13
