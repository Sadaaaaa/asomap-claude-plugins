---
name: listing-for-keywords
description: Write a store listing (title, subtitle or short description, keyword field, description) for one of my apps that covers its tracked keywords within each store's limits, score it against the current one in ASOMap and save it as a draft. Use when the person asks to write, rewrite or optimize their listing, title, subtitle, description or keyword field, "написать листинг", "переписать описание", "оптимизировать название".
---

# Listing for my keywords

Write a listing that covers the app's most valuable tracked keywords, prove it scores better than the current one, and save it where the person can copy it from.

## Steps

1. **Pick the app and locale.** `myApps` for the app (ask if unclear); the locale is the storefront the person named, else the app's main one.
2. **Read what's there.**
   - `getListingDraft` — a draft the person may already be working on;
   - `appDetail` — the live listing;
   - `listKeywords` — tracked keywords with demand and opportunity;
   - `scoreListing` with no text fields — the current score, the gaps and the dead weight.
3. **Write.** Respect each store's fields and limits:
   - **App Store:** name ≤ 30, subtitle ≤ 30, keyword field ≤ 100 (comma-separated, no spaces, no words already in the name or subtitle, no plurals of words already there), promotional text ≤ 170. The description isn't indexed: write it for people.
   - **Google Play:** title ≤ 30, short description ≤ 80, full description ≤ 4000. All three are indexed; use the main keywords naturally in the description, no keyword stuffing.
   - **RuStore:** title ≤ 50, short description ≤ 80, full description ≤ 4000, indexed like Google Play.

   Put the highest-opportunity keywords in the strongest fields (name, then subtitle or short description). Keep the brand name. Write in the listing's language, in a voice that reads well to a person.
4. **Prove it.** Call `scoreListing` with the new fields. If the score isn't higher than the current one, revise once and score again. Show both numbers.
5. **Save.** Ask before saving, then `saveListingDraft` with the new fields. It appears in ASOMap's Listing helper for this app and locale, ready to copy into the store console. It doesn't publish anything to the store.

## What to write

Answer in the person's language:

- The new listing, field by field, with each field's length against its limit.
- Score: current → new, and which important keywords are now covered.
- Anything you chose to leave out and why (for example a keyword that didn't fit the subtitle).
