# Food Sense V1 Design System

Version: V0.1
Date: 2026-06-18

This document defines the V1 visual identity system for Food Sense.

It translates the confirmed direction into practical design rules for the upcoming React + TypeScript + Vite PWA build.

## 1. Design Positioning

Food Sense should feel like:

- A calm personal food reaction assistant.
- An iOS-forward mobile utility.
- Warm enough for daily eating situations.
- Careful enough for health-adjacent information.
- Clear about uncertainty.

Food Sense should not feel like:

- A medical diagnosis product.
- A hospital dashboard.
- A nutrition or diet tracker.
- A restaurant, recipe, or food delivery app.
- A playful lifestyle product.

The approved V1 direction is:

```text
Apple/iOS foundation + Food Sense warmth
```

This means the interface keeps native-feeling iOS structure, typography, grouped surfaces, hairline dividers, safe areas, and restrained motion. Food Sense adds a small visual signature through soft olive, food-observation iconography, and semantic color use.

## 2. Product Personality

Use these words as the design filter:

- Calm.
- Useful.
- Trustworthy.
- Warm.
- Plain-spoken.
- Non-diagnostic.

Avoid these tones:

- Cute.
- Clinical.
- Alarmist.
- Trendy.
- Promotional.
- Overly clever.

## 3. Visual Identity

### 3.1 Brand Mark Direction

The V1 mark can stay simple and UI-native.

Recommended direction:

- Rounded iOS-style square.
- Deep olive fill.
- A quiet food-observation symbol inside.
- No mascot, no medical cross, no fork-only restaurant signal.

The symbol should imply:

```text
food + observation + personal record
```

It does not need to become a final logo in V1. It only needs to make the app feel less generic than a plain system utility.

### 3.2 Icon Direction

Use Lucide-style line icons for V1.

Rules:

- Stroke icons only.
- Rounded line style.
- Consistent size and weight.
- Icons support meaning but never replace labels.
- No emojis.
- No decorative food illustrations in core controls.

Recommended primary action icon meaning:

| Action | Meaning |
| --- | --- |
| `查食物` | inspect / scan visible food information |
| `记饮食` | record what was eaten |
| `记症状` | record a body reaction |

## 4. Color System

Food Sense uses a neutral iOS base with a small semantic palette.

### 4.1 Core Tokens

| Role | Token | Hex | Use |
| --- | --- | --- | --- |
| App background | `background` | `#F5F5F7` | iOS-like canvas |
| Surface | `surface` | `#FFFFFF` | grouped lists, cards, forms |
| Soft surface | `surface-soft` | `#F9F9FB` | quiet secondary areas |
| Text | `text` | `#1D1D1F` | primary copy |
| Muted text | `muted` | `#6E6E73` | helper copy and timestamps |
| Faint text | `faint` | `#A1A1A6` | secondary metadata only |
| Hairline | `hairline` | `rgba(60, 60, 67, 0.12)` | iOS-style dividers |
| Border | `border` | `rgba(60, 60, 67, 0.16)` | input and surface outlines |

### 4.2 Brand And Semantic Tokens

| Role | Token | Hex | Use |
| --- | --- | --- | --- |
| Primary olive | `primary` | `#596321` | primary actions, active nav, selected chips |
| Deep olive | `primary-dark` | `#3F4718` | pressed states, strong olive text |
| Olive tint | `primary-soft` | `#EEF1DF` | selected controls and action icons |
| Sage | `sage` | `#DDE5D2` | food/profile context |
| Sage tint | `sage-soft` | `#F0F4E9` | quiet food/profile surfaces |
| Mist blue | `mist` | `#DCE6E8` | neutral information, privacy, no-clear-match |
| Mist tint | `mist-soft` | `#EEF5F5` | neutral notices |
| Warm amber | `amber` | `#D7A245` | moderate attention |
| Amber tint | `amber-soft` | `#FFF5DD` | attention notices |
| Soft rust | `rust` | `#B96B43` | stronger attention, severe symptom level |
| Rust tint | `rust-soft` | `#FFF0E7` | matched item context |
| Clay | `clay` | `#C98F67` | small human warmth accents only |

### 4.3 Color Rules

Use olive for:

- Main CTAs.
- Active bottom navigation.
- Selected chips.
- Brand mark.
- Calm action emphasis.

Do not use olive for:

- `暂未发现明显命中`.
- Anything that could read as `安全`.
- Medical certainty.

Use mist blue for:

