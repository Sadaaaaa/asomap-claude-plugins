---
name: release
description: Prepare a release of one of my apps in ASOMap — translate the "What's new" text into every language the listing has and save it, and build a screenshot set from the person's screenshots. Use when the person is shipping an update, asks to translate release notes or changelog, write "What's new", or make store screenshots, "релиз", "перевести что нового", "сделать скриншоты".
---

# Release

Two jobs around an app update; do the ones the person asks for.

## A. "What's new" in every language

1. **Pick the app** with `myApps` (ask if unclear).
2. **Get the text.** Use the release notes the person gave you; if they gave none, ask for them. Note the language they're written in (usually en-US).
3. **Find the languages.** Call `changelogLocales` for the app.
   - `origin: confirmed` — the listing's real locale set; translate into all of it.
   - Otherwise the list is a guess. Show it and ask the person to confirm or correct it before translating.
4. **Translate.** One natural translation per locale, same meaning, the store's tone (short, friendly, no marketing filler). Keep app and feature names as they are. Respect the stores' length: App Store and Google Play allow 4000 characters for release notes, but keep each text close to the source length.
5. **Save** with `saveChangelog`: `sourceLocale` plus one entry per locale **including the source itself**. A save replaces the whole changelog, so a locale left out is dropped. Check the reply's `missing` and `unknown` lists and fix anything they flag.

The translations appear on ASOMap's Changelog page: per language, and for Google Play as one tagged block to paste into Play Console.

## B. Screenshot set

1. **Read the guide first:** `screenshotDesignGuide` describes the workflow and the design format. Follow it rather than guessing the format.
2. **Get the images.** Ask where the person's screenshots are. Upload them through `screenshotUploadLink` as the guide describes.
3. **Write the captions** in every language the listing has (see step A.3), short and benefit-first, one idea per screen.
4. **Create the set** with `createScreenshotSet`. It shows up on ASOMap's Screenshots page, where the person can edit it and export every store size.

## What to write

Answer in the person's language: what was saved, for which languages or sizes, and where in ASOMap to find it.
