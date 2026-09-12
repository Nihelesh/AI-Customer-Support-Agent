# Phase 2 — Dataset Acquisition & Understanding

## Objective

Obtain the customer-support conversation dataset, understand its structure, identify the relevant fields, and verify that the dataset contains the information required for conversation reconstruction and intent classification.

---

## 2.1 Dataset Loaded

The customer-support Twitter dataset was loaded into a Pandas DataFrame.

The dataset contains customer and company support tweets, including information required to reconstruct conversations.


Important columns identified:

- `tweet_id`
- `created_at`
- `author_id`
- `inbound`
- `in_response_to_tweet_id`
- `text`
- `conversation_id`

---

## 2.2 Dataset Size

Shape: (2811774, 7)

---

## 2.3 Inbound and Outbound Messages

The `inbound` column was examined to understand message direction.

Initial counts:

| Message Type | Count |
|---|---:|
| Customer / inbound | 203,598 |
| Outbound | 170,444 |

The selected AmazonHelp conversations contain customer messages as well as AmazonHelp responses.

---

## 2.4 Author Analysis

The most frequent authors were examined to understand the composition of the dataset.

The primary author was:

- `AmazonHelp` — 169,840 tweets

Other authors were also present because some conversations involve external delivery companies or other support accounts.

Examples include:

- `UPSHelp`
- `Tesco`
- `XboxSupport`
- `SpotifyCares`
- `AppleSupport`
- `hulu_support`
- `JetBlue`
- `ChaseSupport`

This observation was important because a conversation can contain responses from another company or service provider in addition to AmazonHelp.

---

## 2.5 Conversation Reconstruction

The dataset contains `in_response_to_tweet_id`, which was used to understand the reply relationship between tweets.

A parent-tweet mapping was created:

tweet_id → in_response_to_tweet_id

## 2.5 Conversation Validation

The reconstructed conversations were manually inspected.

The validation showed that:

Tweets belonging to the same conversation are meaningfully related.
The chronological ordering is sensible.
Customer and company responses occur in the expected sequence.
Response chains correctly connect related tweets.
Conversations can contain multiple turns.
Some conversations involve another support company, such as UPSHelp.
Conversation chains terminate when there is no further in_response_to_tweet_id.

## 2.6 Phase 2 Outcome

Phase 2 established an understanding of the dataset structure and confirmed that the dataset is suitable for the planned customer-support intent classification project.