- `基于目前可见信息`.
- Privacy and data moments.
- Neutral or incomplete information.
- No-clear-match states.

Use sage for:

- Food record context.
- Profile and known food context.
- Quiet food-related surfaces.

Use amber/rust for:

- Attention states.
- Matched items.
- Medium or severe symptom levels.

Avoid:

- Restaurant red as the brand color.
- Hospital cyan/green as the dominant system.
- Bright emergency red for ordinary warnings.
- Strong green success states for food checks.
- Large gradients.
- A one-color olive interface.

## 5. Typography

### 5.1 Font Stack

Use system-first typography:

```css
font-family:
  ui-sans-serif,
  system-ui,
  -apple-system,
  BlinkMacSystemFont,
  "SF Pro Text",
  "SF Pro Display",
  "PingFang SC",
  "Hiragino Sans GB",
  "Noto Sans SC",
  "Microsoft YaHei",
  sans-serif;
```

Reason:

- It feels native on iOS.
- It keeps Chinese UI text readable.
- It avoids external font loading for V1.
- It matches the mobile PWA performance target.

Do not use handwritten, playful, or editorial serif fonts in the core app.

### 5.2 Type Scale

Recommended V1 scale:

| Role | Size | Weight | Use |
| --- | --- | --- | --- |
| Home title | 31px | 800-850 | `今天要做什么？` |
| Page title | 24px | 800 | task/page headers |
| Section title | 19px | 750-800 | `最近`, `饮食记录` |
| Card title | 16px | 750-800 | meal/profile/result names |
| Body | 14px | 400-500 | explanatory copy |
| Helper | 12-13px | 400-650 | metadata and cautious notes |
| Button | 15-16px | 750-850 | primary actions |

Rules:

- Use weight and spacing before adding color.
- Keep letter spacing at `0`.
- Do not use tiny text for important warnings.
- Let Chinese copy wrap naturally.

## 6. Layout And Surfaces

Use iOS-style grouped structure:

- Single-column mobile layout.
- White grouped surfaces.
- Hairline separators.
- Rounded corners around grouped areas.
- Minimal shadows.
- Safe-area-aware bottom navigation.

Surface rules:

- Cards should feel like grouped iOS surfaces, not marketing cards.
- Avoid nested cards.
- Use separators inside grouped lists instead of boxing every row.
- Keep result and warning areas calm, readable, and close to the relevant content.

## 7. Component Rules

### 7.1 Home Actions

Home has three primary actions:

```text
查食物 / 记饮食 / 记症状
```

Use one grouped list with three rows.

Each row includes:

- A small semantic icon container.
- A clear action label.
- A short support line only when it improves first-use clarity.

The three actions should feel equal.

### 7.2 Result Cards

Result cards should explain evidence, not diagnose.

Each matched item should show:

- Matched item.
- Status.
- Original visible text.
- Reason.
- Suggested next step when useful.

Use language like:

```text
原文：全脂乳粉、乳清蛋白粉
原因：这些名称在你的档案别名中。
```

Do not use:

- Risk scores.
- Safety badges.
- Diagnosis badges.
- Large red alert panels.

### 7.3 Records

Records should be easy to scan by type:

```text
饮食 / 症状 / 检查
```

Do not mix all record types into one undifferentiated feed.

Food records can show:

- Time.
- Photo.
- Recognized or entered food list.
- Matched profile item if any.

### 7.4 Profile

`档案` is a personal reference area.

It should contain:

- `已知需注意`.
- `可能相关`.
- Report/manual/observed sources.

It should not look like a medical diagnosis list.

## 8. Motion And Interaction

V1 motion should be quiet:

- 150-250ms for taps and simple state changes.
- Transform and opacity only.
- No decorative animation.
- Respect `prefers-reduced-motion`.

Tap targets:

- Minimum 44px height.
- Clear pressed/focus state.
- Icon-only buttons must have accessible labels.

## 9. Accessibility Rules

Minimum requirements:

- Normal text contrast at least 4.5:1.
- Important state is not conveyed by color alone.
- All icon-only controls have labels.
- Form fields have visible labels.
- Bottom navigation has icon and text.
- Text can wrap on narrow mobile screens.

## 10. Implementation Boundary

When React development starts:

- Treat this file as the visual source of truth.
- Create design tokens before page components.
- Do not overbuild a large design system before the first real loop works.
- Keep tokens semantic rather than tying components to raw hex values.

The first implementation should prove clarity and trust before visual flourish.
