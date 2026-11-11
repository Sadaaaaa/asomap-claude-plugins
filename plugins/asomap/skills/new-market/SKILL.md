---
name: new-market
description: Pick the next countries for one of my apps in ASOMap — check the app's main keywords across many App Store or Google Play storefronts at once, see where it already ranks and where demand is, and say which markets deserve a translated listing first. Use when the person asks about expanding to new countries, localization priorities, which markets or languages to translate into, international ASO, "выход на новый рынок", "в какие страны переводить", "где ещё ранжируется".
---

# New market

Find the countries where the app's keywords already work or have demand, and rank them so the person knows which listing to translate first. Only real store data: positions and demand come from the tools.

## Steps

1. **Pick the app.** `myApps` (ask if unclear). App Store and Google Play only: RuStore has one country.
2. **Where it is today (App Store).** `geoCheck` for the app: the storefronts it's on sale in, grouped by listing. Countries in the `base` group show the untranslated listing — those are the first candidates. Pass `vsAppId` for the main competitor to see where they sell and which markets they bothered to translate. Countries in `notOnSaleIn` need the app made available in App Store Connect before anything else. If `pending` is true, the first check is still running; go on with the next steps and look again at the end.
3. **Pick 3–5 keywords to test.** `listKeywords` for the app's main storefront (the first page is sorted by opportunity). Take the best ones that describe what the app does, not the brand name. If the person named keywords, use theirs.
4. **Pick the countries.** The ones the person named, else leave `countries` out for the ten big storefronts. Skip countries the app already tracks keywords in (`listKeywords` with country `ALL` shows them), unless the person wants them in the comparison.
5. **Check each keyword:** `keywordAcrossCountries` with the app, the keyword and the countries. A keyword is searched in the language people use there: for a non-English market, also check the local word when you know it (e.g. "kalorienzähler" for de), and say which word you checked.
6. **Look at who wins there.** For the 2–3 best markets, the `top3` field shows the leaders; call `appDetail` on one only if the person wants to see their listing.

Respect the store: each call runs live searches. Don't check more than about 5 keywords × 15 countries in one go; if a country comes back with an `error`, say so rather than retrying in a loop.

## How to rank the markets

- **Not on sale there**: say so; it's a one-click fix in App Store Connect, then a market like any other.
- **Already ranks, no local listing** (position in the top 100 on an English listing): the cheapest win — a translation should lift it.
- **High demand, not ranked, weak top 3** (small apps, low ratings in `top3`): worth a translated listing.
- **High demand, strong top 3**: possible, but needs more than a translation.
- **Low or no demand**: skip for now.

## What to write

Answer in the person's language.

| Country | Listing there | Keyword | Position | Demand | Top 3 | Verdict |

- One row per country (the best keyword for it), best markets first.
- "Listing there": translated, base (untranslated) or not on sale, from `geoCheck` (App Store); "—" for Google Play.
- Position "—" when not in the top 100; demand "—" when the store gave none. Never estimate either.
- Under the table: the 2–3 countries to localize first and why, and the keywords to put in each one's title.

## Then

Offer to start tracking the chosen keywords in the new countries with `trackKeywords` (it counts against the plan's keyword limit, so ask first), and to write the localized listing with the `listing-for-keywords` workflow.
