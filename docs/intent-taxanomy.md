# Intent Taxonomy

## 1. Purpose

This document defines the customer-support intent taxonomy used for the AmazonHelp customer-support AI agent.

The taxonomy was created through manual exploration of reconstructed customer-support conversations from the TWCS dataset.

The goal is to provide a practical and interpretable set of intents that can be used for intent classification, retrieval, response generation, and evaluation.

---

## 2. Taxonomy Design 

|  # | Intent                                      |
| -: | ------------------------------------------- |
|  1 | Billing / Subscription                      |
|  2 | App / Device Technical Issues               |
|  3 | Playback Bugs                               |
|  4 | Content Availability / Catalog Gaps         |
|  5 | Playlist Management                         |
|  6 | Login / Account Access                      |
|  7 | Ads                                         |
|  8 | Student Discount / Eligibility Verification |
|  9 | Feature Requests / Product Feedback         |
| 10 | Offline / Downloads / Storage               |
| 11 | Regional Availability                       |
| 12 | Positive Feedback / Praise                  |
| 13 | Support-Process Complaints                  |
| 14 | Third-party / Platform Integration          |
| 15 | Account Security / Hacking                  |
| 16 | Payment / Card Errors                       |
| 17 | Gift Cards / Redemption Codes               |
| 18 | Other / Uncategorised                       |



1. BILLING_OR_SUBSCRIPTION

Definition:
Questions or problems related to a Spotify subscription, Premium plan, billing cycle, renewal, cancellation, or subscription status.

Include:

Premium subscription problems
Subscription cancellation
Subscription renewal
Questions about subscription charges
Premium plan status
Switching subscription plans

Exclude:

Card/payment method failing → PAYMENT_CARD_ERRORS
Student Premium → STUDENT_DISCOUNT_OR_ELIGIBILITY
Gift card/voucher → GIFT_CARDS_REDEMPTION_CODES

Example:

"Why did my Premium subscription renew?"

2. APP_OR_DEVICE_TECHNICAL_ISSUES

Definition:
Technical problems involving the Spotify application or the device running Spotify, where the primary issue is the app/device rather than playback itself.

Include:

App crashes
App won't open
App errors
Spotify not working on a particular device
Device compatibility problems

Exclude:

Music specifically won't play → PLAYBACK_BUGS
Download/offline issue → OFFLINE_DOWNLOADS_OR_STORAGE
Connecting Spotify to another platform/device → THIRD_PARTY_PLATFORM_INTEGRATION

Example:

"Spotify keeps crashing on my phone."

3. PLAYBACK_BUGS

Definition:
Problems occurring while attempting to play music/audio.

Include:

Songs won't play
Music stops unexpectedly
Playback pauses
Buffering
Audio playback errors
Songs skipping

Exclude:

Can't download songs → OFFLINE_DOWNLOADS_OR_STORAGE
Song doesn't exist in Spotify → CONTENT_AVAILABILITY_OR_CATALOG_GAPS

Example:

"My songs keep stopping after a few seconds."

4. CONTENT_AVAILABILITY_OR_CATALOG_GAPS

Definition:
Questions or complaints about music, albums, artists, podcasts, or other content being missing, unavailable, or incorrectly represented in Spotify's catalog.

Include:

Missing songs
Missing albums
Missing artists
Request for unavailable music
Removed content
Catalog discrepancies

Exclude:

Country-specific availability → REGIONAL_AVAILABILITY
Playback failure → PLAYBACK_BUGS

Example:

"Why isn't this album available on Spotify?"

5. PLAYLIST_MANAGEMENT

Definition:
Problems or requests specifically involving playlists.

Include:

Creating playlists
Editing playlists
Deleting playlists
Missing playlists
Recovering playlists
Adding/removing songs from playlists

Example:

"My playlist disappeared. How can I recover it?"

6. LOGIN_OR_ACCOUNT_ACCESS

Definition:
Problems accessing or logging into a Spotify account.

Include:

Can't log in
Forgot password
Login problems
Can't access account
Account access problems

Exclude:

Account hacked → ACCOUNT_SECURITY_OR_HACKING
General subscription problem → BILLING_OR_SUBSCRIPTION

Example:

"I can't log into my Spotify account."

7. ADS

Definition:
Questions, complaints, or feedback specifically about advertisements displayed during Spotify usage.

Include:

