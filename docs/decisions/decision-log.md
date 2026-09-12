# Decision Log

## Decision — Project Language

**Decision:** Python

**Reason:** The project involves data processing, machine learning, LLM integration and evaluation, for which Python provides a suitable ecosystem.

---

## Decision — Repository Structure

**Decision:** Separate source code, data, evaluation, tests and documentation.

**Reason:** To keep the project organized and maintainable.

## Decision: Freeze Customer Support Intent Taxonomy

### Decision

Use a hierarchical taxonomy containing 10 intent families and 50 leaf intents for the AmazonHelp support agent.

Each conversation receives one primary intent.

### Why

Manual exploration revealed a wide range of customer-support issues. A taxonomy with too few categories would combine substantially different customer goals, while an excessively granular taxonomy would make classification and evaluation unnecessarily difficult.

The candidate taxonomy was tested on 50 previously unseen conversations, and all sampled conversations could be assigned to an existing intent.

### Alternatives Considered

- Very broad intent categories
- Highly granular intent categories
- Multi-label intent classification

### Rationale

The selected taxonomy provides a practical balance between specificity and implementation complexity for the project.

### Consequence

The taxonomy will remain fixed during the initial baseline, agent, and evaluation phases unless later analysis provides strong evidence that a taxonomy change is necessary.

## Decision: Primary Intent Should Represent the Underlying Customer Support Issue

### Context

Some conversations contain both an identifiable customer support issue and a positive or negative reaction to the support received.

For example:

- Customer initially reports that a $50 gift card was unusable.
- AmazonHelp provides support and escalates the issue.
- The balance is restored.
- Customer then says: "great service!!!"

The final message expresses appreciation, but appreciation was not the reason the customer originally contacted Amazon.

### Decision

The gold intent will represent the **underlying customer support issue that initiated the conversation**, rather than the customer's final emotional reaction or outcome.

Therefore, in the example above, the conversation should be labeled:

`CHARGE_PROBLEM`

rather than:

`APPRECIATION`

### Annotation Rule

When an identifiable support issue initiated the conversation, label the conversation according to that underlying issue, even if the customer later expresses appreciation after the issue is resolved.

`APPRECIATION` should be used when appreciation itself is the primary purpose of the conversation and there is no identifiable underlying support issue.

### Rationale

The objective of the intent classification system is to identify **what the customer needed help with**, rather than simply classifying the customer's final statement.

This rule is particularly important for multi-turn conversations because the final turn may describe the **outcome of the support interaction** rather than the **reason the customer contacted Amazon**.

### Impact

This decision will be applied consistently while annotating the 200-conversation golden evaluation set and will be used when evaluating the AI support agent's intent classification.