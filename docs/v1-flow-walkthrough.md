# Food Sense V1 Flow Walkthrough

Version: V0.1
Date: 2026-06-15

This document walks through four real user paths before app scaffolding.

It answers:

- Which pages are minimally needed?
- Which fields are required?
- What can wait?
- Which copy must stay cautious?
- Where should each button go?

## 1. Walkthrough Summary

The four paths still matter. They serve different purposes:

1. Supermarket / packaged food: validates `能吃吗`.
2. Hot pot / complex meal: validates fast, realistic food logging.
3. Discomfort after eating: validates symptom logging and review.
4. Hospital report: validates food profile setup, but can be partly postponed.

The first build should fully support paths 2 and 3, support path 1 with text-first matching, and only provide a lightweight/manual version of path 4.

## 2. Path 1: Supermarket / Packaged Food

User story:

```text
I am holding a packaged food and want to know whether the visible ingredients contain something from my food profile.
```

### 2.1 Minimum Pages

Required for first build:

1. `+` action sheet
2. `能吃吗`
3. `能吃吗结果`
4. optional save into `记录`

### 2.2 Required Fields

First build:

- Ingredient/menu text input.
- Context:
  - package
  - menu
  - delivery
  - restaurant
  - homemade
  - other
- Time, auto-filled.

Later:

- Photo upload.
- Camera capture.
- AI/OCR extraction.

### 2.3 First Build Behavior

First build should use local text matching:

```text
Pasted text
-> compare against food profile names and aliases
-> show matched items and matched text
```

Result states:

- `发现需要注意的项目`
- `暂未发现明显命中`
- `信息不足`

### 2.4 Cautious Copy

Use:

- `基于目前可见信息`
- `发现需要注意的项目`
- `暂未发现明显命中`
- `信息不足，建议补充配料或询问商家`

Avoid:

- `安全`
- `放心吃`
- `你对这个过敏`
- `这个一定会导致不舒服`

### 2.5 Button Map

```text
+ -> 能吃吗
能吃吗 / 开始检查 -> 能吃吗结果
能吃吗结果 / 保存为记录 -> 记录
能吃吗结果 / 添加到观察 -> 食物档案详情
能吃吗结果 / 再检查一次 -> 能吃吗
```

### 2.6 First Build Decision

Recommended:

- Build this as text-first.
- Show photo/upload controls only if they are clearly marked as coming later, or hide them until AI is ready.

## 3. Path 2: Hot Pot / Complex Meal

User story:

```text
I am eating a complex meal and do not want to record every single dish.
```

### 3.1 Minimum Pages

Required for first build:

1. `+` action sheet
2. `记吃了什么`
3. `记录`
4. `首页` recent activity preview

### 3.2 Required Fields

Must have:

- Time, auto-filled but editable.
- Text description.
- Scene:
  - home
  - restaurant
  - delivery
  - supermarket
  - other
- Tags:
  - `锅底`
  - `蘸料`
  - `饮料`
  - `甜品`
  - `加工食品`

Nice later:

- Photo attachment.
- AI food tag extraction.
- Meal templates.

### 3.3 First Build Behavior

First build should make one-line logging feel acceptable:

```text
火锅：牛肉、虾滑、豆腐、青菜、蘸料
```

The app should not pressure the user to be complete.

### 3.4 Cautious Copy

Use:

- `简单写一下就可以`
- `复杂餐可以先记一条`
- `容易漏记`

Avoid:

- Any copy that makes the user feel the record is invalid unless complete.

### 3.5 Button Map

```text
+ -> 记吃了什么
记吃了什么 / 保存记录 -> 记录
记录 item -> 记录详情 or edit form
首页 recent item -> 记录详情 or 记录
```

### 3.6 First Build Decision

Recommended:

- Fully build this path in the first implementation slice.
- Start with text-first records and tags.
- Do not require photos.

## 4. Path 3: Discomfort After Eating

User story:

```text
I feel uncomfortable after eating and want to quickly save what happened and see what I ate before it.
```

### 4.1 Minimum Pages

Required for first build:

