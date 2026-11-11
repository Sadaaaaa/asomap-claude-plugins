---
name: reply-to-reviews
description: Answer the unanswered store reviews of one of my apps through ASOMap — read the inbox, draft a reply to each in the reviewer's language, and publish only the ones the person approves. Use when the person asks to reply to reviews, answer negative reviews, clear the review inbox, "ответить на отзывы", "разобрать отзывы", "ответы на негатив".
---

# Reply to reviews

Clear the app's review inbox with replies the person approved, one by one. A reply is public: everyone in the store sees it under the review.

## Steps

1. **Pick the app.** `myApps` (ask if there are several and none was named).
2. **Open the inbox.** `reviewInbox` with `status: "unreplied"`; start with `ratings: "1,2"` unless the person asked otherwise.
   - `connected: false`: the store's developer key isn't connected. Say that the workspace owner connects it on ASOMap's Reviews page (App Store: an App Store Connect key with the Customer Support role; Google Play: a service account with "Reply to reviews"; RuStore: an API key with the reviews methods) and stop.
   - `viaApi: false`: connected but not read yet; call `syncReviews`, then `reviewInbox` again.
3. **Group them.** Reviews often repeat one problem (a crash in a version, a price complaint). Name the groups and how many reviews each has before drafting.
4. **Draft.** One reply per review, in the review's language:
   - thank them, answer the actual point, 2–4 sentences, no marketing;
   - a bug: acknowledge it, and say it's fixed only if the person told you it is;
   - never promise dates or features you don't know about; no made-up support addresses;
   - don't paste the same text everywhere: reviewers and the store notice.
5. **Show the drafts and ask.** A short table: stars, the review's gist, your draft. Ask which to send as they are, which to change, which to skip. Wait for a clear answer.
6. **Send only what was approved,** with `replyToReview` and the exact approved text. Report what went out. The App Store and RuStore show a reply after their own check (`PENDING_PUBLISH` / `MODERATION`, then `PUBLISHED`; RuStore may answer `REJECTED`); Google Play publishes at once.

Store limits: App Store 5970 characters, Google Play 350, RuStore 500. Google Play's API only has the last week's reviews, so older Play reviews in the inbox can't be answered from here.

Never call `replyToReview` for a draft the person hasn't approved in this conversation, and never send more than they approved.

## What to write

Answer in the person's language: the groups found, then the drafts table, then the question. After sending: how many went out, and what's left in the inbox.
