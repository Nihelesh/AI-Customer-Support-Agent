# Intent Taxonomy

## 1. Purpose

This document defines the customer-support intent taxonomy used for the AmazonHelp customer-support AI agent.

The taxonomy was created through manual exploration of reconstructed customer-support conversations from the TWCS dataset.

The goal is to provide a practical and interpretable set of intents that can be used for intent classification, retrieval, response generation, and evaluation.

---

## 2. Taxonomy Design Approach

The taxonomy was developed through the following process:

1. Reconstructed conversation threads from tweet-response relationships.
2. Inspected sampled AmazonHelp conversations manually.
3. Identified recurring customer problems and requests.
4. Grouped similar observations into broader intent families.
5. Created candidate intents within each family.
6. Tested the candidate taxonomy on 50 previously unseen conversations.
7. Confirmed that all 50 sampled conversations could be assigned to
   an existing intent.
8. Finalized the taxonomy for subsequent project phases.

The taxonomy is intentionally designed to be practical for this project rather than attempting to reproduce Amazon's complete internal support taxonomy.

---

## 3. Labeling Principle

Each conversation is assigned one primary intent.

The primary intent represents the main customer problem or goal that needs to be addressed.

If a conversation contains multiple issues, the issue that represents the customer's primary support need should be selected.

---

## 4. Intent Families

### 4.1 Delivery

- DELIVERY_DELAY
- DELIVERY_NOT_RECEIVED
- DELIVERED_BUT_MISSING
- DELIVERY_LOCATION_PROBLEM
- COURIER_OR_DRIVER_ISSUE
- DELIVERY_TRACKING_PROBLEM
- DELIVERY_ATTEMPT_PROBLEM
- DAMAGED_DURING_DELIVERY

### 4.2 Orders

- ORDER_CANCELLATION
- ORDER_PLACEMENT_PROBLEM
- ORDER_STATUS
- ORDER_MODIFICATION
- WRONG_OR_MISSING_ITEM
- PRODUCT_AVAILABILITY

### 4.3 Returns

- RETURN_REQUEST
- RETURN_ELIGIBILITY
- RETURN_PICKUP_PROBLEM
- RETURN_PROBLEM
- REPLACEMENT_PROBLEM

### 4.4 Payment & Billing

- PAYMENT_FAILURE
- CHARGE_PROBLEM
- REFUND_MONEY_PROBLEM
- DUPLICATE_CHARGE
- UNAUTHORIZED_PAYMENT
- AMAZON_PAY_PROBLEM

### 4.5 Prime & Subscriptions

- PRIME_MEMBERSHIP_PROBLEM
- PRIME_CHARGE_OR_RENEWAL
- PRIME_BENEFIT_PROBLEM
- SUBSCRIPTION_PROBLEM

### 4.6 Technical / Digital

- DEVICE_PROBLEM
- APP_OR_WEBSITE_PROBLEM
- DIGITAL_CONTENT_PROBLEM
- STREAMING_OR_PLAYBACK_PROBLEM
- ACCOUNT_LINKING_OR_CONNECTIVITY_PROBLEM

### 4.7 Security & Fraud

- SUSPICIOUS_EMAIL_OR_PHISHING
- SCAM_OR_FRAUD_CONCERN
- UNAUTHORIZED_ACCOUNT_ACTIVITY

### 4.8 Promotions & Offers

- PROMOTION_OR_DISCOUNT_PROBLEM
- CASHBACK_PROBLEM
- CONTEST_OR_QUIZ_INQUIRY
- OFFER_ELIGIBILITY

### 4.9 Customer Service

- CUSTOMER_SERVICE_COMPLAINT
- SUPPORT_AGENT_COMPLAINT
- UNRESOLVED_SUPPORT_ISSUE
- ESCALATION_REQUEST

### 4.10 General / Other

- GENERAL_INFORMATION
- PRODUCT_INFORMATION
- FEEDBACK
- APPRECIATION
- UNCLEAR_REQUEST

---

## 5. Taxonomy Validation

The candidate taxonomy was tested using 50 previously unseen AmazonHelp conversations.

All 50 conversations could be assigned to an existing intent.

No additional intent category was required during this validation sample.

This provided sufficient evidence to freeze the taxonomy for the remaining project phases.

---

## 6. Important Boundary Rules

### Delivery Delay vs Delivered but Missing

If the customer says the package has not arrived and delivery is still pending, use:

`DELIVERY_DELAY`

If Amazon shows the package as delivered but the customer cannot find it, use:

`DELIVERED_BUT_MISSING`

### Payment Failure vs Unauthorized Payment

If the customer attempted a payment and it failed, use:

`PAYMENT_FAILURE`

If the customer does not recognize a transaction, use:

`UNAUTHORIZED_PAYMENT`

### Product Problem vs Delivery Problem

If the package arrived but the product itself is damaged or defective, use a product-related intent.

If the package or delivery process itself caused the problem, use a delivery-related intent.

### Prime Delivery vs Prime Membership

If the main issue concerns delivery performance, use a delivery intent.

If the main issue concerns Prime membership, renewal, charges, or benefits, use a Prime-related intent.

### Feedback

If the customer is primarily praising or commenting on the support experience rather than requesting resolution of another issue, use the appropriate Customer Service or General / Other intent.