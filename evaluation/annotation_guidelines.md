# Golden Set Annotation Guidelines

## Objective

Assign one primary intent to each complete AmazonHelp conversation.

## Annotation Unit

One complete conversation identified by conversation_id.

## Primary Intent Rule

Select the intent that best represents the customer's primary problem or request after reading the complete conversation.

Primary intent should represent the customer's underlying support need/problem that initiated the conversation. Positive or negative reactions to the support experience should not replace the underlying issue when that issue can be clearly identified.

## Candidate Intent

candidate_intent represents the preliminary automatically assigned intent and must not be treated as the final label.

## Gold Intent

gold_intent is the final human-assigned label.

## Label Reason

Provide a short explanation supporting the selected gold intent.

## Difficulty

- EASY: Intent is clear.
- MEDIUM: Some ambiguity exists but one intent is preferred.
- HARD: Multiple intents are genuinely difficult to distinguish.

## Multiple Issues

When a conversation contains multiple issues, select the single primary customer intent.

## Annotation Principle

Read the complete conversation before assigning the label.