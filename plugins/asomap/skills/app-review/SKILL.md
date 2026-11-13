---
name: app-review
description: Review one of my apps in ASOMap — what dropped, what is close to the top 10, which valuable keywords are missing from the title and description, and what to do first. Use when the person asks how their app is doing in the stores, for an ASO review or audit of their app, "разбор приложения", "что с моими позициями", "как дела у приложения".
---

# Review my app

A short, decision-ready review of one of the person's apps, built only from their ASOMap data.

## Steps

1. **Pick the app.** Call `myApps`. If there is one app, use it. If there are several and the person didn't name one, list them (title, store) and ask which; don't guess.
2. **Check the data is fresh.** Call `status` for the app's store. If the last collection is older than two days, say so at the top: the review describes that date.
3. **Overall picture.** Call `asoSummary`, then for the app's store and its main country call:
   - `movers` with `window: "week"` — what climbed and what dropped;
   - `recommendations` — missing high-demand keywords, near-top-10 keywords, recent drops;
   - `metadataCheck` — which tracked keywords are in the title and description, and its `policy` list: store rules the live listing breaks (report every `error`);
   - `intentVisibility` — tracked keywords by query type (function, problem, format, object, brand, condition) and how many of each are in the top 10 against a month ago. Name the type the app is weakest in where it has demand: problem, format and object queries usually bring the most installs.
4. **If the app has competitors** (`listCompetitors`), call `competitorGaps` and keep the three biggest gaps.

## What to write

Answer in the person's language. Keep it to one screen:

- **The state in one line** — e.g. "12 of 80 keywords in the top 10, 5 dropped this week".
- **Dropped this week** — the keywords with the biggest falls, with old → new position. Only real drops; skip keywords that are not ranked at all.
- **Close to the top 10** — positions 11–20 with good demand: the cheapest wins.
- **Missing from the metadata** — high-demand tracked keywords that are not in the title (App Store: name, subtitle, keyword field; Google Play and RuStore: title, short and full description).
- **Competitors ahead** — up to three keywords where a competitor clearly outranks the app.
- **Do first** — three concrete actions, most impact first (for example "add «meal planner» to the subtitle").

Use numbers from the tools; never invent positions, demand or downloads. If a section has nothing in it, leave it out rather than padding it.

## Next steps to offer

- Write a new listing for these keywords → the `listing-for-keywords` workflow.
- Look closer at one competitor → the `beat-a-competitor` workflow.
- Find new keywords → the `new-keywords` workflow.
