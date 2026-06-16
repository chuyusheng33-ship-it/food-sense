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
- `记症状`

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

- Use `查食物`, `记饮食`, and `记症状` for the three primary home actions.

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

## 2026-06-15: Warn before checking with an empty profile

Decision:

- When the user enters `查食物`, show a reminder if `档案` has no items.
- Explain that Food Sense can save the check content, but cannot match "things to watch" until the profile has report/manual/observed items.

Reason:

- `查食物` only has value when there is something in the user's profile to match against.
- This prevents users from interpreting "no match" as "safe".

## 2026-06-15: Treat auto-filled fields as suggestions

Decision:

- For `记饮食`, time should be auto-suggested from input when possible and remain editable.
- Do not include scene or tag suggestions in the first `记饮食` form.
- The UI label should simply be `时间`; avoid extra helper copy unless users are confused.

Reason:

- Suggestions reduce friction without pretending the app is certain.
- The user should always understand that auto-filled values can be wrong and can be edited.

## 2026-06-15: Remove scene from first `查食物` flow

Decision:

- Do not ask for scene in the first `查食物` flow.
- The input itself should be enough: ingredients, menu, delivery description, or product description.
- Show AI upload/privacy copy only when image recognition or external AI upload is actually triggered.

Reason:

- Scene adds work without improving the first text-matching version much.
- The page should stay focused on checking content against the user's profile.

## 2026-06-15: Use three severity levels for discomfort

Decision:

- Use three severity levels in `记症状`: `轻微`, `中等`, `严重`.

Reason:

- A 1-10 scale is too detailed for quick symptom logging.
- Three levels are easier to choose while the user is uncomfortable.

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

- The user makes final product decisions.
- Codex should explain tradeoffs in plain language.
- Product docs should be updated as decisions change.
- Meaningful changes should be committed and pushed to GitHub.
- See `docs/archive/collaboration-agreement.md`.

## 2026-06-16: Define V1 UI direction before app build

Decision:

- Use a clean, warm, professional-but-everyday UI direction for V1.
- Treat `Warm Utility` as the current recommended base direction.
- Keep the first build mobile-first, restrained, and focused on the three core actions.
- Avoid medical dashboard styling, strong green success states, and alarming red warning states.

Reason:

- Food Sense is health-adjacent, so trust and careful language matter more than visual novelty.
- The product needs to feel useful in daily eating situations, not like a hospital report.
- V1 private testing should validate clarity, speed, and confidence boundaries before stronger branding.

Working UI rules:

- Home actions stay as `查食物`, `记饮食`, `记症状`.
- Bottom navigation stays as `首页 / 记录 / 档案`.
- Result states use `发现需要注意的项目`, `暂未发现明显命中`, `信息不足`, and `无法识别`.
- `暂未发现明显命中` must not look or sound like `安全`.
- AI recognition results are always editable suggestions.

Still needs product owner confirmation:

- Final V1 base option remains `Warm Utility` structure plus the soft olive visual reference unless revised.
- Exact soft olive shade for the first clickable build.
- Whether home actions should use stacked rows in the first clickable build.
- Whether `档案` remains the V1 navigation label through private testing.

## 2026-06-16: Use uploaded soft olive UI reference as V1 visual anchor

Decision:

- Use the product owner's uploaded mobile UI reference as the V1 visual anchor.
- Combine the `Warm Utility` structure with the reference's warm light gray background, rounded white cards, soft olive accents, calm bottom navigation, and generous spacing.
- Shift the likely primary color from muted tomato / coral toward soft olive.

Reason:

- The reference feels clean, warm, modern, and everyday without becoming cute or medical.
- Soft olive fits Food Sense better than hospital blue or alarm red.
- The card and navigation style can make the app feel polished while keeping the home screen simple.

Boundary:

- Do not copy the event marketplace content model.
- Do not make Food Sense image-heavy just because the reference uses image cards.
- Do not use green to mean `安全`.
- `暂未发现明显命中` should stay neutral, not green success.
- Warning and attention states should still use warm amber, muted coral, or soft rust.

