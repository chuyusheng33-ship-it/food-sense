# Food Sense V1 Page Structure

Version: V0.1
Date: 2026-06-14

This document defines the first low-fidelity page structure for Food Sense V1.

The goal is not visual design yet. The goal is to decide what each screen needs to contain, how users move between screens, and what information must be visible for the first private test.

## 1. Navigation Model

V1 uses a mobile-first bottom navigation:

```text
首页 / 记录 / 档案
```

The home screen shows the three primary actions:

```text
查食物
记饮食
记不适
```

`档案` is the user's personal food reaction profile. It contains report-confirmed items, manually added items, and possible patterns discovered from food and symptom records.

## 2. Screen List

V1 low-fidelity screens:

1. 首页
2. 查食物
3. 检查结果
4. 记饮食
5. 记不适
6. 症状后回看
7. 记录
8. 档案
9. 档案详情 / 添加项目
10. 报告提取确认
11. 隐私与数据

## 3. Screen Details

### 3.1 首页

Purpose:

- Give the user a calm starting point.
- Surface the most useful next action.
- Show recent signals without claiming diagnosis.

Primary content:

- Main prompt: `今天要做什么？`
- Three action shortcuts: `查食物`, `记饮食`, `记不适`.
- One recent activity preview.
- Local storage / privacy link.

Empty state:

- If the user has no profile and no records, show one simple setup prompt:
  - Add first profile item.
  - Or skip and start recording.

Language boundary:

- Avoid medical certainty.
- Use `记录`, `观察`, `可能相关`.

### 3.2 查食物

Purpose:

- Check visible food information against the user's food profile.
- Remind the user that checks only work meaningfully when the profile has items.

Input methods:

- Take and upload photo.
- Choose from album.
- Paste text.

Primary fields:

- Profile prerequisite notice:
  - If the profile is empty, explain that the app cannot match anything yet.
  - Offer `去添加` and `保存检查内容`.
- Input choice: take photo, choose from album, or text.
- Photo placeholder or future AI flow.
- `检查内容`: ingredients, menu, delivery description, or product description.
- AI/privacy notice only when image recognition or external AI upload is actually triggered.

Primary action:

- `开始检查`

Secondary actions:

- Save check content as a record, especially when the profile is empty.
- Cancel.

### 3.3 检查结果

Purpose:

- Show whether visible information contains items from the user's food profile.

Result states:

- `发现需要注意的项目`
- `暂未发现明显命中`
- `信息不足`
- `无法识别`

Primary content:

- Result summary.
- Matched profile items.
- Matched original text, such as `全脂乳粉`, `白砂糖`.
- Why this was flagged.
- Confidence or completeness note.
- Suggested next step:
  - Avoid or choose carefully.
  - Ask seller.
  - Add missing ingredients.
  - Save as food record.

Language boundary:

- Do not say `安全`, `一定没问题`, `一定导致症状`, or `过敏`.
- Prefer `目前可见信息中`, `可能相关`, `建议继续观察`.

### 3.4 记饮食

Purpose:

- Make real-life food logging fast enough that users will actually do it.

Input methods:

- Take and upload photo.
- Choose from album.
- Text note.

Primary fields:

- `饮食内容`: photo-derived or text-entered meal description.
- Time, suggested from input when possible and marked editable.
- Extracted food tags, if AI or manual parsing is available.

Complex meal support:

- Allow one photo plus one sentence.
- After photo upload or album selection, automatically suggest likely foods from the image.
- Generated food content must be editable before saving.
- Recognition is a suggestion and does not need to be complete.

Primary action:

- `保存记录`

### 3.5 记不适

Purpose:

- Let the user record symptoms quickly and then review prior food.

Primary fields:

- Start time.
- Symptom type:
  - abdominal pain
  - bloating
  - diarrhea
  - nausea
  - skin reaction
  - other
- Severity: mild, moderate, severe.
- Duration.
- Notes.

