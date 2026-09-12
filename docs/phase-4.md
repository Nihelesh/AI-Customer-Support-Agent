# Phase 4 — Clean & Prepare Conversations

## Objective

Clean and prepare the reconstructed AmazonHelp conversations for downstream intent annotation and evaluation.

The goal of this phase was to remove unnecessary Twitter-specific noise while preserving the actual customer-support meaning and conversation context.

---

## 4.1 Input Dataset

The input dataset was the reconstructed AmazonHelp conversation dataset produced during the previous phases.

Before cleaning:

- Number of tweets: **374,042**
- Number of conversations: **82,534**

The conversation structure was preserved during cleaning.

---

## 4.2 Timestamp Standardization

The `created_at` column was converted into a timezone-aware datetime format using Pandas.

```python
amazon_df["created_at"] = pd.to_datetime(
    amazon_df["created_at"],
    utc=True
)