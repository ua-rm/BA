# Requirements Workshop Notes
## E-Commerce Modernization - Discovery Session

**Date**: 2025-03-05  
**Duration**: 90 minutes  
**Facilitator**: Business Analyst  
**Attendees**: Head of E-Commerce, UX Lead, Engineering Lead, Marketing Manager, Customer Support Lead

---

## Workshop Objectives
1. Align on the primary problem we are solving
2. Identify highest-impact friction points in the current journey
3. Surface constraints and non-negotiables
4. Produce an initial prioritized list of capabilities for MVP

---

## Key Insights Captured

### Current Pain Points (Affinity Grouped)
**Checkout Friction**
- Forced account creation is the #1 cited reason for abandonment (Support tickets + session recordings)
- Too many steps / page loads on mobile
- Shipping cost surprise appears too late

**Discovery & Trust**
- Customers struggle to find previously viewed items
- Limited social proof and recommendations on product pages
- Mobile product images and information hierarchy feel cluttered

**Operational**
- Support team handles high volume of Where is my order? and checkout error tickets
- Marketing campaigns sometimes break on new landing page templates

### Success Vision (Paraphrased from stakeholders)
> A customer should be able to go from product interest to paid order in under 3 minutes on their phone, without creating an account, and feel confident about delivery and total cost the whole way.

---

## Decisions Made

| Decision | Owner | Notes |
|----------|-------|-------|
| Guest checkout is non-negotiable for MVP | Head of E-Com | Confirmed with CDO offline |
| We will not replace the payment gateway in Phase 1 | Eng Lead | Risk & timeline |
| Accessibility (WCAG 2.1 AA) is required | UX Lead + Legal | Compliance |
| Recommendations can start rule-based; ML later | Eng Lead | Feasibility |

---

## Open Questions / Follow-ups

1. Exact analytics events required for measuring the new funnel -> Analytics team
2. Impact of guest checkout on CRM / email marketing flows -> Marketing
3. Performance budget targets for mobile -> Engineering + UX

---

## Next Steps
- BA to draft BRD and initial user stories (target: 1 week)
- UX to begin low-fidelity flows for progressive checkout
- Engineering to spike guest session handling and cart persistence
- Follow-up refinement session scheduled for 2025-03-12