Primary action:

- `保存并回看`

### 3.6 症状后回看

Purpose:

- Immediately answer: what did I eat before feeling uncomfortable?

Primary content:

- Time window selector: 2h, 4h, 8h, 24h.
- Food records in that window.
- Highlighted profile matches.
- Repeated foods from recent records.
- Button to mark item as `继续观察`.

Language boundary:

- Say `这些记录出现在不舒服之前`.
- Say `可能值得继续观察`.
- Do not say `这些导致了不舒服`.

### 3.7 记录

Purpose:

- Provide a chronological view of food checks, food logs, and symptoms.

Primary content:

- Date selector.
- Timeline grouped by day.
- Item types:
  - food check
  - food record
  - symptom record
- Filters:
  - all
  - food
  - symptoms
  - checks
- Tap item to view or edit details.

Primary actions:

- Edit or delete an entry.

### 3.8 档案

Purpose:

- Store and grow the user's personal food reaction profile.
- Combine known report/manual items with non-diagnostic observation patterns.

Primary content:

- `已知需注意`: items from medical reports or manual entries.
- `观察中`: items the user is watching.
- `可能相关`: foods or tags that repeatedly appear before discomfort.
- Food cards show:
  - name
  - status
  - key aliases
  - source or evidence summary
- Empty state for:
  - Add manually.
  - Upload report.
  - Start recording without setup.

Primary actions:

- Add food or ingredient.
- Upload medical report.
- Review related records for possible patterns.

### 3.9 档案详情 / 添加项目

Purpose:

- Let the user create and refine one profile item.

Fields:

- Food or ingredient name.
- Aliases / hidden names.
- Status: avoid, observe, uncertain.
- Source.
- Notes.

Primary actions:

- Save.
- Delete.

### 3.10 报告提取确认

Purpose:

- Make report import user-confirmed, not automatic.

Flow:

1. User chooses report image.
2. Product explains AI upload if needed.
3. Product extracts candidate items.
4. User reviews and edits extracted rows.
5. User confirms which items enter food profile.
6. Product avoids long-term storage of original report image by default.

Primary content:

- Extracted rows.
- Original detected name.
- Result level.
- Value.
- Proposed status.
- Include checkbox.

### 3.11 隐私与数据

Purpose:

- Give the user control and clarity around sensitive local data.

Primary content:

- Local storage explanation.
- AI upload explanation.
- Saved data categories:
  - food profile
  - food records
  - symptom records
  - check results
  - extracted report data
- Delete all local data.
- Delete report images, if any are temporarily stored.
- Export data can be considered later, but is not required for V1.

## 4. Key Flows

### 4.1 Check Before Eating

```text
首页
-> 查食物
-> photo / image / text
-> consent if AI upload is needed
-> result
-> optional save as food record
```

### 4.2 Log Complex Meal

```text
首页
-> 记饮食
-> photo or text
-> short note
-> time / scene / optional tags
-> save
-> 记录
```

### 4.3 Record Symptom and Review

```text
首页
-> 记不适
-> save symptom
-> 症状后回看
-> choose 2h / 4h / 8h / 24h
-> mark food as continue observing
```

### 4.4 Build Food Profile

```text
档案
-> add manually or upload report
-> confirm known items
-> app adds possible related foods after enough records
-> future checks and logs use profile
```

### 4.5 Observe in Profile

```text
档案
-> record foods and symptoms over time
-> app notices foods that appear before discomfort
-> app labels them `可能相关`
-> user opens related records and decides what to watch
```

## 5. Open UX Questions

1. Should onboarding force a first profile item, or allow immediate use without setup?
2. Should `查食物` results be saved by default or only when the user chooses?
3. Should symptom review be a separate screen or embedded immediately after saving?
4. Is `档案` understandable as a personal food reaction profile, or should it become warmer before the first clickable prototype?
5. How much original image data should be retained for food records, compared with report images?
