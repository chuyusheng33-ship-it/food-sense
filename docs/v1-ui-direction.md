# Food Sense V1 UI Direction

Version: V0.3
Date: 2026-06-16

This document defines the first visual and interaction direction for Food Sense V1.

It is not a final design system. It is the product-facing UI direction for the first React + TypeScript + Vite mobile PWA build.

## 1. Direction Summary

Food Sense V1 should feel:

- Clean and warm.
- Professional, but not hospital-like.
- Everyday and useful, but not cute.
- Calm when warning users.
- Clear about uncertainty.

The interface should feel like a personal food reaction assistant, not a diagnosis report, diet tracker, nutrition app, or medical dashboard.

Working recommendation:

- Use the uploaded soft olive mobile reference as the visual anchor for V1.
- Keep the `Warm Utility` structure, but shift the accent color toward soft olive instead of tomato/coral.
- Keep the first build restrained. The goal is trust, speed, and clarity, not a strong brand statement yet.

Reference image:

```text
design/ui-references/food-sense-v1-soft-olive-reference.png
```

## 2. Product UI Principles

### 2.1 Fast First

The app should prioritize the three core actions:

```text
查食物 / 记饮食 / 记症状
```

The home screen should stay simple. It should not become a dashboard full of charts, scores, tips, lessons, or lifestyle content.

### 2.2 Low Burden

V1 forms should ask only for information that changes the user's next step.

Do not add scene fields, nutrition fields, suggested tags, or extra categories unless they clearly reduce work.

### 2.3 Editable AI

AI recognition should help fill content, not replace the user.

For images, menus, reports, and complex meals:

- Recognition output is suggested content.
- Users can edit before saving.
- The UI should not imply the result is complete.
- The UI should not imply the result is medically certain.

### 2.4 Careful Language

UI copy should use observation language:

- `可能相关`
- `建议继续观察`
- `信息不足`
- `基于目前可见信息`
- `可与医生讨论`

Avoid certainty language:

- `安全`
- `放心吃`
- `一定导致`
- `过敏`
- `绝对不能吃`
- `完全没问题`

## 3. Mobile Layout Rules

V1 is mobile-first.

### 3.1 App Frame

- Use a single-column layout.
- Keep bottom navigation fixed with three items: `首页 / 记录 / 档案`.
- Do not use a bottom center `+`.
- Keep primary actions on the home screen.
- Keep page headers compact.
- Use back navigation only inside a task flow.
- For primary action flows such as `查食物`, `记饮食`, and `记症状`, center the page title area and keep the title/subtitle smaller than home hero text.

### 3.2 Screen Width And Safe Area

- Design for common phone widths first.
- Keep readable content within a comfortable horizontal padding.
- Avoid edge-to-edge cards that make dense text feel cramped.
- Keep bottom actions above the bottom navigation or safe area.

### 3.3 Spacing And Density

- Use generous touch targets.
- Keep forms short and scan-friendly.
- Avoid nested cards.
- Use clear section breaks instead of heavy boxes everywhere.
- Let important actions appear above the fold on common phone screens when possible.
- Use compact section titles. Do not use hero-scale type inside forms, cards, or timelines.

### 3.4 Home Screen

The home screen should include only:

1. Product name and today context.
2. Three primary actions.
3. Recent record preview.
4. Local storage / privacy entry.

Empty state can prompt the user to add the first profile item, but it must still allow starting with records.

## 4. Color And State Direction

The palette should be warm, restrained, readable, and not one-note.

Soft olive is the anchor color, but it should not carry every meaning. V1 needs a small supporting palette so the app can distinguish actions, records, profile content, attention states, and neutral uncertainty without feeling medical or cute.

### 4.1 V1 Color System

Core tokens:

| Role | Token | Hex | Use |
| --- | --- | --- | --- |
| App background | `background` | `#EEEDE7` | App canvas and phone background |
| Surface | `surface` | `#FFFFFB` | Cards, forms, bottom navigation |
| Soft surface | `surface-soft` | `#F7F6EF` | Secondary panels and quiet grouped areas |
| Text | `text` | `#22231F` | Primary copy |
| Muted text | `muted` | `#7D7D73` | Helper copy and timestamps |
| Border | `border` | `#E3E1D7` | Card borders, dividers, input outlines |
| Primary olive | `primary` | `#596321` | Primary buttons, selected states, active navigation |
| Deep olive | `primary-dark` | `#3F4718` | Pressed states and strong headings when needed |
| Olive tint | `primary-soft` | `#EEF1DF` | Selected chips, soft primary backgrounds |

