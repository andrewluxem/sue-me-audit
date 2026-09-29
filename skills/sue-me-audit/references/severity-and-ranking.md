# Severity and ranking

## Severity (per FAIL)

CRITICAL: statutory or per-violation damages, regulator exposure, or live data exposure. Typical examples: texting without consent, biometric capture without consent, trackers that share data before consent, public buckets holding personal data, health data sent to ad platforms, a chatbot with no self-harm handling.

HIGH: a common demand-letter or class-action target, or a clear consumer-protection problem. Typical examples: no cookie reject option, hard-to-cancel subscriptions, trials with no reminder, fake urgency or testimonials, missing unsubscribe, accessibility gaps across many pages.

LOW: real but unlikely to be pursued on its own, or easy to cure once someone complains. Typical examples: a policy missing one vendor, a few images with no alt text, an incomplete DMCA page.

Severity is about how bad it is if someone acts. Ranking is about how likely someone acts. Keep them separate.

## Ranking fails by likelihood of harm

Order every FAIL (and any CAN'T TELL that is probably a fail) using these factors, in this order:

1. Frequency: how often this exact issue draws demand letters, class actions, or regulator action.
2. Damages: statutory or per-violation damages outrank actual damages, because they make small cases worth filing.
3. Visibility: can an outsider detect it from the public site (a scraper, a browser extension, a test signup) without discovery? Visible issues get found first.
4. Scale: how many users or pages are affected.

Give one line of reasoning per ranked item.

## Fix order

The fix order is not always the ranking. Build it by:

1. Front-loading CRITICAL items and the top of the likelihood ranking.
2. Grouping fixes that touch the same files so they ship together.
3. Calling out quick wins (under an hour) separately from larger work.
4. Tagging each fix with effort: S (under an hour), M (under a day), L (more than a day).
