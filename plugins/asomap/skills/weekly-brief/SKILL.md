---
name: weekly-brief
description: A short weekly ASO brief across all my apps in ASOMap — rank distribution, the week's biggest climbs and drops, new opportunities and one thing to do. Use when the person asks for a weekly report, summary, digest or status of their apps' rankings, something to share with the team, "еженедельный отчёт", "сводка за неделю", "что изменилось за неделю".
---

# Weekly brief

A brief the person can read in a minute or paste into a team chat.

## Steps

1. **Freshness.** For each store the person's apps are in, call `status`. Mention any store whose data is older than two days.
2. **Across all apps:** `asoSummary` — per store, the app, how many keywords are in the top 10, top 50, beyond, not ranked.
3. **Per store and main country:**
   - `movers` with `window: "week"` — the biggest climbs and drops;
   - `opportunities` with `limit: 5` — new winnable keywords not tracked yet.
4. **New reviews worth a look:** `listReviews` for each app with `maxRating: 2` and `limit: 10`; keep only reviews from the last week.

## What to write

Answer in the person's language. Plain text that pastes well into a chat (no wide tables):

```
ASO brief, <date range>

<App> · <store>
Top 10: N (±n vs last week) · Top 50: N · Not ranked: N
▲ <keyword> 18 → 7 · <keyword> 25 → 14
▼ <keyword> 4 → 12
New chances: <keyword>, <keyword>
Low reviews: 2 this week — "<short quote>"

Do this week: <one action>
```

- One block per app and store; skip stores where nothing moved.
- Positions and counts come from the tools; if the week-ago number isn't available, leave out the "±".
- "Do this week" is one concrete action for the whole portfolio, the one with the most impact.
