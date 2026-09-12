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