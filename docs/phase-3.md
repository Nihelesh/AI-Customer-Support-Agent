# Phase 3 — Brand Exploration & Selection

## Objective

Explore the available support brands in the dataset and select one brand as the primary focus for the customer-support AI project.

The selected brand should provide enough conversation volume, customer interactions, conversation depth, and issue diversity to support the later intent classification and evaluation phases.

---

## 3.1 Brands Considered

The following five support brands were compared:

- AppleSupport
- AmazonHelp
- Uber_Support
- SpotifyCares
- Delta

---

## 3.2 Brand Comparison

The brands were compared using:

- Number of outbound support tweets
- Number of distinct customers
- Number of reconstructed conversations
- Average messages per conversation
- Issue diversity

| Brand | Outbound Tweets | Distinct Customers | Conversations | Avg. Messages / Conversation | Issue Diversity |
|---|---:|---:|---:|---:|---:|
| AppleSupport | 106,860 | 76,366 | 80,702 | 2.9 | 10 |
| AmazonHelp | 169,840 | 71,049 | 82,534 | 4.5 | 10 |
| Uber_Support | 56,270 | 38,300 | 41,923 | 3.0 | 6 |
| SpotifyCares | 43,265 | 27,794 | 28,280 | 3.0 | 5 |
| Delta | 42,253 | 22,331 | 26,166 | 3.0 | 6 |

---

## 3.3 Observations

### AppleSupport

AppleSupport has a large number of conversations and customers, with approximately 2.9 messages per conversation.

It also showed high issue diversity.

However, its average conversation depth was lower than AmazonHelp.

---

### AmazonHelp

AmazonHelp had the highest number of outbound support tweets and the highest number of reconstructed conversations among the five brands.

It also had the highest average conversation length at approximately 4.5 messages per conversation.

AmazonHelp showed broad issue diversity, making it suitable for studying different types of customer-support problems.

---

### Uber_Support

Uber_Support provided a substantial number of conversations and customers.

However, its conversation volume and issue diversity were lower than AmazonHelp and AppleSupport.

---

### SpotifyCares

SpotifyCares had fewer conversations and customers compared with the larger support datasets.

Its issue diversity was also lower.

---

### Delta

Delta had fewer conversations than AmazonHelp, AppleSupport, and Uber_Support.

Its issue diversity was also lower than the two strongest candidates.

---

## 3.4 Brand Selection

Based on the comparison, **AmazonHelp was selected as the primary brand for the project**.

The main reasons were:

1. High conversation volume.
2. Highest number of outbound support tweets among the compared brands.
3. Highest number of reconstructed conversations.
4. Highest average conversation length.
5. Broad issue diversity.
6. Sufficient customer interactions for creating an evaluation dataset.
7. Conversations contain multiple turns, providing useful context for intent classification.

---

## 3.5 Selection Decision

The final decision was:

> **Selected Brand: AmazonHelp**

The project will therefore focus on AmazonHelp conversations for the remaining data preparation, intent annotation, golden-set construction, baseline development, and AI-agent evaluation phases.

---

## 3.6 Conversation-Level Validation Before Proceeding

Before continuing with AmazonHelp, reconstructed conversation threads were manually inspected.

The validation confirmed that:

- Tweets within a reconstructed conversation are related.
- Tweets appear in a meaningful chronological order.
- Customer and support responses form coherent interaction sequences.
- Response relationships were reconstructed correctly.
- Conversations can contain multiple turns.
- Some conversations can involve other support accounts.

Example:

Customer → AmazonHelp → Customer → AmazonHelp

Some conversations can also involve another support organization:

Customer → AmazonHelp → UPSHelp → Customer → AmazonHelp

This validation increased confidence that the selected AmazonHelp conversation threads can be used for downstream intent annotation.

---

## 3.7 Outcome

Phase 3 resulted in the selection of **AmazonHelp** as the target brand.

The brand-selection process was based on quantitative comparison and manual inspection of reconstructed conversations rather than selecting a brand arbitrarily.

The selected AmazonHelp dataset contains:

- **82,534 conversations**
- **169,840 AmazonHelp outbound responses**
- **71,049 distinct customers**
- Approximately **4.5 messages per conversation**
- Broad customer-support issue diversity

The project proceeds with AmazonHelp as the fixed target dataset.