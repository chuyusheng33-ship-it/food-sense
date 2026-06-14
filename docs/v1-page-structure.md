# Food Sense V1 Page Structure

Version: V0.1
Date: 2026-06-14

This document defines the first low-fidelity page structure for Food Sense V1.

The goal is not visual design yet. The goal is to decide what each screen needs to contain, how users move between screens, and what information must be visible for the first private test.

## 1. Navigation Model

V1 uses a mobile-first bottom navigation:

```text
首页 / 记录 / + / 食物档案 / 发现
```

The center `+` opens the three primary actions:

```text
能吃吗
记吃了什么
记录不舒服
```

`食物档案` is a temporary working name. It contains foods and ingredients the user needs to avoid, is observing, or has imported from reports.

## 2. Screen List

V1 low-fidelity screens:

1. 首页
2. + 快捷动作面板
3. 能吃吗
4. 能吃吗结果
5. 记吃了什么
6. 记录不舒服
7. 症状后回看
8. 记录时间线
9. 食物档案
10. 食物档案详情 / 添加项目
11. 报告提取确认
12. 发现
13. 隐私与数据

## 3. Screen Details

### 3.1 首页

Purpose:

- Give the user a calm starting point.
- Surface the most useful next action.
- Show recent signals without claiming diagnosis.

Primary content:

- Today summary: meals recorded, checks done, symptoms recorded.
- Main prompt: `今天想先做什么？`
- Three action shortcuts: `能吃吗`, `记吃了什么`, `记录不舒服`.
- Recent activity preview.
- Gentle reminder if food profile is empty.
- Link to privacy and local data settings.

Empty state:

- If the user has no profile and no records, show a simple setup path:
  - Add food manually.
  - Import report.
  - Skip and start recording.

Language boundary:

- Avoid medical certainty.
- Use `记录`, `观察`, `可能相关`.

### 3.2 + 快捷动作面板

Purpose:

- Make the three core actions reachable from anywhere.

Primary content:

- Action sheet with:
  - `能吃吗`: scan food, menu, package, or ingredients.
  - `记吃了什么`: save a meal, snack, drink, sauce, or complex meal.
  - `记录不舒服`: save symptoms and review prior food.
- Close control.

Behavior:

- Opens as a bottom sheet over the current tab.
- Choosing an action opens the relevant flow.

### 3.3 能吃吗

Purpose:

- Check visible food information against the user's food profile.

Input methods:

- Take photo.
- Upload image.
- Paste text.

Primary fields:

- Image or text input.
- Optional context: package, menu, delivery, restaurant, homemade, other.
- Consent notice before any AI upload:
  - What will be uploaded.
  - Why it is needed.
  - What will be saved locally.

Primary action:

- `开始检查`

Secondary actions:

- Save as food record after check.
- Cancel.

### 3.4 能吃吗结果

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

### 3.5 记吃了什么

Purpose:

- Make real-life food logging fast enough that users will actually do it.

Input methods:

- Take photo.
- Upload image.
- Text note.

Primary fields:

- Time.
- Description.
- Scene: home, restaurant, delivery, supermarket, other.
- Optional tags: sauce, seasoning, drink, dessert, processed food.
- Extracted food tags, if AI or manual parsing is available.

Complex meal support:

- Allow one photo plus one sentence.
- Prompt for commonly forgotten parts:
  - `锅底`
  - `蘸料`
  - `饮料`
  - `甜品`
  - `加工食品`

Primary action:

- `保存记录`

### 3.6 记录不舒服

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
- Severity.
- Duration.
- Notes.

Primary action:

- `保存并回看`

### 3.7 症状后回看

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

### 3.8 记录时间线

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
- Entry detail view.

Primary actions:

- Add new record through `+`.
- Edit or delete an entry.

### 3.9 食物档案

Purpose:

- Store the user's personal foods and ingredients to avoid, observe, or keep uncertain.

Primary content:

- Status tabs:
  - `需要避开`
  - `正在观察`
  - `不确定`
- Search.
- Food cards with:
  - name
  - aliases / hidden ingredients
  - source
  - latest note
- Empty state for:
  - Add manually.
  - Import report.

Primary actions:

- Add food or ingredient.
- Import report.

### 3.10 食物档案详情 / 添加项目

Purpose:

- Let the user create and refine one profile item.

Fields:

- Food or ingredient name.
- Aliases / hidden names.
- Status: avoid, observe, uncertain.
- Severity or report level, if known.
- Test value, if known.
- Source.
- Notes.

Primary actions:

- Save.
- Delete.

### 3.11 报告提取确认

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

### 3.12 发现

Purpose:

- Show non-diagnostic patterns that may help the user observe over time.

Primary content:

- Possible recurring foods before symptoms.
- Profile items recently detected in checks or logs.
- Meals worth reviewing.
- Foods newly worth observing.

Required caveats:

- Findings are based on local records.
- Findings are not medical diagnosis.
- Suggested wording:
  - `可能相关`
  - `建议继续观察`
  - `可在复诊时与医生讨论`

Empty state:

- Explain that findings need several food and symptom records.

### 3.13 隐私与数据

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
首页 or +
-> 能吃吗
-> photo / image / text
-> consent if AI upload is needed
-> result
-> optional save as food record
```

### 4.2 Log Complex Meal

```text
首页 or +
-> 记吃了什么
-> photo plus short note
-> optional tags for sauce / drink / dessert / processed food
-> save
-> 记录时间线
```

### 4.3 Record Symptom and Review

```text
首页 or +
-> 记录不舒服
-> save symptom
-> 症状后回看
-> choose 2h / 4h / 8h / 24h
-> mark food as continue observing
```

### 4.4 Build Food Profile

```text
食物档案
-> add manually or import report
-> confirm items
-> future checks and logs use profile
```

## 5. Open UX Questions

1. Should onboarding force a first food profile item, or allow immediate use without setup?
2. Should `能吃吗` results be saved by default or only when the user chooses?
3. Should symptom review be a separate screen or embedded immediately after saving?
4. Is `食物档案` understandable enough for private testers, or should it become warmer before the first clickable prototype?
5. How much original image data should be retained for food records, compared with report images?