Output:

- `design/ui-references/food-sense-v1-soft-olive-reference.png`
- `docs/v1-ui-direction.md`
- `docs/v1-ui-options.md`

## 2026-06-16: Build UI prototype before development boundary docs

Decision:

- Do not move directly from PRD and UI direction into SDD or production app development.
- Build a clickable V1 UI prototype first so the product owner can review Food Sense's actual screen direction.
- Treat the prototype as visual and flow review only, not as the production React app.

Reason:

- A reference image and direction document are not enough to validate Food Sense's own UI.
- The product owner needs to see the Food Sense screens before approving development.
- This prevents coding too early and discovering late that the UI direction does not feel right.

Output:

- `design/prototypes/v1-ui-prototype.html`
- `docs/v1-ui-prototype-notes.md`

Next gate:

- Product owner reviews the prototype and gives feedback.
- After prototype approval, create `docs/DESIGN.md`, `docs/ARCHITECTURE.md`, and `TODO.md`.
- Formal app development starts only after those boundaries are clear.

## 2026-06-16: Remove home search from V1 prototype

Decision:

- Remove the search-style input from the V1 home prototype.
- Keep the home screen focused on the three primary actions: `查食物`, `记饮食`, and `记症状`.

Reason:

- The home search looked like a general search feature, but V1 does not need global search yet.
- If it only opens `查食物`, it duplicates the main action and adds visual noise.
- Early users should first understand the three core actions without extra interpretation.

Future note:

- A search or quick-check entry can be reconsidered after private testing if users repeatedly want to paste ingredients directly from the home screen.

## 2026-06-16: Add copy-from-recent to food logging

Decision:

- `记饮食` should let users copy a recent food record into a new editable record.
- The copied record should prefill `饮食内容`; time should be updated or remain editable before saving.
- V1 should keep this as a lightweight recent-record action, not a full template, favorite meal, or meal plan system.

Reason:

- Many users repeat meals, drinks, breakfasts, or takeout orders.
- 复制上一条或最近记录可以减少输入，帮助用户在 30 秒内完成饮食记录。
- This supports real use without adding scene fields or heavy categorization.

Product boundary:

- 复制会生成一条新记录，不会修改旧记录。
- Users can modify the copied content before saving.
- The feature should not imply nutrition tracking or a diet-plan system.

## 2026-06-16: Show meal photos and recognized foods in records

Decision:

- Food records should be able to show the meal photo when available.
- Food records should also show a clear list of recognized or entered food items.
- The `记录` page should make food records feel like meal cards, not only text notes.

Reason:

- Users need to remember what they actually ate, especially for complex meals.
- A photo plus food-item list is more useful for later symptom review than a short text line alone.
- This supports the V1 goal of AI-assisted meal recognition.

Product boundary:

- V1 should not show calories, nutrients, food scores, or diet advice.
- Recognition remains editable and may be incomplete.
- The goal is food reaction observation, not nutrition tracking.

## 2026-06-16: Split record page into clear sections

Decision:

- Keep `记录` as one bottom-navigation destination, but split its content into clear sections for `饮食`, `症状`, and `检查`.
- Do not mix all record types into one undifferentiated feed.
- Let users switch between record sections while keeping the same date context.

Reason:

- The user wants records to be easy to distinguish.
- Separate sections are easier to scan than a single mixed timeline.
- This keeps the record page organized without adding more top-level navigation.

Behavior:

- `饮食` shows meal cards with photo and food-item list.
- `症状` shows symptom cards and can link to symptom review.
- `检查` shows check results and matched items.
- Date selection still applies across sections.

## 2026-06-16: Center primary flow page titles

Decision:

- In primary action flows, center the top title area for `查食物`, `记饮食`, and `记症状`.
- Reduce title and subtitle size compared with the earlier prototype.

Reason:

- The previous title area felt too large and left-heavy.
- Centered, smaller titles make the pages feel calmer and more polished.
- The screen focus should stay on the task controls and form content.

