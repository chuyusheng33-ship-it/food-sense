# Food Sense V1 UI Prototype Notes

Version: V0.1
Date: 2026-06-16

Prototype file:

```text
design/prototypes/v1-ui-prototype.html
```

Reference style:

```text
design/ui-references/food-sense-v1-soft-olive-reference.png
```

## Purpose

This prototype is for visual and flow review before formal app development.

It is not the production React app. It does not connect to real storage, AI recognition, or final business logic.

The goal is to let the product owner review:

- Whether the soft olive visual direction feels right for Food Sense.
- Whether the home screen is simple enough.
- Whether the three main actions are clear.
- Whether `查食物`, `记饮食`, `记症状`, `记录`, and `档案` feel coherent together.
- Whether result language avoids medical certainty.
- Whether the app feels like a personal assistant instead of a diagnosis tool.

## Included Screens

1. 首页
2. 查食物
3. 检查结果
4. 记饮食
5. 记症状
6. 症状后回看
7. 记录
8. 档案
9. 隐私与数据

## Interaction Level

The prototype supports light click-through navigation:

- Home actions open their related flows.
- Bottom navigation switches between `首页`, `记录`, and `档案`.
- Route buttons in the side panel jump to each screen.
- Chips and time windows can be selected visually.

The prototype intentionally does not:

- Save real data.
- Run local matching.
- Upload images.
- Use AI.
- Implement final form validation.

## Design Direction Used

Visual direction:

- Warm light gray app background.
- Rounded white cards.
- Soft olive primary accent.
- Calm bottom navigation.
- Gentle shadows.
- Compact mobile-first layout.

Language direction:

- Use `可能相关`, `建议继续观察`, `信息不足`, and `基于目前可见信息`.
- Do not use `安全`, `放心吃`, `过敏`, or `一定导致`.

## Feedback To Collect

Before moving to SDD and formal development, review:

1. Does the homepage feel clear or still too busy?
2. Should the three home actions stay as compact cards, or become larger stacked rows?
3. Does soft olive feel right as the main color?
4. Do the result cards feel calm enough but still noticeable?
5. Is `档案` understandable as a bottom navigation label?
6. Is the overall style close enough to the selected reference?

## Next Step After Approval

If the product owner approves the prototype direction, the next step is to create the development boundary docs:

- `docs/DESIGN.md`
- `docs/ARCHITECTURE.md`
- `TODO.md`

Then formal app development can begin in small tested slices.