Supporting colors:

| Role | Token | Hex | Use |
| --- | --- | --- | --- |
| Sage | `sage` | `#DDE5D2` | Profile surfaces, known/observed food context |
| Mist blue | `mist` | `#DCE6E8` | Neutral information, no clear match, data/privacy moments |
| Warm amber | `amber` | `#D7A245` | Attention without panic, medium severity |
| Amber tint | `amber-soft` | `#FFF5DD` | Attention card backgrounds |
| Soft rust | `rust` | `#B96B43` | Stronger attention, severe symptom level |
| Rust tint | `rust-soft` | `#FFF0E7` | Matched item / stronger attention backgrounds |
| Clay | `clay` | `#C98F67` | Human warmth for small accents, empty states, illustrations |

### 4.2 Color Use Rules

Use olive for:

- Primary actions.
- Active bottom navigation.
- Selected chips.
- Calm confirmation that an action is selected or saved.

Do not use olive for:

- `暂未发现明显命中` as a success state.
- Any message that could be read as `safe`.
- Medical certainty.

Use sage for:

- `档案` content.
- Known or observed food profile areas.
- Quiet food-related context.

Use mist blue for:

- Privacy/data explanations.
- `暂未发现明显命中`.
- Neutral information where the app is not warning the user.

Use amber/rust for:

- `发现需要注意的项目`.
- Stronger attention.
- Symptom severity above light.

Do not use bright red in V1 unless a future version adds a true emergency flow.

Avoid:

- Hospital blue as the dominant color.
- Bright medical red for normal warnings.
- Bright or medical green as a result-state success color.
- Overly cute pastel palettes.
- One-note palettes where the whole app reads as only beige, only green, or only red.

### 4.3 Component Color Mapping

Recommended first mapping:

| Component | Default | Active / Important | Attention |
| --- | --- | --- | --- |
| Home action | `surface` | Olive icon or label accent | None |
| Primary button | `primary` | `primary-dark` on press | None |
| Secondary button | `surface` + `border` | Olive text | None |
| Bottom nav | Muted text | `primary` | None |
| Upload method | `surface` | Olive icon | None |
| Form field | `surface` + `border` | Olive focus border | None |
| Record card | `surface` | Type pill uses olive/mist/amber | None |
| Profile card | `surface` or sage tint | Olive label | Amber/rust only for attention |
| Result summary | `surface` or mist tint | State-dependent | Amber/rust tint for matches |
| Notice | `surface-soft` or mist tint | None | Amber tint only when action is needed |

### 4.4 Result States

Result states should be visually distinct but calm.

`发现需要注意的项目`

- Use warm amber or soft rust.
- The state should feel noticeable, not alarming.
- Do not use emergency red unless the product has a true emergency feature, which V1 does not.

`暂未发现明显命中`

- Use neutral or mist blue.
- Do not use strong green.
- Copy must clarify this is based on visible information, not a safety guarantee.

`信息不足`

- Use neutral gray or soft amber.
- Invite the user to add more information or ask the seller.

`无法识别`

- Use neutral gray.
- Offer retry, text input, or manual save.

### 4.5 Severity States

For `记症状`, severity uses three levels:

```text
轻微 / 中等 / 严重
```

Visual treatment:

- `轻微`: neutral or sage/mist tint.
- `中等`: warm amber.
- `严重`: deeper warm rust, not emergency red.

Do not make severity look like a medical triage system.

## 5. Component Direction

### 5.1 Home Actions

Use three large, clear action rows or buttons:

```text
查食物
记饮食
记症状
```

Rules:

- The three actions should feel equal in importance.
- `查食物` can appear first, but it should not make logging feel secondary.
- Each action can have a short supporting line only if it helps the first-time user.
- Do not over-explain every action.

Recommended first build:

