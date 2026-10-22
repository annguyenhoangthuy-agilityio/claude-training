# Day 02 — Ticket analysis, reproduce and understand

Oct 22, 2026

## Exercises

Day 02 has two exercises: ticket analysis in the morning and bug reproduction in the afternoon. Source: the [ShuttleShop — Training Backlog](https://claude.ai/artifact/Amu78xhgZQQewDVvL1LfE5).

1. **Ticket analysis.** Take 5 real tickets from the training backlog. For each, write the three-sentence analysis: what it asks, what's ambiguous, first step. Use Claude to find gaps and draft clarifying questions; compare with a partner's analysis.
2. **Reproduce and understand.** Each pair takes one seeded bug ticket. Get the app running locally from scratch, reproduce the bug, and write exact repro steps into the ticket.

## Exercise 1

### Prompt

Prompt 1 (SS-201):

```text
You are a senior developer reviewing a feature ticket before implementation.
Ticket: SS-201 in the backlog @https://claude.ai/artifact/Amu78xhgZQQewDVvL1LfE5

Do two things:

1. Answer these 3 questions, 1–2 sentences each:
   - What it asks: the core scope of the ticket.
   - What's ambiguous: the most important unclear or missing points
     (e.g. business rules, validation, error handling, security, UI states).
   - First step: what the developer should do first to start implementation.

2. Draft clarifying questions for the ticket author based on the gaps above.
   - Maximum 5 questions, each under 30 words.
   - Order them by impact: questions that block implementation come first.
   - Only ask what the ticket doesn't already answer; fewer than 5 is fine.

Output format:
## Summary
**What it asks:** ...
**What's ambiguous:** ...
**First step:** ...

## Clarifying questions
1. ...
```

Prompt 2 (SS-202 to SS-205):

```text
continue to review ticket SS-202, SS-203, SS-204, SS-205 following to the outline above
```

### Result

| Ticket | What it asks | What's ambiguous | First step | Clarifying questions (ordered by impact) |
| --- | --- | --- | --- | --- |
| SS-201 Sign up & log in | Sign up with email or phone + password, log in, reset a forgotten password via link, stay logged in after closing the browser. | No email/phone verification or uniqueness rules; no password policy; no session lifetime, "Remember me" or logout; no reset flow for phone-only users; no failed-login lockout or safe error wording. | Confirm the identity model (verification, uniqueness), then sketch the user/credential schema and sign-up/login sequence. | (1) Must email or phone be verified (OTP / confirmation link) before the account is active, and can unverified users log in or place orders? (2) Can one account have both email and phone? What happens if someone signs up with an email or phone already registered? (3) How does a phone-only user reset their password (SMS link, OTP, other), and how long is a reset link/code valid? (4) How long should a session last after closing the browser? Is there "Remember me" and logout, and must logout invalidate all devices? (5) What are the password rules and failed-login policy (attempt limit, lockout duration, error wording that doesn't reveal account existence)? |
| SS-202 Product catalog by category | Browse 6 categories (name, image, price), select size/color/type, set quantity, add to cart; out-of-stock products can't be bought. | Variant model undefined (price/SKU/stock per combination, options per category, meaning of "type"); out-of-stock behavior vague; no pagination, sort, filters or empty state. | Model products and variants with the author; SS-203, SS-204 and SS-206 depend on it. | (1) Does each option combination (e.g., blue / 4U) have its own SKU, price and stock, or do options share one price and stock? (2) Which option types apply to each category, and what does "type" mean (e.g., racket weight, grip size, shuttle speed)? (3) When a product or variant is out of stock: hidden, shown disabled with a label, or "Notify me"? Can other variants still be bought? (4) Does the category page need pagination, sorting or filters? If so, which ones and how many products per page? (5) Is quantity capped by available stock, a fixed per-order limit, or both? |
| SS-203 Add to cart | Add items (duplicates increase quantity), cart icon count, change quantity/remove with live subtotal, cart persists on return. | Guest cart, retention period and merge on login unclear; "same product" vs same variant; no handling of stock limits, price changes, out-of-stock items, quantity 0; option change in cart (implied by SS-206) missing. | Decide the cart storage model (client vs server, guest vs logged-in, merge on login). | (1) Can guests add to cart? If yes, does the guest cart merge with the account cart after login, and how are conflicts handled? (2) How long is the cart kept: until browser storage clears, a fixed number of days, or indefinitely for logged-in users? (3) Does "same product" mean the same variant? Should different colors or sizes be separate cart lines? (4) If an item's price changes or it goes out of stock while in the cart: warn, auto-update, or block checkout? (5) Can customers change options (color/size) in the cart, as SS-206 suggests, or only quantity and remove? |
| SS-204 Checkout | Enter shipping info, see subtotal + location-based shipping fee + total, pay by COD or bank transfer, order created as "Pending", confirmation sent. | No shipping fee rule (zones, carrier API, free shipping, unsupported areas); bank transfer flow undefined (instructions, who confirms, unpaid timeout); guest checkout, field validation, stock reservation, confirmation channel, double-submit handling missing. | Get the shipping fee rules and the order status lifecycle (incl. bank transfer states). | (1) How is the shipping fee calculated (zone table, carrier API like GHN/GHTK, weight)? Any free-shipping thresholds or areas not served? (2) For bank transfer: what does the customer see (account info, QR, reference)? Who confirms payment, and when do unpaid orders expire? (3) Can guests check out, or must they log in (SS-201)? Can logged-in users pick saved addresses (SS-207)? (4) Is stock reserved or deducted when the order is placed? What if an item sells out between cart and "Place order"? (5) Is the confirmation sent by email, SMS, an on-screen page, or a combination, and what must it contain? |
| SS-205 Order history & manage orders | List orders newest first (ID, date, total, status), view details, cancel undelivered orders, reorder into cart. | "Not delivered yet" allows cancelling shipped orders; refunds and restocking missing; reorder edge cases (out of stock, repriced, cart merge); "track deliveries" has no AC; no pagination or own-orders-only rule. | Align the order status lifecycle with SS-204, then define which statuses allow cancellation. | (1) Which statuses allow cancellation (only "Pending", or also "Confirmed"/"Shipping")? Is a confirmation step or cancel reason required? (2) When a paid bank-transfer order is cancelled, how is the refund handled? Is stock returned automatically? (3) On "Reorder", what happens to out-of-stock, discontinued or repriced items? Are items added to or replacing the current cart? (4) What does "track deliveries" require: a status timeline, a carrier tracking number/link, or only the status column? (5) Does "My orders" need pagination or filters (e.g., by status)? How many orders per page? |

## Exercise 2

### Prompt

```plain
You are a QA. Rewrite the bug ticket below so a developer can reproduce the bug.

Bug ticket SS-206 in the training backlog

Tasks:
Rewrite the ticket with these sections:
   - Title: [Area] short description of the wrong behavior
   - Environment & setup: OS/browser
   - Preconditions: starting state, account/role, test data
   - Steps to reproduce: numbered, one action per step, concrete data
   - Expected result
   - Actual result
   - Frequency: always / intermittent
```

### Result

#### Rewritten ticket

**Title:** \[Cart\] Cart shows the default color instead of the selected color when adding a racket on mobile

**Environment & setup**

- Reported: mobile, device and browser unknown (customer report via Facebook page).
- Reproduce on: iPhone Safari (iOS \[TBC\]) and Android Chrome (\[TBC\]); also desktop Chrome on the same build to confirm it is mobile-only.
- Build / URL: local build, commit \[TBC\].

**Preconditions**

- Role: Guest (not logged in). Repeat as Customer if it reproduces.
- Cart: empty (clear it or use a fresh private window).
- Test data: product "QA Racket 01" in Rackets, with 2 color variants, each with its own SKU and price:

| Variant | SKU | Price (VND) | Stock |
| --- | --- | --- | --- |
| Red (default) | QA-R01-RED | 1,200,000 | 10 |
| Blue | QA-R01-BLU | 1,350,000 | 10 |

**Steps to reproduce**

1. On a mobile device, open the Rackets category.
2. Tap "QA Racket 01".
3. Verify Red is pre-selected and the price shows 1,200,000 VND.
4. Tap the Blue color option.
5. Verify the product page now shows Blue and 1,350,000 VND.
6. Tap "Add to cart".
7. Open the cart.

**Expected result:** The cart has 1 line: QA Racket 01, color Blue, SKU QA-R01-BLU, price 1,350,000 VND.

**Actual result:** The cart line shows color Red \[TBC: confirm; note whether the price shows 1,200,000 or 1,350,000; attach screenshot or screen recording\].

**Frequency:** \[TBC\] after at least 5 attempts per device (e.g. "5/5 on iOS Safari, 0/5 on desktop Chrome"). The report suggests always on mobile.

**Notes**

- The second symptom ("changed it and the price changed too") is a different action (editing color in the cart) with its own expected result (AC2). Log it as a separate bug once reproduced.
- Confirm the variants really have different prices before calling the price change a bug.
- Dependency: SS-203 doesn't define whether color can be changed in the cart; confirm the feature exists before testing the second symptom.