## 2026-06-15: Set V1 UI direction

Decision:

- Use a clean, warm, professional-but-life-like UI direction for V1.
- Avoid a hospital-like visual system.
- Avoid an overly cute or playful visual system.
- Keep the home screen simple and centered on `查食物 / 记饮食 / 记症状`.

Reason:

- Food Sense handles sensitive health-adjacent information, so the interface needs trust and calm.
- The product is still a daily assistant, not a medical portal.
- Warnings need to be noticeable without frightening users.
- Green should not be used as a strong success signal because it can imply `safe`.

Output:

- `docs/v1-ui-direction.md`

## 2026-06-15: Add calendar-based record review to V1

Decision:

- The `记录` page should include a calendar entry or month view.
- Users should be able to switch dates and see that day's food, discomfort, and check records.
- The page should default to today, but should not be limited to today's records.

Reason:

- Food Sense depends on reviewing food and discomfort over time.
- A today-only record page would make longer-term observation too hard.
- A lightweight calendar supports real use without turning V1 into a statistics dashboard.

Output:

- `docs/PRD.md`
- `docs/v1-page-structure.md`
- `docs/v1-build-plan.md`
- `docs/v1-ui-direction.md`
- `design/wireframes/v1-low-fi.md`

## 2026-06-15: Explore three static UI directions before app build

Decision:

- Before building the React/Vite app, review three static UI directions.
- Use code-based static mockups because ImageGen is not available in the current tool environment.
- Do not treat these mockups as the final app.

Reason:

- The product owner wants to confirm UI feel before app construction.
- Static mockups are enough to compare layout, color, and component tone.
- This keeps the Product Design workflow while avoiding premature app scaffolding.

Output:

- `docs/v1-ui-options.md`
- `design/ui-directions/v1-ui-options.html`

## 2026-06-15: Build local-first core loop while keeping AI recognition in V1

Decision:

- The first implementation slice should prioritize a real local-first product loop.
- V1 private test target experience should include AI recognition for `查食物` and `记饮食` image input.
- Development can still start with text input, local matching, and mock recognition while the app shell and data loop are being built.
- Report extraction stays in V1 as an AI-assisted flow, but extracted items must be confirmed by the user before entering the profile.

Reason:

- The intended user journey depends on taking or uploading a photo and letting the product identify visible food, ingredients, menus, or order content.
- The product still needs a manual/text fallback for speed, privacy, and error correction.
- AI recognition must be introduced with upload consent and cautious wording.

Output:

- `docs/v1-build-plan.md`

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

- `docs/v1-build-plan.md`

## 2026-06-15: Tighten MVP scope, blacklist, and acceptance criteria

Decision:

- PRD should explicitly separate:
  - MVP core functions
  - V1 feature blacklist
  - first build acceptance criteria
- V1 MVP should include AI recognition for `查食物` and `记饮食` image input.
- `查食物` should also support text matching against local profile names and aliases as a fallback.
- Report import should be AI-assisted but always require user confirmation.

Reason:

- The product needs a real usable loop, and the intended loop includes photo-based recognition.
- AI/OCR quality, privacy, backend cost, and consent flows still need careful handling.
- Clear acceptance criteria will make UI and development decisions easier to evaluate.

Output:

- `docs/PRD.md`

## 2026-06-15: Consolidate docs for V1 planning

Decision:

- Keep the active docs folder focused on current product and build materials.
- Merge the old MVP slice and flow walkthrough into `docs/v1-build-plan.md`.
- Rename `docs/privacy-notes.md` to `docs/privacy.md`.
- Move early process notes to `docs/archive/`.

Reason:

- The GitHub and Obsidian views should be easy to scan.
- PRD should remain the product source of truth.
- The build plan should hold implementation order, user paths, and acceptance criteria without duplicating multiple process documents.

Output:

- `docs/v1-build-plan.md`
- `docs/privacy.md`
- `docs/archive/`
