---
name: new-keywords
description: Find new keywords for one of my apps in ASOMap — store autocomplete suggestions and discovered keywords, with demand and difficulty, filtered to what the app can realistically win. Use when the person asks for keyword ideas, new keywords, long-tail keywords, keyword research for their app or a new country, "подобрать ключи", "новые ключевые слова", "какие ключи добавить".
---

# New keywords

Build a short list of keywords worth tracking for one app in one store and country, using only real store data.

## Steps

1. **Pick the app and the market.** `myApps` for the app (ask if unclear). The country is the one the person named, else the app's main storefront. RuStore is always `ru`.
2. **What is already tracked.** `listKeywords` for the store and country, so nothing already tracked is suggested again.
3. **Gather candidates** from three sources:
   - `opportunities` — winnable keywords (high demand, low competition) not tracked yet;
   - `discover` — keywords seen in the daily collection, ranked by demand;
   - `suggestKeywords` — the store's live autocomplete for 2–4 seed words. Take the seeds from the app's category and from its best tracked keywords; ask the person for seeds if the app is new.
4. **Filter.** Drop candidates that are already tracked, that are competitors' brand names, or that don't describe what the app does (read the app's listing with `appDetail` if you aren't sure what it does).

## What to write

Answer in the person's language. One table, at most 20 rows, best first:

| Keyword | Demand | Difficulty | Why it fits |

- Demand and difficulty come from the tools (0–100). If a source gives no demand, show "—", don't estimate.
- "Why it fits" is a few words: the feature it matches, or "long tail of «calorie counter»".
- Under the table, name the 3–5 you'd start with and why (demand worth it, difficulty the app can beat).

## Then

Offer to start tracking the chosen ones with `trackKeywords` (in the same store and country). It changes the workspace and counts against the plan's keyword limit, so ask first and add only what the person picks. Their positions appear after the next collection.