- Use stacked action rows on mobile.
- Each row has one clear label and one small visual cue.
- Match the reference's rounded white surfaces and soft shadow style, but keep Food Sense less image-heavy.
- Avoid a dense 3-card grid unless the first screen feels too long.

### 5.2 Bottom Navigation

Use three stable items:

```text
首页 / 记录 / 档案
```

Rules:

- The active item should be clear, but not loud.
- Use soft olive for the active bottom navigation item.
- Avoid badge-heavy navigation in V1.
- Keep labels short.
- Do not put primary creation actions in the bottom navigation.
- Do not add an extra home icon inside `记录` or `档案`; bottom navigation already provides the way back to `首页`.

### 5.3 Upload Entry

For `查食物` and `记饮食`, use the same input pattern:

```text
拍照上传 / 从相册选择 / 输入文字
```

Rules:

- The upload entry should feel like a normal choice, not a technical file picker.
- The three choices should be visible without hiding them behind a generic upload button.
- If image recognition is used, show the recognized content in editable form.

When AI upload is triggered, show a clear consent moment that explains:

- What will be uploaded.
- What it will be used for.
- What will be saved locally.

### 5.4 Forms

Forms should be short and direct.

Use:

- Text fields for user-editable content.
- Segmented controls or chips for small fixed choices.
- Date/time controls only when useful.
- Simple save buttons with direct labels.

Avoid:

- Long helper text under every field.
- Required-looking fields that are actually optional.
- Tags or scene choices in the first food logging flow.
- Placeholder text that sounds dismissive, such as `简单写一下`.

Preferred labels:

```text
饮食内容
检查内容
时间
开始时间
症状类型
严重程度
持续时间
备注
保存记录
保存并回看
```

### 5.5 Result Cards

Result cards should show:

- Result state.
- Matched item.
- Matched original text.
- Reason.
- Suggested next step.

They should not look like medical diagnosis cards. Keep language close to the source:

```text
命中：乳制品
原文：全脂乳粉
原因：在你的档案中
```

Rules:

- Do not use a `safe` or `risk score` pattern.
- Do not show a medical-looking badge.
- If there is no clear match, say `暂未发现明显命中`, not `安全`.
- If the source is incomplete, show `信息不足` clearly.

### 5.6 Timeline

The record page should be easy to scan and should not mix every record type into one confusing feed.

The record page should include a lightweight calendar entry or month view so users can move beyond today and review a specific date.

The calendar should:

- Default to today.
- Mark days that have records.
- Avoid heavy analytics or health-score styling in V1.

Use clear sections or segmented views:

```text
饮食 / 症状 / 检查
```

Each section should show only its own record type.

Food record items should show:

- Time.
- Meal photo when available.
- Recognized or entered food items.
- Important profile match, if any.

Symptom record items should show:

- Time.
- Symptom type.
- Severity.
- Link to symptom review, if useful.

Check record items should show:

- Time.
- Checked content.
- Result state and matched items, if any.

### 5.7 Profile Items

Profile item rows should show:

- Name.
- Status.
- Key aliases or hidden names.
- Source or evidence summary.

`已知需注意` and `可能相关` should be visually separated, but both belong inside `档案`.

`可能相关` must look like an observation, not a confirmed medical result.

Recommended visual hierarchy:

- `已知需注意`: slightly stronger surface or label.
- `观察中`: neutral surface.
- `可能相关`: observation-style surface with evidence text.

## 6. Screen-Specific Notes

### 6.1 首页

Keep the first screen calm and useful.

Recommended order:

1. `Food Sense` and date / today context.
2. `今天要做什么？`
3. Three action rows.
4. Recent record preview.
5. `本地保存 · 隐私与数据`.

Do not add trend charts, health scores, food education content, or daily tips in V1.

### 6.2 查食物

If the profile is empty, show this clearly before the user interprets a result:

```text
需要先有档案项，才能检查是否命中需要注意的食物或成分。
```

The screen can still let the user save check content for later.

The input area should support:

- `拍照上传`
- `从相册选择`
- `输入文字`

Do not ask for a scene.

### 6.3 检查结果

Header:

- Use the short title `检查结果`.
- Do not put caution copy in the title area.
- Put `基于目前可见信息` as a content-level notice above the result summary.