1. `+` action sheet
2. `记录不舒服`
3. `症状后回看`
4. `记录`
5. optional `食物档案详情` when marking a food as observing

### 4.2 Required Fields

Must have:

- Start time, auto-filled but editable.
- Symptom type:
  - abdominal pain
  - bloating
  - diarrhea
  - nausea
  - skin reaction
  - other
- Severity.
- Duration, optional.
- Notes, optional.

### 4.3 First Build Behavior

After saving, immediately show food records before the symptom:

```text
2 hours
4 hours
8 hours
24 hours
```

The review should show:

- Food record time.
- Food description.
- Tags.
- Any matched food profile items, if available.

### 4.4 Cautious Copy

Use:

- `这些记录出现在不舒服之前`
- `不代表一定导致症状`
- `可能值得继续观察`
- `可与医生讨论`

Avoid:

- `原因`
- `导致`
- `罪魁祸首`
- `过敏源`

### 4.5 Button Map

```text
+ -> 记录不舒服
记录不舒服 / 保存并回看 -> 症状后回看
症状后回看 / 2h 4h 8h 24h -> update visible records
症状后回看 / 标记为继续观察 -> 食物档案详情
症状后回看 / 查看完整记录 -> 记录
```

### 4.6 First Build Decision

Recommended:

- Fully build this path in the first implementation slice.
- This is one of the strongest product moments.

## 5. Path 4: Hospital Report to Food Profile

User story:

```text
I have a hospital or lab report and want to turn its food items into my food profile.
```

### 5.1 Minimum Pages

First build:

1. `食物档案`
2. `食物档案详情 / 添加项目`

Optional after core loop:

1. `报告提取确认`
2. AI upload consent UI

### 5.2 Required Fields

Manual first build:

- Food or ingredient name.
- Aliases.
- Status:
  - `需要避开`
  - `正在观察`
  - `不确定`
- Source:
  - manual
  - report
  - product
  - user observation
- Notes.

Later:

- Report image.
- Extracted rows.
- Result level.
- Test value.
- Include checkbox.

### 5.3 First Build Behavior

Recommended first build:

```text
User manually adds report items one by one
-> source can be set to report
-> items immediately become usable in checks and symptom review
```

This is less magical, but more reliable and safer for the first local-first build.

### 5.4 Cautious Copy

Use:

- `从报告手动添加`
- `报告信息由你确认后保存`
- `保存的是结构化结果`

Avoid:

- `自动诊断`
- `医学结论`
- `一定不能吃`

### 5.5 Button Map

```text
食物档案 / 添加 -> 食物档案详情
食物档案详情 / 保存 -> 食物档案
食物档案 / 导入报告 -> later or manual report entry explanation
报告提取确认 / 确认加入食物档案 -> 食物档案
```

### 5.6 First Build Decision

Recommended:

- Postpone real OCR and AI extraction.
- Keep source=`report` in manual add/edit so report-based items are still supported.

## 6. MVP Page Reduction

The 13 low-fidelity views reduce into this first build set:

### Build Now

1. 首页
2. + 快捷动作面板
3. 记录时间线
4. 食物档案
5. 食物档案详情 / 添加项目
6. 记吃了什么
7. 记录不舒服
8. 症状后回看
9. 隐私与数据
10. 能吃吗 text-first
11. 能吃吗结果

### Build Lightly

1. 发现
   - Empty state plus simple local summaries.

2. 报告提取确认
   - Not needed for the first core loop.
   - Can be represented by manual report-source entries.

### Postpone

1. Real OCR.
2. Real image understanding.
3. Backend AI calls.
4. Cloud sync.
5. Public launch features.

## 7. App Scaffolding Direction

Recommended stack:

- React
- TypeScript
- Vite
- Mobile-first CSS
- Local storage first, with IndexedDB preferred for structured data
- Mock/sample data for initial visual states
- No AI integration in the first app slice

## 8. Product Owner Next Step

The product owner should confirm:

1. Are paths 2 and 3 the first fully polished flows?
2. Should path 1 be text-first for now?
3. Should path 4 be manual-first for now?
4. Should UI direction move forward as `clean utility with soft warmth`?

Recommended answer:

```text
Yes to all four.
```
