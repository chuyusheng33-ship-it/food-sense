# Food Sense V1 MVP Development Slice

Version: V0.1
Date: 2026-06-15

This document turns the V1 product direction into the first buildable slice.

The goal is to build a real local-first product loop before making AI recognition, cloud accounts, or public launch work heavier.

## 1. Product Bet

The first version should prove this loop:

```text
I can define foods I care about
-> I can record what I ate
-> I can record discomfort
-> I can see what I ate before discomfort
-> I can check visible ingredients against my own food profile
```

This is enough to be personally useful and shareable with a small private group.

## 2. Build Philosophy

V1 should favor:

- Real local data over fake backend complexity.
- Fast manual input over fragile full automation.
- Clear cautious language over confident medical claims.
- A polished mobile experience over too many unfinished features.

V1 should not depend on AI being perfect.

## 3. First Build Scope

### 3.1 Must Be Real in First Build

These should work with real local data:

1. Bottom navigation:
   - `首页`
   - `记录`
   - `档案`

2. Home primary actions:
   - `查食物`
   - `记饮食`
   - `记不适`

3. Food profile:
   - Add food or ingredient manually.
   - Edit name, aliases, status, source, and notes.
   - Delete a profile item.
   - Upload or manually enter medical report items.
   - Show possible related items from usage patterns when enough records exist.
   - Store locally.

4. Food logging:
   - Record time.
   - Add short text description.
   - Select scene.
   - Add simple tags like `锅底`, `蘸料`, `饮料`, `甜品`, `加工食品`.
   - Save locally.

5. Symptom logging:
   - Record start time.
   - Select symptom type.
   - Select severity.
   - Add optional duration and notes.
   - Save locally.
   - Immediately show food records from the last 2, 4, 8, and 24 hours.

6. Timeline:
   - Show food records, symptom records, and check records in time order.
   - Allow basic filtering by type.

7. Local privacy controls:
   - Explain local-first storage.
   - Explain that AI upload is not active yet or requires explicit consent later.
   - Delete all local data.

### 3.2 Can Be Manual or Mocked in First Build

These should be designed into the UI, but can use simple local logic or mock behavior first:

1. `查食物`
   - User can choose photo or text.
   - Text input should work first.
   - App matches pasted text against food profile names and aliases.
   - Photo entry can exist as a placeholder or local attachment decision, but AI image recognition can be disabled or marked as coming later.

2. Check result:
   - Show matched profile items.
   - Show matched original text for text input.
   - Show `暂未发现明显命中` when no local match is found.
   - Show `信息不足` for empty or very short input.

3. Report import:
   - First build can use a manual confirmation table.
   - User can add extracted-looking rows manually.
   - Real OCR/AI extraction can come after the core loop is proven.

4. Profile observations:
   - First build can show simple local summaries:
     - Foods/tags that appear before symptoms.
     - Profile items recently matched.
     - Meals worth reviewing.
   - Use cautious wording and data-count thresholds.

### 3.3 Explicitly Later

Do not build these in the first implementation slice:

- Account login.
- Cloud sync.
- Public user profiles.
- Payment.
- Doctor dashboard.
- Community features.
- Barcode database.
- Large public food database.
- Full nutrition analysis.
- Automated meal recognition from photos.
- Real hospital report OCR unless the product owner explicitly pulls it forward.
- Claims that a food definitely caused symptoms.

## 4. Page Priority

### Priority 1: Core Loop

Build first:

1. App shell and bottom navigation.
2. Home with the three primary actions.
3. Food profile list and add/edit screen.
4. Food log form.
5. Symptom form.
6. Symptom review screen.
7. Timeline.
8. Local data store.

### Priority 2: Useful Check

Build after the core loop works:

1. `查食物` text input.
2. Local matching against profile names and aliases.
3. Check result screen.
4. Save check result into timeline.

### Priority 3: Profile Observations

Build after records exist:

1. Profile observation empty state.
2. Simple pattern cards.
3. Links back to related records.

### Priority 4: Import and AI Hooks

Build only after the product feels useful manually:

1. Report import confirmation UI.
2. AI consent copy.
3. Backend/API plan for OCR or image understanding.

## 5. Data Model for First Build

### 5.1 Food Profile Item

```text
id
name
aliases[]
status: avoid | observe | uncertain
source: manual | report | product | user_observation
reportLevel?
testValue?
notes?
createdAt
updatedAt
```

### 5.2 Food Record

```text
id
type: food
time
description
scene: home | restaurant | delivery | supermarket | other
tags[]
matchedProfileItemIds[]
notes?
createdAt
updatedAt
```

### 5.3 Symptom Record

```text
id
type: symptom
startTime
symptoms[]
severity
duration?
notes?
createdAt
updatedAt
```

### 5.4 Check Record

```text
id
type: check
time
inputMode: text | image
inputText?
context: package | menu | delivery | restaurant | homemade | other
resultState: matched | no_obvious_match | insufficient_info | failed
matchedProfileItemIds[]
matchedTexts[]
notes?
createdAt
updatedAt
```

## 6. First Build Acceptance Criteria

The first implementation slice is acceptable when:

1. A new user can add a food profile item in under 1 minute.
2. A user can record a meal in under 30 seconds.
3. A user can record discomfort in under 30 seconds.
4. After saving discomfort, the app shows prior food records in 2, 4, 8, and 24 hour windows.
5. A user can paste ingredient text and see whether it matches profile names or aliases.
6. A user can review all records in a timeline.
7. A user can delete all local data.
8. The UI never uses diagnostic certainty language.

## 7. Complexity Estimate

Overall first build complexity: Medium.

Why:

- The UI has multiple flows, but the first build can avoid accounts and cloud sync.
- Local storage is manageable.
- Text matching is much simpler than AI image recognition.
- The main challenge is product clarity and mobile polish, not deep backend complexity.

## 8. Product Owner Decisions Needed Before App Scaffolding

The product owner should decide:

1. Keep `档案` as the V1 navigation name?
2. Should the bottom `+` be removed, with primary actions living on the home screen?
3. Should `发现` be merged into `档案` as profile observations?
4. Should photo entry be a visible first-class option in `查食物` and `记饮食`, even if recognition is not active yet?
5. Should `查食物` first build use text matching first, with photo/AI marked as coming later?
6. Should report import be postponed until after the manual profile flow feels good?
7. Which visual direction should V1 use:
   - calm and clinical
   - warm and everyday
   - clean utility with soft warmth

## 9. Recommended Decisions

Recommended for the first build:

1. Keep `档案` for now.
2. Remove the bottom `+`; place `查食物`, `记饮食`, and `记不适` directly on the home screen.
3. Merge `发现` into `档案` as `可能相关` / observation content.
4. Show photo and text as the two entry options for both `查食物` and `记饮食`.
5. Make `查食物` text-first using local matching, while photo recognition waits.
6. Postpone real report OCR/AI extraction until the manual flow is useful.
7. Use `clean utility with soft warmth` as the visual direction.

Reason:

- It gets us to a working product fastest.
- It keeps privacy risk lower.
- It lets the product owner and early users test the core loop before we spend time on AI reliability.