Required result framing:

```text
基于目前可见信息
```

Use one of these states:

- `发现需要注意的项目`
- `暂未发现明显命中`
- `信息不足`
- `无法识别`

Do not use:

- `安全`
- `可以放心吃`
- `你对这个过敏`
- `这一定导致不适`

### 6.4 记饮食

The page should make incomplete records feel acceptable without saying `容易漏记`.

The page should also support repeated meals:

- Show a lightweight `从过往饮食选择` entry near the input methods.
- Tapping it opens a simple selection page with past meal cards.
- Past meal cards should show time, meal title, food items, and a photo when available.
- Use it when the current meal is the same or similar to a previous record.
- Copying should create an editable draft.
- Do not make this a heavy template or favorites system in V1.

The saved record should feel more like a meal card than a text note:

- Show a meal photo when available.
- Show the recognized or entered food items as a clear list.
- Keep the list mobile-friendly and easy to scan.
- Do not show calorie, nutrient, or score-style information in V1.

For complex meals, AI can generate a starting description such as:

```text
火锅：牛肉、虾滑、豆腐、青菜、蘸料
```

The user can edit it before saving.

Rules:

- Time field stays visible and editable.
- Do not write `建议，可修改`.
- Do not add scene field.
- Do not add suggested tags in the first flow.

### 6.5 记症状

The page should be quick and calm.

Severity uses three levels:

```text
轻微 / 中等 / 严重
```

The save action should lead to symptom review.

### 6.6 症状后回看

Always show the boundary copy near the top:

```text
这些记录出现在不适之前，不代表一定导致症状。
```

The UI can highlight repeated or matched items, but should never claim causality.

The time window control should be:

```text
2小时 / 4小时 / 8小时 / 24小时
```

### 6.7 档案

The `档案` page should feel like a personal reference area, not a diagnosis page.

Primary sections:

- `已知需注意`
- `可能相关`

Actions:

- `添加`
- `上传报告`

If empty, offer:

- Add first item.
- Upload report.
- Start recording first.

### 6.8 报告提取确认

This screen must make user confirmation obvious.

Rules:

- AI-extracted rows are candidates, not final profile items.
- User can edit, delete, or uncheck extracted rows.
- Only confirmed rows enter `档案`.
- Do not imply the app has interpreted the medical meaning of the report.

### 6.9 隐私与数据

The privacy page should be short, plain, and reachable.

It should explain:

- V1 uses local browser storage.
- AI recognition may upload selected content only after notice.
- Users can delete all local data.

## 7. Typography And Tone

Use simple Chinese UI text.

Tone:

- Calm.
- Direct.
- Human.
- Not overly medical.
- Not playful for serious states.

Avoid phrases that feel dismissive or add burden:

- `简单写一下`
- `补充信息`
- `容易漏记`

Prefer direct labels:

- `饮食内容`
- `检查内容`
- `时间`
- `备注`
- `保存记录`

## 8. First Build Guidance

When the app build starts, begin with a lightweight design token layer:

- Spacing scale.
- Text sizes.
- Color roles.
- Surface styles.
- Button and input styles.
- Result state styles.

Do not overbuild a design system before the first private-test flow works.

The first UI implementation should prove:

1. Home actions are clear.
2. Food logging feels fast.
3. Symptom logging feels calm.
4. Check results are understandable without implying safety or diagnosis.
5. Profile items are easy to add and scan.
6. Privacy and AI upload moments are visible at the right time.

## 9. Product Owner Decisions Needed

Before building polished screens, the product owner should still choose:

1. Confirm whether home actions should use stacked rows or the current compact grid in the first build.
2. Confirm whether `档案` remains the V1 bottom navigation label through private testing.
3. Review the expanded color system in the clickable prototype before implementation begins.

Current recommendation:

- Start with `Warm Utility` structure plus the uploaded soft olive reference.
- Use the expanded soft olive color system in this document.
- Consider stacked home action rows if the compact grid feels too compressed.
- Keep `档案` for private testing.
- Use olive for primary navigation and actions.
- Use mist blue for neutral information and no-clear-match states.
- Use sage for profile and food context.
- Use warm amber / soft rust only for attention states.
