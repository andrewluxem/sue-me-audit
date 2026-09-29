# Checklist

Every check has a stable ID. IDs never change meaning and are never reused, so issues, pull requests, and reports can reference them. To retire a check, mark it `Retired` and leave the ID in place.

Evidence hints are starting points, not exhaustive search lists.

## PRIV: Privacy

### PRIV-01 Privacy policy missing or incomplete
Find the policy route or page. It must name the data collected, AI use (what is sent to model providers and why), and third parties (analytics, ads, email and SMS, payments, AI vendors). Cross-check against the third parties found in Step 0. Any vendor present in code but absent from the policy is a FAIL.

### PRIV-02 Pixels or trackers firing before consent
Look for Google tag / GTM, Meta Pixel, TikTok, LinkedIn Insight, Pinterest, Snap, Reddit, Hotjar, Microsoft Clarity, FullStory, Segment, PostHog, Mixpanel, Amplitude, onsite email or SMS SDKs, and platform analytics. Trace whether each loads unconditionally in the root layout, head, or theme, or waits for a consent state. Session replay and chat widgets count.

### PRIV-03 Cookie banner with no reject
If a banner exists, confirm a Reject or Decline option at the same level and prominence as Accept, and that rejecting actually blocks the scripts found in PRIV-02. A banner that only says "OK" is a FAIL.

### PRIV-04 Health data sent to analytics
Look for health, symptom, condition, medication, fitness, pregnancy, fertility, or mental-health fields or pages. FAIL if URLs, page titles, form values, or events containing them reach analytics or ad pixels.

### PRIV-05 Face or biometric data with no consent
Face detection or recognition libraries, liveness checks, face-matching APIs, voiceprints, fingerprints. Requires notice, explicit written consent before capture, and a published retention and destruction schedule.

### PRIV-06 Unencrypted personal data
Plaintext PII or passwords in schemas, logs, client storage, query strings, or non-TLS endpoints. Weak or missing password hashing. PII written to application logs.

### PRIV-07 Public storage buckets
S3, GCS, Azure Blob, Supabase Storage, Firebase rules, or platform blob stores set to public read or list for user data. Policies often live outside the repo: CAN'T TELL with instructions when that is the case.

### PRIV-08 Deleted uploads still stored
Trace the delete path for user uploads and accounts. Is the object removed from storage and CDN, or only the database row? A soft delete with no purge job is a FAIL.

## CONT: Content

### CONT-01 Unlicensed images
Inventory image sources: static folders, CMS, hotlinked URLs, scraped assets, stock-looking filenames, watermark-like names. Licenses live outside the repo, so this is usually CAN'T TELL with a short list of the highest-risk assets to verify.

### CONT-02 No report button or takedown route
Applies when there is user-generated content (comments, uploads, profiles, reviews, messages). Confirm a report or flag control in the UI and a backend path that records and queues it.

### CONT-03 No DMCA agent
Look for a copyright or DMCA page naming a designated agent and a notice process. Whether the agent is registered and current with the Copyright Office is CAN'T TELL.

### CONT-04 No age gate
Applies when content or products are age-restricted (gambling, alcohol, cannabis, tobacco, adult) or when the app may collect data from children under 13. Otherwise N/A with the reason stated.

### CONT-05 Missing alt text and basic accessibility
Missing or empty alt on meaningful images. Also flag the gaps accessibility demand letters commonly cite: unlabeled form inputs, icon-only buttons with no accessible name, no visible focus state, no skip link.

## SALE: Sales

### SALE-01 Fake testimonials or fake urgency
Hardcoded reviews or testimonials with no source, countdown timers that reset on reload, random "X people are viewing" or "only N left" values not tied to real data.

### SALE-02 Cancelling harder than signing up
Compare the signup flow to the cancel flow. Count steps. FAIL if signup is online but cancel requires chat, phone, email, or a retention maze with no direct path.

### SALE-03 Trials that charge with no reminder
Free-trial-to-paid logic in billing code. Confirm clear pre-charge disclosure at signup and a reminder before the first charge.

### SALE-04 Texts without opt-in
SMS sends through any provider. Confirm express written consent capture with disclosure language near the phone field, STOP and HELP handling, and quiet-hour logic. Stored consent records may be CAN'T TELL.

### SALE-05 Emails with no unsubscribe
Marketing templates and sends: a working unsubscribe link, one-click List-Unsubscribe headers, and a physical mailing address.

### SALE-06 Pricing based on user data with no label
Price or discount logic keyed to location, device, browsing history, or other personal data without disclosure to the user.

## AI: AI features

### AI-01 Unproven "AI-powered" claims
Marketing copy with "AI-powered", "AI-driven", "smart", "predictive", "guaranteed", or accuracy percentages. FAIL where the code shows no AI behind the claim, or the claim promises results the product cannot back up.

### AI-02 AI output with no label
Generated text, images, audio, or advice shown to users with no disclosure that it is AI-generated.

### AI-03 Chatbot with no self-harm response
Applies to any chat or free-text LLM surface. Check the system prompt and middleware for detection of self-harm or crisis language and a response that surfaces crisis resources. Missing is CRITICAL.

### AI-04 Acting as a therapist or other licensed professional
Prompts, personas, or copy that present the bot as a therapist, counselor, doctor, lawyer, or financial advisor, or that offer diagnosis or treatment.

### AI-05 Quoting prices and policies on its own
The model can state prices, refunds, discounts, or policy terms not grounded in a source of truth, with no disclaimer that the official policy governs.

## Proposing a new check

New checks get the next unused ID in their section. A proposal needs: the problem in one line, why it creates legal exposure (with a source link), what evidence in code proves PASS or FAIL, and when it is N/A. See CONTRIBUTING.md at the repository root.
