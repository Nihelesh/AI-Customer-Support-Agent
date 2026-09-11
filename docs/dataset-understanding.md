# Dataset Understanding

## Dataset

Twitter Customer Support (TWCS)

## Source

Kaggle

## Dataset Description

The Customer Support on Twitter dataset is a large, modern corpus of tweets and replies to aid innovation in natural language understanding and conversational models, and for study of modern customer support practices and impact.

## Files

sample.csv
twcs.csv

## Number of Records

28,11,774

## Columns

7

1. tweet_id
The unique ID for this tweet

2. author_id
The unqiue ID for this tweet author (anonymized for non-company users)

3. inbound
Whether or not the tweet was sent (inbound) to a company

4. created_at
When the tweet was created

5. text
The text content of the tweet

6. response_tweet_id
The tweet that responded to this one, if any

7. in_response_to_tweet_id
The tweet this tweet was in response to, if any

## Initial Observations

Dataset size: 2,811,774 rows × 7 columns

Duplicate rows: 0

No exact duplicate rows were identified during the initial dataset-quality check.

Inbound:
True  → 1,537,843
False → 1,273,931

Missing values:
response_tweet_id → 1,040,629
in_response_to_tweet_id → 794,335

Conversation structure:
Tweet relationships can be reconstructed using the tweet and response ID fields.


## Brands

The dataset contains 108 authors with at least one outbound tweet.

Initial analysis shows that several recognizable customer-support accounts have exclusively outbound tweets, including AmazonHelp, AppleSupport, Uber_Support, SpotifyCares and others.

The `inbound` field combined with tweet-response relationships can be used to distinguish company
responses from customer messages and associate customer interactions with specific brands.

Brand selection will be performed after comparing candidate brands based on conversation volume,
customer interaction volume, response coverage and support-issue diversity.

## Brand Selection Scorecard

| Brand        | Outbound tweets | Distinct customers | Conversations | Avg messages per conversation | Issue diversity |
| ------------ | --------------: | -----------------: | ------------: | --------: | --------------: |
| AppleSupport |         106,860 |             76,366 |             80,702 |         2.9 |               10 |
| AmazonHelp   |         169,840 |             71,049 |             82,534 |         4.5 |               10 |
| Uber_Support |          56,270 |             38,300 |             41,923 |         3 |               6 |
| SpotifyCares |          43,265 |             27,794 |             28,280 |         3 |               5 |
| Delta        |          42,253 |             22,331 |             26166 |         3 |               6 |

## Conversation Structure

Conversation threads can be reconstructed using the tweet response relationships.

Manual inspection of AppleSupport conversations showed typical multi-turn interactions containing approximately 3–4 turns.

A common pattern observed was:

Customer → Company → Customer → Company

Conversation chains may terminate when no subsequent response tweet is recorded.

Some inspected conversations ended with the company directing the customer to continue the interaction through a direct message (DM). This behavior was observed during manual inspection and will be investigated quantitatively later.

### AppleSupport Candidate

AppleSupport has 106,860 outbound tweets and has directly responded to 106,696 unique customer tweets.

The number of unique customers associated with these interactions is 76,366.

The 106,696 figure represents unique customer tweets directly answered by AppleSupport and should not yet be treated as the definitive number of complete conversation threads.

## Conversation Reconstruction

A conversation ID was generated for each tweet by following the `in_response_to_tweet_id` relationships backward until the root tweet was reached.

Tweets sharing the same root tweet are treated as belonging to the same reconstructed conversation thread.

Cycle detection was included to prevent infinite traversal in case of malformed response relationships.

Initial analysis of five candidate brands produced:

| Brand | Threads | Customer Messages | Brand Responses |
|---|---:|---:|---:|
| AppleSupport | 80,702 | 131,764 | 106,860 |
| AmazonHelp | 82,534 | 203,598 | 169,840 |
| Uber_Support | 41,923 | 72,154 | 56,270 |
| SpotifyCares | 28,280 | 48,543 | 43,265 |
| Delta | 26,166 | 45,296 | 42,253 |

These are reconstructed response-chain threads and are not necessarily guaranteed to represent complete real-world support resolutions.

## Conversation Validation

Five reconstructed AppleSupport conversation threads were manually inspected.

The sampled conversations showed that tweets belonging to the same reconstructed conversation were contextually related. Chronological ordering was sensible, and customer and company roles followed the expected interaction pattern.

Based on this validation, the reconstructed conversation threads are considered suitable for subsequent exploratory analysis.

The reconstruction represents dataset-level response threads and should not automatically be interpreted as confirmed real-world issue resolution.