# ShuttleShop — Day 02 Training Backlog

Oct 22, 2026

## Context

This is a mock backlog of 7 tickets for Day 02 practice: ticket analysis in the morning (SS-201 to SS-205, SS-207) and bug reproduction in the afternoon (SS-206). Gaps are planted on purpose and not marked.

**ShuttleShop** is an online store for badminton accessories: rackets, shoes, apparel, shuttlecocks, strings and grips, bags.

| Role | What they do |
| --- | --- |
| Guest | Browses products without logging in |
| Customer | Signs up, buys products, tracks orders, manages profile |
| Shop Admin | Manages products, orders and users (no tickets in this set) |

For each ticket, write the three-sentence analysis first (what it asks, what's ambiguous, first step), then use Claude to find more gaps and draft clarifying questions.

## SS-201 — Sign up & log in

**Description**

As a customer, I want to create an account and log in, so that I can place orders and track them. Customers can sign up with email or phone number. Users stay logged in after closing the browser.

**Acceptance Criteria**

- **AC1:** Given I am on the Sign up page, when I enter a valid email or phone number and a password and submit, then my account is created and I am logged in.
- **AC2:** Given I already have an account, when I enter the correct credentials, then I am redirected to the home page.
- **AC3:** Given I enter a wrong password, when I submit, then an error message is shown.
- **AC4:** Given I forgot my password, when I click "Forgot password", then I receive a link to reset it.

## SS-202 — Product catalog by category

**Description**

As a customer, I want to browse products by category and choose product options, so that I can find the right gear. Categories: Rackets, Shoes, Apparel, Shuttlecocks, Strings & Grips, Bags.

**Acceptance Criteria**

- **AC1:** Given I open a category, when the page loads, then I see a list of products with name, image and price.
- **AC2:** Given I open a product page, when the product has options, then I can select size, color and type.
- **AC3:** Given I have selected options, when I set the quantity, then I can add the product to the cart.
- **AC4:** Given a product is out of stock, when I view it, then I cannot buy it.

## SS-203 — Add to cart

**Description**

As a customer, I want to add products to my cart and adjust them, so that I can review what I'm buying before checkout.

**Acceptance Criteria**

- **AC1:** Given I selected all required options, when I click "Add to cart", then the item is added and the cart icon shows the number of items.
- **AC2:** Given the same product is already in my cart, when I add it again, then the quantity is increased.
- **AC3:** Given I am on the Cart page, when I change the quantity or remove an item, then the subtotal is updated.
- **AC4:** Given I leave the site, when I come back later, then my cart is still there.

## SS-204 — Checkout

**Description**

As a customer, I want to check out my cart, so that I can receive my products at home. Payment methods: COD and bank transfer. Shipping fee depends on location.

**Acceptance Criteria**

- **AC1:** Given I have items in my cart, when I click "Checkout", then I am asked to enter shipping information.
- **AC2:** Given I entered my address, when the shipping fee is calculated, then I see subtotal, shipping fee and total.
- **AC3:** Given I chose a payment method, when I click "Place order", then the order is created with status "Pending".
- **AC4:** Given my order is placed, when the process completes, then I receive an order confirmation.

## SS-205 — Order history & manage orders

**Description**

As a customer, I want to view and manage my past orders, so that I can track deliveries and buy again easily.

**Acceptance Criteria**

- **AC1:** Given I am logged in, when I open "My orders", then I see my orders sorted by newest first, with order ID, date, total and status.
- **AC2:** Given I open an order, when the detail page loads, then I see items, options, quantities, prices and shipping address.
- **AC3:** Given my order has not been delivered yet, when I click "Cancel order", then the order status changes to "Cancelled".
- **AC4:** Given I view a past order, when I click "Reorder", then all items are added to my cart.

## SS-206 — Bug: Cart shows wrong item after changing color

*For the afternoon session (reproduce and understand).*

**Description**

Reported by a customer via the Facebook page: "I picked the blue racket but the cart shows red. Then I changed it and the price changed too?? Very confusing." Seems to happen on mobile.

**Acceptance Criteria (expected behavior after fix)**

- **AC1:** Given I select a color on the product page, when I click "Add to cart", then the cart shows the color I selected.
- **AC2:** Given an item is in my cart, when I change its color, then the price shown is the correct price for that color.

To complete during the afternoon: Environment, Steps to reproduce, Actual result, Severity/Priority, Evidence.

## SS-207 — Manage personal information

*Extra practice ticket.*

**Description**

As a customer, I want to update my personal information, so that my orders are delivered to the right place and I can be contacted.

**Acceptance Criteria**

- **AC1:** Given I am on "My profile", when I update my name, phone or email and save, then the changes are saved and a success message is shown.
- **AC2:** Given I want to change my password, when I enter a new password and save, then my password is updated.
- **AC3:** Given I have saved addresses, when I add, edit or delete an address, then the list is updated.
- **AC4:** Given I enter invalid data, when I save, then the system shows a validation error.
