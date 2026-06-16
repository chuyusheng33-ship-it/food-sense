# Food Sense V1 Build Plan

Version: V0.1
Date: 2026-06-15

This document turns the PRD into the first buildable product slice.

The PRD is the product source of truth. This file is the working plan for what to build first, in what order, and how to judge whether the first version is usable.

## 1. V1 Product Loop

V1 should prove this loop:

```text
Create or import personal food profile
-> Check visible food, ingredients, menus, or product descriptions
-> Record food
-> Record discomfort
-> Review food records before discomfort
-> Notice items worth observing
```

The product must stay cautious: it can say `可能相关`, `建议继续观察`, `信息不足`, or `可与医生讨论`; it must not say a food definitely caused symptoms.

## 2. First Build Scope

### 2.1 Must Work With Real Local Data

1. App shell with bottom navigation:
   - `首页`
   - `记录`
   - `档案`

2. Home primary actions:
   - `查食物`
   - `记饮食`
   - `记症状`

3. Food profile:
   - Add, edit, and delete items.
   - Store name, aliases, status, source, and notes.
   - Support source=`report` for manually confirmed report items.
   - Store locally.

4. Food logging:
   - Input by text.
   - Save time and description.
   - Keep time editable.
   - Store locally.

5. Discomfort logging:
   - Save start time, symptom type, 3-level severity, optional duration, and notes.
   - After saving, show food records from the last 2, 4, 8, and 24 hours.

6. Timeline:
   - Provide a calendar entry or month view.
   - Let users switch dates instead of only viewing today.
   - Show food records, discomfort records, and check records for the selected day in time order.
   - Mark days that contain records.
   - Support simple filtering by type.

7. Privacy controls:
   - Explain local-first storage.
   - Explain that AI recognition uploads require user consent.
   - Delete all local data.

### 2.2 Must Be In V1 Target Experience

These can be implemented after the local loop is working, but they are part of the intended V1 private-test product.

1. `查食物` image recognition:
   - Take photo.
   - Choose from album.
   - Recognize ingredients, menus, delivery screenshots, product descriptions, or visible food text.
   - Match recognized content against profile names and aliases.

2. `记饮食` image recognition:
   - Take photo.
   - Choose from album.
   - For complex meals, recognize likely foods from a table photo, menu, or order screenshot.
   - Generate editable food content from meals, menus, order screenshots, drinks, snacks, or packaged food.
   - Treat recognition as a suggestion; it does not need to be complete or perfectly reliable.

3. Report import:
   - Extract candidate rows from report images.
   - Let users confirm, edit, or delete each item before saving to the profile.

4. Upload consent:
   - Before sending images or text to AI, clearly explain what is uploaded and what is saved.

### 2.3 Explicitly Not In V1

1. Account login.
2. Cloud sync or multi-device sync.
3. Public launch.
4. Payment.
5. Doctor dashboard.
6. Community features.
7. Barcode database.
8. Large public food database.
9. Full nutrition analysis.
10. Fully reliable meal recognition with no user correction.
11. Medical interpretation of report results.
12. Any claim that a food definitely caused symptoms.

## 3. User Paths To Validate

### 3.1 Supermarket Or Packaged Food

Goal:

```text
User checks whether visible ingredients contain something from their profile.
```

Required screens:

1. 首页
2. 查食物
3. 检查结果
4. 记录, if saved

Required behavior:

- If profile is empty, explain that matching cannot work yet.
- Support text input as fallback.
- Support photo and album input in the V1 target experience.
- Show matched items, matched text, and cautious result language.

### 3.2 Complex Meal

Goal:

```text
User records a meal without listing every dish perfectly.
```

Required screens:

1. 首页
2. 记饮食
3. 记录

Required behavior:

- A one-line record is acceptable.
- Time is saved and editable.
- After photo upload or album selection, image recognition should suggest likely foods and generate editable content.
- The app should not make the user feel the record is invalid unless complete.

### 3.3 Discomfort After Eating

Goal:

```text
User records discomfort and immediately reviews what appeared before it.
```

Required screens:

1. 首页
2. 记症状
3. 症状后回看
4. 记录

Required behavior:

- Record symptoms in under 30 seconds.
- Use 3 severity levels: `轻微`, `中等`, `严重`.
- Show prior food records across 2, 4, 8, and 24 hour windows.
- Use cautious copy such as `这些记录出现在不适之前，不代表一定导致症状`.

### 3.4 Report To Profile

Goal:

```text
User turns report items into profile items that can be used by checks.
```

Required screens:

1. 档案
2. 档案详情 / 添加项目
3. 报告提取确认

Required behavior:

- Manual report-source entry should work first.
- AI-assisted extraction is part of the V1 target experience.
- Extracted items must be confirmed by the user before entering the profile.

## 4. Build Order

### Step 1: App Shell And Local Store

Build:

1. React + TypeScript + Vite app.
2. Mobile-first layout.
3. Bottom navigation.
4. Local data store.
5. Mock data for early visual states.

### Step 2: Core Manual Loop

Build:

1. 首页.
2. 档案 add/edit/delete.
3. 记饮食 text flow.
4. 记症状 flow.
5. 症状后回看.
6. 记录 timeline.

### Step 3: 查食物 Text Matching

Build:

1. 查食物 text input.
2. Local matching against profile names and aliases.
3. 检查结果.
4. Save check record to timeline.
5. Empty-profile warning.

### Step 4: AI Recognition

Build:

1. AI upload consent UI.
2. Backend/API route for AI calls.
3. `查食物` image recognition.
4. `记饮食` image recognition.
5. Report extraction confirmation.

### Step 5: Polish For Private Test

Build:

1. Empty states.
2. Error states.
3. Delete local data flow.
4. Mobile polish.
5. Cautious copy review.

## 5. Acceptance Criteria

The V1 private-test build is acceptable when:

1. A new user can add a profile item in under 1 minute.
2. A user can record a meal in under 30 seconds.
3. A user can record discomfort in under 30 seconds.
4. After saving discomfort, the app shows prior food records in 2, 4, 8, and 24 hour windows.
5. A user can paste ingredient text and see whether it matches profile names or aliases.
6. A user can use photo or album input in `查食物` and see recognized content.
7. A user can use photo or album input in `记饮食` and get editable food content.
8. A report item can be added manually or confirmed from extraction before entering the profile.
9. A user can use the record calendar to switch dates and review that day's timeline.
10. A user can delete all local data.
11. The UI never uses diagnostic certainty language.

## 6. Key Open Decisions

1. Keep `档案` as the V1 navigation name?
2. Which AI recognition provider should power image input?
3. What exact consent copy should appear before uploading images or text?
4. Should report images be stored locally, or should only structured results be saved?
5. How should the first clickable build test whether `档案` is clear enough?

Resolved:

- V1 UI direction is defined in `docs/v1-ui-direction.md`: clean and warm, professional but life-like, calm about warnings, and careful with uncertainty.
