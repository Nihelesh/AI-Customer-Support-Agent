Phase 4 — Clean & Prepare Conversations
Objective

Clean and prepare the AmazonHelp conversations so that they can be used as input for downstream intent classification and annotation.

The goal of this phase is to remove unnecessary noise while preserving information that may be useful for identifying the customer's intent.

1. Conversation Dataset

The processed dataset contains:

374,027 conversation turns
82,534 conversations
10 columns

Conversation-level analysis showed:

Conversation Length	Conversations	Percentage
1 turn	1	~0.00%
2 turns	31,292	37.91%
3 turns	11,570	14.02%
4 turns	14,013	16.98%
5+ turns	25,658	31.09%

The average conversation length is approximately 4.53 turns.

2. Conversation Structure

The dataset contains both customer messages and AmazonHelp responses.

Message Type	Count
Customer messages	203,583
AmazonHelp responses	170,444

The conversations contain AmazonHelp responses in essentially all identified conversations.

This confirms that the dataset represents two-sided customer-support interactions, rather than isolated customer messages.

3. Text Cleaning

A text-cleaning process was implemented to prepare conversation text for NLP processing.

The cleaning process includes:

Removing URLs
Preserving user mentions
Removing unnecessary whitespace
Replacing newline characters with spaces
Removing leading and trailing whitespace
Removing unnecessary textual noise where appropriate
Important Decision — User Mentions

User mentions were not removed completely.

Mentions were retained because they may provide useful conversational context and their presence does not inherently prevent NLP/AI models from learning the underlying intent.

4. Language Detection

Language detection was performed on the cleaned conversation text.

The detected language distribution included:

Language	Conversations
English (en)	7,523
Japanese (ja)	541
Spanish (es)	513
French (fr)	469
German (de)	276
Portuguese (pt)	182
Hungarian (hu)	148
Italian (it)	117
Dutch (nl)	94
Turkish (tr)	21
Filipino (tl)	16
Unknown	10
Other detected languages	Remaining conversations

The dataset therefore contains conversations in multiple languages rather than English only.

5. Language Detection Optimization

Because full conversations can contain several turns and may be computationally expensive to process, language detection was optimized by examining only the initial portion of the conversation text.

The purpose is to reduce processing time while still obtaining sufficient information to determine the likely language of the conversation.

This optimization was considered because the dataset contains tens of thousands of conversations.

6. Non-English Conversations

Language detection showed that the dataset contains a substantial number of conversations that are not English.

These conversations were identified rather than silently treating all text as English.

The language information can subsequently be used to:

Filter conversations for an English-only model
Create separate multilingual datasets
Analyze language distribution
Prevent incorrect assumptions during NLP preprocessing

No decision was made to simply discard all non-English conversations at this stage.

7. Complete Conversation Preservation

For downstream intent classification, the complete conversation should be preserved in the prepared dataset.

The conversation should not be represented only by the first customer message because later turns can provide important information about the actual customer issue.

For example, a customer may initially describe a problem vaguely and provide the actual issue in a later turn.

Therefore, the prepared conversation representation should retain:

Customer → AmazonHelp → Customer → AmazonHelp → ...

rather than extracting only the first message.

8. Preparation for Intent Annotation

After cleaning and language detection, conversations are prepared for the next stage of the pipeline.

The prepared data will contain conversation text that is:

Normalized
Free from unnecessary URLs
Free from excessive whitespace
Preserved as a complete conversation
Associated with detected language information
Suitable for candidate-intent generation and manual annotation
Phase 4 Output

The output of Phase 4 is a cleaned and prepared conversation dataset that can be used for subsequent intent annotation and gold-label creation.

The overall processing flow is:

Raw Conversations

→ Conversation Grouping

→ Text Cleaning

→ Language Detection

→ Language Information Added

→ Complete Conversation Preserved

→ Clean Prepared Conversations

→ Next Phase: Annotation / Gold Dataset Creation