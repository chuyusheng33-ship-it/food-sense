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

- `能吃吗`
- `记吃了什么`
- `记录不舒服`

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