Too many ads
Ads playing frequently
Ad-related complaints
Questions about advertisements

Example:

"Why am I getting so many ads?"

8. STUDENT_DISCOUNT_OR_ELIGIBILITY

Definition:
Issues concerning Spotify's student plan, student discount, or student eligibility/verification.

Include:

Student discount
Student Premium
Student verification
Eligibility problems
University/student status

Example:

"Why can't I verify my student status?"

9. FEATURE_REQUESTS_OR_PRODUCT_FEEDBACK

Definition:
Suggestions, requests, or feedback about Spotify's product or features.

Include:

Requests for new features
Suggestions for improvements
Feature ideas
Product feedback
Requests to change how Spotify works

Example:

"Spotify should add a feature to show lyrics while playing."

Important:
A complaint about customer support is not this intent. That belongs to SUPPORT_PROCESS_COMPLAINTS.

10. OFFLINE_DOWNLOADS_OR_STORAGE

Definition:
Problems or questions involving downloading music, offline listening, or Spotify's storage usage.

Include:

Download failures
Offline mode
Downloaded songs unavailable offline
Storage problems caused by Spotify
Managing downloaded content

Example:

"My downloaded songs aren't available offline."

11. REGIONAL_AVAILABILITY

Definition:
Problems caused by country, region, location, or geographical availability restrictions.

Include:

Spotify unavailable in a country
Content unavailable in a particular country
Country restrictions
Region-specific features
Moving to another country

Example:

"Why isn't Spotify available in my country?"

Key distinction

If the customer says:

"This song isn't available in my country."

→ REGIONAL_AVAILABILITY

If they say:

"This song isn't available on Spotify."

→ CONTENT_AVAILABILITY_OR_CATALOG_GAPS

12. POSITIVE_FEEDBACK_OR_PRAISE

Definition:
Purely positive customer feedback without a support problem or request requiring resolution.

Include:

Compliments
Praise
Thank-you messages
Positive comments about Spotify

Example:

"Spotify is amazing! I love the new update."

Important:
If the message contains both praise and a problem, classify according to the problem/request, not this intent.

13. SUPPORT_PROCESS_COMPLAINTS

Definition:
Complaints about Spotify's customer-support process or service experience.

Include:

Poor customer service
Slow support
Support not responding
Repeated automated responses
Complaints about support handling
Frustration with support representatives/process

Example:

"I've contacted support three times and nobody has helped me."

14. THIRD_PARTY_PLATFORM_INTEGRATION

Definition:
Problems involving Spotify's connection or integration with another application, platform, service, or external device.

Include:

Spotify + Facebook
Spotify + PlayStation/Xbox
Spotify + Google/Alexa
Spotify + another application
Connecting Spotify to external services
Third-party integration problems

Example:

"I can't connect Spotify to my PlayStation."

15. ACCOUNT_SECURITY_OR_HACKING

Definition:
Problems involving unauthorized access, hacking, compromised accounts, or suspicious account activity.

Include:

Account hacked
Someone accessed account
Unauthorized account activity
Suspicious login
Password changed by someone else
Unknown activity

Exclude:

Simply can't log in → LOGIN_OR_ACCOUNT_ACCESS

Example:

"Someone hacked my Spotify account and changed my password."

16. PAYMENT_CARD_ERRORS

Definition:
Problems specifically involving a payment method or payment transaction failure.

Include:

Credit/debit card declined
Card not accepted
Payment failed
Payment method error
Can't complete payment

Exclude:

Why was I charged? → BILLING_OR_SUBSCRIPTION
Student payment/discount → STUDENT_DISCOUNT_OR_ELIGIBILITY
Gift card → GIFT_CARDS_REDEMPTION_CODES

Example:

"My credit card keeps getting declined when I try to pay."

17. GIFT_CARDS_REDEMPTION_CODES

Definition:
Problems involving Spotify gift cards, vouchers, promotional codes, or redemption codes.

Include:

Gift card not working
Voucher problems
Redemption code errors
Can't redeem a code
Gift card balance

Example:

"My Spotify gift card code isn't working."

18. OTHER_OR_UNCATEGORISED

This should be your fallback only.

Use it when:

The conversation genuinely cannot be mapped to any of the 17 defined intents.

Do not use it just because you're uncertain.

If you find yourself using OTHER frequently, that is evidence that the taxonomy needs another intent or that an existing definition needs improvement.