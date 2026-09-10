Problem:

A company has a customer support team which receives thousands of conversations. Humans have to do repeated tasks like read message, understand problem, search previous cases, write response and decides whether escalation is required.

Humans need to do this repetitive work which consumes their time and effort.

Input:

Customer Support on Twitter — Kaggle thoughtvector/customer-support-on-twitter. This dataset has approximately 3 million tweets for various brands. It is real, noisy and imperfect. After data cleaning and data preprocessing steps, the input will look something like,

{
  "customer_message": "My order hasn't arrived yet"
}

Output:

{
  "intent": "DELIVERY_ISSUE",
  "reply": "Sorry to hear about the delay. Please DM us your order number so we can check the status.",
  "decision": "AUTO_HANDLE",
  "reason": "Similar delivery issues have historically been resolved through standard order-status assistance."
}

Core capabilities:

1. Intent classification
2. Grounded reply generation
3. Auto-handle vs escalation decision

Out of scope:

- No huge production chatbot with Twitter integration
- No fancy frontend
- No deployment to production
- No massive deep learning model