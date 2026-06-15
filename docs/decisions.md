# Decisions

This file records product decisions and the reasoning behind them.

## 2026-06-14: Use `food-sense` as the project codename

Decision:

- Use `food-sense` for the local project folder and repository name.

Reason:

- It is simple, descriptive, and flexible enough before the product has a final brand name.

## 2026-06-14: Start as mobile web / PWA

Decision:

- V1 should be a mobile-first web app / PWA.

Reason:

- It is easier to share with 5-20 private users.
- It avoids app store review and native app complexity.
- It can still support camera/image upload and local storage.

## 2026-06-14: Local-first storage for V1

Decision:

- V1 should store data locally first instead of requiring cloud accounts.

Reason:

- The first test group is small.
- Food and symptom data is sensitive.
- Local-first reduces privacy and backend complexity for the first version.

Tradeoff:

- Data will not sync across devices in V1.
- Users may lose data if they clear browser storage.

## 2026-06-14: Do not diagnose allergy

Decision:

- The product should not claim that a user is allergic to a food.

Reason:

- Food sensitivity and intolerance are complex.
- The product is for recording, reviewing, and pattern discovery, not diagnosis.

Preferred wording:

- `可能相关`
- `建议继续观察`
- `可与医生讨论`

## 2026-06-14: Main actions are centered around user language

Decision:

- The main action labels should use user language instead of technical feature names.

Current working labels:

- `查食物`
- `记饮食`
- `记不适`

Reason:

- These match the user's real-life questions better than labels such as `风险扫描` or `症状记录`.

## 2026-06-14: Food profile area name is unresolved

Decision:

- Do not finalize the label yet.

Rejected or uncertain labels:

- `清单`: too plain and vague.
- `关注`: confusing.
- `避雷`: too aggressive.
- `忌口`: too restrictive and medical-feeling.
- `我的食物`: warmer, but still may be vague as a navigation label.

Need:

- A warmer but clear name for the area that contains known foods to avoid, foods to observe, and report-extracted items.

## 2026-06-14: Use `档案` as the temporary V1 navigation label

Decision:

- Use `档案` as the temporary V1 label for the personal food profile area.

Reason:

- It is clearer than `清单` or `关注`.
- It is less aggressive than `避雷`.
- It is less restrictive and medical-feeling than `忌口`.
- It can contain avoid items, observe items, uncertain items, report extraction results, manual entries, aliases, and hidden ingredients.

Tradeoff:

- It may feel slightly formal.
- It should be tested with private users before being treated as final naming.

Update on 2026-06-15:

- `食物档案` was shortened to `档案` to keep bottom navigation labels concise and consistent.
- The full meaning remains personal food/ingredient profile.

## 2026-06-15: Use equal-length home action labels

Decision:

- Use `查食物`, `记饮食`, and `记不适` for the three primary home actions.

Reason:

- The previous labels had uneven length and rhythm.
- The new labels are short, action-oriented, and consistent.
- They still map to the user's real tasks: checking food, logging intake, and recording discomfort.

## 2026-06-15: Remove bottom `+` from V1 navigation

Decision:

- V1 bottom navigation should be `首页 / 记录 / 档案`.
- The three primary actions should live directly on the home screen instead of behind a center `+`.

Reason:

- The first version has only three core actions.
- Showing them on the home screen makes the product easier to understand.
- A hidden `+` adds navigation complexity before the product needs it.

## 2026-06-15: Merge `发现` into `档案`

Decision:

- Remove `发现` as a separate V1 bottom navigation item.
- Treat `档案` as the user's personal food reaction profile.
- `档案` should include known report/manual items and non-diagnostic possible related items discovered through ongoing use.

Reason:

- The user thinks of these as one personal profile, not two separate areas.
- Medical report imports and long-term observation both contribute to the same personal food profile.
- This reduces navigation and makes the product easier to explain.

Language boundary:

- Use `可能相关`, `观察中`, and `建议继续观察`.
- Do not say `可能过敏` or imply diagnosis.

## 2026-06-14: Move V1 into low-fidelity page structure

Decision:

- Start V1 design with text-based low-fidelity wireframes before implementing app code.

Reason:

- The product has sensitive health-adjacent flows and needs careful language before UI polish.
- The three core actions need to be fast and understandable.
- Privacy and AI upload moments need to be built into the structure early.

Output:

- `docs/v1-page-structure.md`
- `design/wireframes/v1-low-fi.md`

## 2026-06-14: Keep Obsidian view updated with project docs

Decision:

- The Food Sense project folder is also available in Obsidian.
- Future updates to product docs, design notes, decisions, and planning materials should be reflected in the Obsidian-visible Markdown files.

Reason:

- Obsidian is useful for reviewing and connecting product thinking.
- The repository Markdown files should remain the source of truth, so GitHub and Obsidian do not drift apart.

Working rule:

- Update the repo Markdown files first.
- Commit and push changes to GitHub.
- If a separate Obsidian-only summary note is created later, update that note alongside the repo docs.

## 2026-06-15: Adopt a technical co-founder collaboration model

Decision:

- The user is the product owner with final decision power.
- Codex acts as technical co-founder and builder.
- Food Sense should be treated as a real product, not a throwaway prototype.

Reason:

- The project needs product judgment, implementation speed, clear documentation, and careful handling of health-adjacent risks.
- The product owner should stay informed and in control without having to manage every technical detail.

Working agreement:

- See `docs/collaboration-agreement.md`.

## 2026-06-15: Build local-first core loop before heavy AI

Decision:

- The first implementation slice should prioritize a real local-first product loop.
- AI image recognition and real report OCR should be added after the manual and text-based flows are useful.

Reason:

- The main product value can be tested with manual food profile items, food logs, symptom logs, review windows, and text-based ingredient matching.
- This reduces privacy, reliability, and backend complexity during the first build.
- It lets early users validate whether the product is useful before investing in heavier AI infrastructure.

Output:

- `docs/v1-mvp-slice.md`

## 2026-06-15: Use four real paths to validate V1 before app scaffolding

Decision:

- Before app scaffolding, validate the V1 plan against four real user paths:
  - supermarket / packaged food
  - hot pot / complex meal
  - discomfort after eating
  - hospital report to food profile

Reason:

- The MVP slice defines what to build, but the walkthrough checks whether the flows make sense in real life.
- It clarifies required fields, deferred features, cautious wording, and button destinations.

Output:

- `docs/v1-flow-walkthrough.md`
