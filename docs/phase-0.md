# Phase 0 — Understand + Plan

## Objective

Understand the project requirements, define the overall problem, establish the project roadmap, and decide how the customer-support AI system will be developed and evaluated.

---

## 1. Problem Understanding

The project focuses on building an AI-based customer support system using real customer-support conversations.

The system should be able to understand the customer's issue from the context of a conversation and identify the appropriate customer-support intent.

The project is designed around complete conversations rather than isolated tweets/messages because the issue may become clearer as the conversation progresses.

---

## 2. Conversation-Level Approach

A key decision was made to work at the **conversation level** rather than treating individual tweets independently.

The conversation reconstruction process showed that:

- Tweets belonging to the same conversation are related.
- The chronological order of messages is meaningful.
- Customer and company responses generally alternate as expected.
- Conversations commonly contain multiple turns.
- A conversation may continue across several customer and company responses.
- The conversation should be considered as a complete context when determining the customer's issue.

This is important because the customer's initial message does not always completely describe the actual issue. Later messages can clarify or change the understanding of the problem.

---

## 3. Primary Problem Definition

The initial problem was framed as:

> Given a customer-support conversation, understand the conversation context and identify the customer's primary support issue.

The focus is therefore on **context-aware intent identification** rather than simple keyword matching.

For example, a customer may mention several things during a conversation, but the annotation should identify the underlying primary issue rather than automatically selecting an intent based on a single word.

---

## 4. Intent Annotation Principle

A primary annotation principle was established:

> **Identify the underlying customer issue rather than simply selecting an intent based on a keyword or secondary statement.**

For example:

- A customer may complain about poor customer service while the underlying issue is a payment failure.
- A customer may mention a cancelled order while the actual problem is an unexpected charge.
- A customer may praise AmazonHelp after an issue has been resolved, while the original issue remains the primary intent.
- A customer asking whether an offer is valid is different from a customer reporting that a promotional code does not work.

This principle will be used during the creation of the golden evaluation set.

---

## 5. Project Roadmap

The project was divided into the following phases:

| Phase | Goal |
|---|---|
| Phase 0 | Understand + plan |
| Phase 1 | GitHub repository + project skeleton |
| Phase 2 | Obtain + understand dataset |
| Phase 3 | Explore brands + select one |
| Phase 4 | Clean + prepare conversations |
| Phase 5 | Define intents |
| Phase 6 | Build golden evaluation set |
| Phase 7 | Build baselines |
| Phase 8 | Build support AI agent |
| Phase 9 | Build evaluation harness |
| Phase 10 | Failure analysis |
| Phase 11 | Improve system |
| Phase 12 | Final experiments + results |
| Phase 13 | Report + decision log |
| Phase 14 | GitHub cleanup + final submission |

The project will be developed incrementally, with important decisions documented instead of making major architectural or modelling decisions upfront.

---

## 6. Evaluation-First Direction

The project will establish a manually annotated **golden evaluation set** before evaluating the final AI system.

The purpose is to create a trusted set of conversations with manually assigned intents so that different approaches can be compared against the same reference labels.

The planned golden set will contain representative conversations across the defined intent categories, including difficult and ambiguous cases.

---

## 7. Decision-Making Approach

The project will follow a decision-driven workflow.

Important decisions will be documented in `decision-log.md`, including:

- Why a particular approach was selected.
- Why alternative approaches were not selected.
- How ambiguous conversations are classified.
- How difficult/boundary cases are handled.
- Any changes made to earlier decisions.

The goal is to make the development process reproducible and explainable.

---

## 8. Development Philosophy

The project will be developed incrementally through the defined phases.

The major decisions will be made based on observations from the dataset and evaluation results rather than assumptions.

The workflow will therefore be:

**Understand → Explore → Prepare → Annotate → Establish Baselines → Build Agent → Evaluate → Analyze Failures → Improve → Final Evaluation**

---

## Phase 0 Completion Status

**Status: COMPLETED**

The project problem was understood, the conversation-level approach was established, the primary intent-classification objective was defined, the annotation principle was established, the evaluation-first direction was planned, and the complete project roadmap was defined.

The project can therefore proceed to **Phase 1 and the subsequent dataset-driven phases according to the roadmap**.