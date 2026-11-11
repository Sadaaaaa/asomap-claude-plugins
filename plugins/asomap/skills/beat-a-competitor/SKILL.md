---
name: beat-a-competitor
description: Compare one of my apps with a competitor in ASOMap — keywords where the competitor is ahead, why, and what to change in my listing to overtake it. Use when the person asks how to beat, overtake or catch up with a competitor, what a rival ranks for that they don't, "обогнать конкурента", "по каким ключам конкурент впереди".
---

# Beat a competitor

Find where a competitor wins on keywords the person cares about, and turn that into listing changes.

## Steps

1. **Pick the app** with `myApps` (ask if there are several and none was named).
2. **Pick the competitor.** Call `listCompetitors` for the app.
   - If the person named a competitor that is in the list, use it.
   - If they named one that isn't tracked yet, find it with the store search the person gives you (its store id) and offer to add it with `trackCompetitor`. Adding changes their workspace, so ask first. A new competitor has no rank history until the next collection; say so.
   - If they named none, show the list and `suggestedCompetitors` (apps that keep appearing next to theirs) and ask which one.
3. **Head to head.** For the app's store and main country:
   - `compare` — positions of both apps on every tracked keyword, plus rating and downloads;
   - `competitorGaps` — keywords where the competitor is in the top 100 and the app is behind or not ranked, with the gap.
4. **Why they win.** Call `appDetail` for the competitor to read its title, subtitle or short description and description. Note which gap keywords appear in their metadata and not in the app's (`metadataCheck` for the app).
5. **What they changed lately.** `listChanges` for the app (competitors are included) for the last 90 days: a rename, a new subtitle or description, new screenshots or a release right before they climbed is often the real reason. Match the dates against the gaps.

## What to write

Answer in the person's language:

- **Score** — on how many tracked keywords each app is ahead.
- **Biggest gaps** — up to ten keywords, sorted by demand × gap: keyword, their position, the app's position.
- **Why** — for each of the top gaps, whether the keyword is in the competitor's title or description and missing from the app's. Add any recent listing change of theirs that lines up with the climb, with its date. Say plainly when the reason isn't visible in the metadata or the change history (it may be ratings, downloads or age).
- **What to change** — concrete edits to the app's title, subtitle or keyword field that cover the gaps, within the store's character limits. Check a proposed version with `scoreListing` before suggesting it and quote the score change.

Don't copy the competitor's wording; use the keywords, write the app's own text.

## Next steps to offer

- Save the proposed listing as a draft → the `listing-for-keywords` workflow.
- Track the gap keywords that aren't tracked yet with `trackKeywords` (ask first).
