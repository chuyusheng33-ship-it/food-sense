# Food Sense V1 UI Direction

Version: V0.1
Date: 2026-06-15

This document defines the first visual and interaction direction for Food Sense V1.

It is not a final design system. It is the product-facing UI direction to guide the first React/Vite mobile PWA build.

## 1. Direction Summary

Food Sense V1 should feel:

- Clean and warm.
- Professional, but not hospital-like.
- Everyday and useful, but not cute.
- Calm when warning users.
- Clear about uncertainty.

The interface should feel like a personal food reaction assistant, not a diagnosis report, diet tracker, or medical dashboard.

## 2. Product UI Principles

### 2.1 Fast First

The app should prioritize the three core actions:

```text
查食物 / 记饮食 / 记不适
```

The home screen should stay simple. It should not become a dashboard full of charts, scores, tips, or labels.

### 2.2 Low Burden

V1 forms should ask only for information that changes the user's next step.

Do not add scene fields, suggested tags, nutrition fields, or extra categories unless they clearly reduce work.

### 2.3 Editable AI

AI recognition should help fill content, not replace the user.

For images, menus, reports, and complex meals:

- Recognition output is suggested content.
- Users can edit before saving.
- The UI should not imply the result is complete or medically certain.

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

## 3. Mobile Layout Rules

V1 is mobile-first.

### 3.1 App Frame

- Use a single-column layout.
- Keep bottom navigation fixed with three items: `首页 / 记录 / 档案`.
- Do not use a bottom center `+`.
- Keep primary actions on the home screen.
- Keep page headers compact, with back navigation only when the user is inside a flow.

### 3.2 Spacing And Density

- Use generous touch targets.
- Keep forms short and scan-friendly.
- Avoid nested cards.
- Use clear section breaks instead of heavy boxes everywhere.
- Let important actions appear above the fold on common phone screens when possible.

### 3.3 Home Screen

The home screen should include only:

1. Product name and today context.
2. Three primary actions.
3. Recent record preview.
4. Local storage / privacy entry.

Empty state can prompt the user to add the first profile item, but it must still allow starting with records.

## 4. Color And State Direction

The palette should be warm, restrained, and readable.

### 4.1 Base Colors

Recommended direction:

- Background: warm off-white, not pure hospital white.
- Text: deep neutral, not cold blue-gray.
- Primary action: calm food-adjacent color such as muted tomato, cranberry, or warm coral.
- Supporting color: soft olive or sage for profile and record surfaces.
- Neutral surfaces: light cream or very pale warm gray.

Avoid:

- Hospital blue as the dominant color.
- Bright medical red for normal warnings.
- Strong green as the main success color, because it can imply `safe`.
- Overly cute pastel palettes.

### 4.2 Result States

Result states should be visually distinct but calm.

`发现需要注意的项目`

- Use warm amber, muted coral, or soft rust.
- The state should feel noticeable, not alarming.
- Do not use emergency red unless the product has a true emergency feature, which V1 does not.

`暂未发现明显命中`

- Use neutral or muted blue-gray.
- Do not use strong green.
- Copy must clarify this is based on visible information, not a safety guarantee.

`信息不足`

- Use neutral gray or soft amber.
- The UI should invite the user to add more information or ask the seller.

`无法识别`

- Use neutral gray.
- Offer retry, text input, or manual save.

## 5. Component Direction

### 5.1 Home Actions

Use three large, clear action rows or buttons:

```text
查食物
记饮食
记不适
```

Each action can have a short supporting line only if it helps the first-time user. Do not over-explain every action.

The three actions should feel equal in importance. `查食物` can be visually first, but not so dominant that logging becomes secondary.

### 5.2 Bottom Navigation

Use three stable items:

```text
首页 / 记录 / 档案
```

The active item should be clear, but not loud. Avoid badge-heavy navigation in V1.

### 5.3 Upload Entry

For `查食物` and `记饮食`, use the same input pattern:

```text
拍照上传 / 从相册选择 / 输入文字
```

The upload entry should feel like a normal choice, not a technical file picker.

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

### 5.5 Result Cards

Result cards should show:

- Result state.
- Matched item.
- Matched original text.
- Reason.
- Suggested next step.

They should not look like medical diagnosis cards. The card language should stay close to the source:

```text
命中：乳制品
原文：全脂乳粉
原因：在你的档案中
```

### 5.6 Timeline

The record timeline should be easy to scan.

Each record item should show:

- Time.
- Type: 饮食 / 不适 / 检查.
- Short content.
- Important match or severity, if any.

Filtering should stay light:

```text
全部 / 饮食 / 不适 / 检查
```

### 5.7 Profile Items

Profile item rows should show:

- Name.
- Status.
- Key aliases or hidden names.
- Source or evidence summary.

`已知需注意` and `可能相关` should be visually separated, but both belong inside `档案`.

`可能相关` must look like an observation, not a confirmed medical result.

## 6. Screen-Specific Notes

### 6.1 查食物

If the profile is empty, show this clearly before the user interprets a result:

```text
需要先有档案项，才能检查是否命中需要注意的食物或成分。
```

The screen can still let the user save check content for later.

### 6.2 记饮食

The page should make incomplete records feel acceptable.

For complex meals, AI can generate a starting description such as:

```text
火锅：牛肉、虾滑、豆腐、青菜、蘸料
```

The user can edit it before saving.

### 6.3 记不适

The page should be quick and calm.

Severity uses three levels:

```text
轻微 / 中等 / 严重
```

The save action should lead to symptom review.

### 6.4 症状后回看

Always show the boundary copy near the top:

```text
这些记录出现在不适之前，不代表一定导致症状。
```

The UI can highlight repeated or matched items, but should never claim causality.

### 6.5 隐私与数据

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

Avoid phrases that feel dismissive or add burden, such as:

- `简单写一下`
- `补充信息`
- `容易漏记`

Prefer direct labels:

- `饮食内容`
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

## 9. Open UI Questions

These should be tested during the first clickable build:

1. Is `档案` clear enough as the bottom navigation label?
2. Should the three home actions be stacked rows or a compact grid?
3. Which warm primary color feels trustworthy without feeling medical?
4. How much supporting text should first-time users see before the screen feels heavy?
5. Should `暂未发现明显命中` use a neutral state only, or a very soft positive state without green?
