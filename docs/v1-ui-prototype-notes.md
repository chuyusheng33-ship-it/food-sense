# Food Sense V1 UI Prototype Notes

Version: V0.3
Date: 2026-06-18

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
- Whether the Apple-style foundation still leaves Food Sense with its own warm food-observation identity.

## Included Screens

1. 首页
2. 查食物
3. 检查结果
4. 记饮食
5. 选择饮食记录
6. 记症状
7. 饮食回看
8. 记录
9. 档案
10. 隐私与数据

## Interaction Level

The prototype supports light click-through navigation:

- Home actions open their related flows.
- `记饮食` can open `选择饮食记录` and copy a past meal into an editable draft.
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

- Apple-style grouped mobile app direction.
- Food Sense-specific visual identity defined in `docs/DESIGN.md`.
- Light iOS-like gray app background.
- Rounded white grouped surfaces with subtle hairline borders.
- Reduced shadows and less decorative hero treatment.
- Home primary actions use an iOS-like grouped list rhythm instead of custom promo cards.
- Home primary actions now include short support lines to make the three core jobs clearer without adding a dashboard.
- Home iconography is tuned toward food observation and personal recording instead of generic app utilities.
- Context cards use white grouped surfaces with subtle semantic markers instead of large tinted gradients.
- Soft olive primary accent.
- Sage for food/profile context.
- Mist blue for neutral information and privacy/data moments.
- Amber/rust for attention and stronger symptom/result states.
- Translucent bottom navigation.
- Compact mobile-first layout.
- System-first Chinese typography, matching the V1 design system.

Language direction:

- Use `可能相关`, `建议继续观察`, `信息不足`, and `基于目前可见信息`.
- Do not use `安全`, `放心吃`, `过敏`, or `一定导致`.

## Feedback To Collect

Before moving to formal development, review:

1. Does the homepage feel clear or still too busy?
2. Do the three home action subtitles help first-time clarity without making the page feel heavy?
3. Does the expanded soft olive palette feel richer without becoming noisy?
4. Do the result cards feel calm enough but still noticeable?
5. Is `档案` understandable as a bottom navigation label?
6. Does the Apple-style foundation now feel like Food Sense rather than a generic utility app?

## Next Step After Approval

If the product owner approves the prototype direction, the next step is to create the development boundary docs:

- `docs/DESIGN.md`
- `docs/ARCHITECTURE.md`
- `TODO.md`

Then formal app development can begin in small tested slices.
