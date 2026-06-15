# Food Sense

Food Sense is a working codename for a food sensitivity and intolerance companion.

The product helps people:

- Check whether a food, menu, package, or ingredient list may contain foods they need to avoid or observe.
- Record what they ate in real life, including complex meals.
- Record symptoms and review what appeared before them.
- Build a personal food reaction history over time.

This repository starts as the product workspace. It contains product docs, design notes, and eventually the app code.

## Current Stage

Stage: Exploration to V1 planning.

The first version is planned as a mobile web app / PWA for small private testing with 5-20 users.

## Structure

```text
docs/
  PRD.md
  collaboration-agreement.md
  v1-page-structure.md
  user-journey.md
  privacy-notes.md
  decisions.md
design/
  wireframes/
  ui-references/
app/
```

## Current Design Notes

V1 is currently in low-fidelity page structure planning.

Working bottom navigation:

```text
首页 / 记录 / + / 食物档案 / 发现
```

The center `+` opens:

- `能吃吗`
- `记吃了什么`
- `记录不舒服`

Current low-fidelity materials:

- `docs/v1-page-structure.md`
- `design/wireframes/v1-low-fi.md`

Working agreement:

- `docs/collaboration-agreement.md`

## Obsidian Sync Note

This project is also available in Obsidian.

When project docs, design notes, decisions, or planning materials are updated, keep the Markdown files in this repository as the source of truth so the Obsidian view stays current too.

## Product Boundary

Food Sense is not a diagnostic medical product. It should not claim that a user is allergic to a food. It should help users record, review, and notice patterns that may be worth observing or discussing with a clinician.
