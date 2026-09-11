# Phase 4 — Data Cleaning and Conversation Preparation

## 1. Objective

The objective of Phase 4 was to clean and prepare the selected AmazonHelp customer-support conversations for downstream intent definition, evaluation, and AI-agent development.

The preparation focused on:

* Converting timestamps into a usable datetime format
* Establishing chronological conversation order
* Creating turn numbers
* Inspecting text artifacts
* Defining conservative text-cleaning rules
* Creating a cleaned text field
* Removing records that contained no usable text after cleaning
* Validating the resulting dataset

The goal was to preserve the original conversational meaning while removing unnecessary formatting and anonymized identifiers.

---

## 2. Input Dataset

The selected dataset contains conversations involving the AmazonHelp support account.

Before text preparation:

* Tweets: 374,042
* Conversations: 82,534
* Inbound tweets: 203,598
* Outbound tweets: 170,444

The dataset contains customer messages, AmazonHelp responses, and a small number of other support-account responses that participate in some conversation threads.

---

## 3. Timestamp Preparation

The `created_at` column was originally stored as text.

It was converted into a timezone-aware datetime representation using UTC.

Resulting datatype:

```text
datetime64[ns, UTC]
```

This allows tweets to be reliably ordered chronologically within each conversation.

---

## 4. Chronological Conversation Ordering

Tweets were sorted using:

1. `conversation_id`
2. `created_at`

This ensures that messages within each conversation appear in chronological order.

Example:

```text
Turn 1 → Customer
Turn 2 → AmazonHelp
Turn 3 → Customer
Turn 4 → AmazonHelp
```

Sample conversations were manually inspected to verify that the reconstructed order was sensible.

---

## 5. Turn Number Generation

A `turn_number` column was created using the conversation ID as the grouping key.

Each conversation starts from:

```text
turn_number = 1
```

Validation showed:

```text
turn_number
1    82,534
```

This confirms that all 82,534 conversations have a valid first turn.

---

## 6. Text Quality Inspection

The following text artifacts were investigated before cleaning.

| Artifact                   |   Count |
| -------------------------- | ------: |
| Tweets containing URLs     | 102,691 |
| Tweets containing mentions | 362,685 |
| Tweets containing newlines |  21,632 |
| Missing text               |       0 |
| Empty text                 |       0 |

The inspection also identified multilingual content, including Japanese conversations.

The cleaning strategy was therefore designed to be language-agnostic and conservative.

---

## 7. Text Cleaning Strategy

A new `clean_text` column was created rather than modifying the original `text` column.

This preserves the original dataset for reproducibility and debugging.

### Cleaning rules

| Element                                              | Action                 |
| ---------------------------------------------------- | ---------------------- |
| Standard URLs                                        | Removed                |
| Numeric user mentions such as `@115821`              | Replaced with `[USER]` |
| Known support-account mentions such as `@AmazonHelp` | Preserved              |
| Newline characters                                   | Replaced with spaces   |
| Excessive whitespace                                 | Normalized             |
| Punctuation                                          | Preserved              |
| Emojis                                               | Preserved              |
| Numbers                                              | Preserved              |
| Original text                                        | Preserved              |
| Non-English text                                     | Preserved              |
| Stopwords                                            | Preserved              |

The objective was to remove obvious noise without destroying information that could be useful for customer-support intent understanding.

---

## 8. Handling User Mentions

The dataset contains anonymized customer identifiers represented as numeric Twitter mentions, for example:

```text
@115770
@115821
@115850
```

These identifiers do not provide meaningful semantic information for the support task.

Therefore, numeric mentions were normalized to:

```text
[USER]
```

Example:

```text
@115821 Order has not arrived
```

becomes:

```text
[USER] Order has not arrived
```

Support-account mentions were preserved.

For example:

```text
@AmazonHelp My order hasn't arrived
```

remains:

```text
@AmazonHelp My order hasn't arrived
```

---

## 9. Handling URLs

Standard URLs were removed because the destination of shortened support links is generally not required for the initial intent-understanding task.

For example:

```text
Please check this link https://t.co/example
```

becomes:

```text
Please check this link
```

URL-only tweets require special handling because removing the URL leaves no usable textual content.

---

## 10. URL-Only Tweets

After cleaning, 15 tweets contained no remaining textual content.

Inspection showed that these records consisted only of URL content.

These 15 records were removed because they contain no usable text for intent understanding.

The removal was validated against conversation counts.

Before removal:

```text
82,534 conversations
```

After removal:

```text
82,534 conversations
```

Therefore, no conversation was lost as a result of this filtering step.

---

## 11. Cleaning Validation

The cleaning pipeline was validated using the following checks:

### Numeric mentions

```text
Numeric mentions remaining: 0
```

### Newlines

```text
Newlines remaining: 0
```

### Empty cleaned tweets

The initial validation identified 15 URL-only tweets. These were removed.

Final cleaned dataset:

```text
Empty cleaned tweets: 0
```

### Conversation preservation

```text
Conversations before: 82,534
Conversations after: 82,534
```

This confirms that the cleaning process preserved the complete conversation set.

---

## 12. Final Dataset

After Phase 4 cleaning:

| Metric               | Final value |
| -------------------- | ----------: |
| Tweets               |     374,027 |
| Conversations        |      82,534 |
| Inbound tweets       |     203,598 |
| Outbound tweets      |     170,429 |
| Empty cleaned tweets |           0 |
| Lost conversations   |           0 |

The resulting dataset contains a cleaned conversational representation suitable for the next phase.

---

## 13. Important Design Decisions

The following decisions were intentionally made during preprocessing:

### Preserve the original text

The original `text` column was not overwritten.

This allows the preprocessing process to be inspected and reproduced later.

### Conservative preprocessing

Aggressive NLP preprocessing such as stopword removal, stemming, lemmatization, translation, and punctuation removal was not applied.

This was intentional because customer-support conversations contain contextual information that could be lost through aggressive preprocessing.

### Language preservation

Non-English conversations were retained in their original language.

Translation was not performed during this phase.

### Conversation preservation

The cleaning process was validated at the conversation level, not only at the tweet level.

This ensured that removing unusable tweets did not accidentally remove complete conversation threads.

---

## 14. Phase 4 Outcome

Phase 4 successfully produced a cleaned and chronologically ordered AmazonHelp conversation dataset.

The final dataset contains:

```text
374,027 tweets
82,534 conversations
```

with:

* reliable timestamps
* conversation IDs
* chronological ordering
* turn numbers
* original tweet text
* cleaned tweet text

The dataset is now ready for **Phase 5 — Intent Definition**.
