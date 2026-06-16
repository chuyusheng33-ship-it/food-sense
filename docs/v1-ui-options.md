# Food Sense V1 UI Options

Version: V0.2
Date: 2026-06-16

This document records the first static UI direction options for Food Sense V1.

Preview file:

```text
design/ui-directions/v1-ui-options.html
```

Selected reference:

```text
design/ui-references/food-sense-v1-soft-olive-reference.png
```

## Purpose

These options are not the final app.

They are static visual mockups used to choose the product's first visual direction before building the React/Vite app.

## Options

### 1. Warm Utility

Warm, restrained, and clear.

Strengths:

- Closest to the current V1 UI direction.
- Good balance between trust and everyday use.
- Warning states feel noticeable without feeling alarming.

Risk:

- May feel a little plain if we want more distinct brand personality.

### 2. Quiet Journal

Calm, journal-like, and observation-focused.

Strengths:

- Fits long-term food and symptom review.
- Record calendar feels central and serious.
- Good for users who want a private tracking tool.

Risk:

- Could feel slightly too quiet for quick actions like `查食物`.

### 3. Soft Assistant

Warmer, friendlier, and more assistant-like.

Strengths:

- More approachable for first-time users.
- Home screen feels light and easy to enter.
- Could make logging feel less heavy.

Risk:

- Needs careful handling so serious states do not feel too casual.

## Recommendation

Start from Option 1, then apply the uploaded soft olive mobile reference as the visual anchor.

Option 1 is the safest foundation for V1 private testing because it is clear, warm, and unlikely to overstate medical certainty.

Option 2 is the best alternative if the product should feel more like a private health journal.

Option 3 is useful if first-time approachability becomes more important than restraint.

## Product Owner Preference

On 2026-06-16, the product owner shared a mobile UI reference and said this style feels good.

Extracted direction for Food Sense:

- Warm light gray app background.
- Rounded white cards.
- Soft olive primary accent.
- Calm bottom navigation.
- Clear search/input surfaces.
- Gentle shadows and enough breathing room.

Adaptation boundary:

- Do not copy the event marketplace content model.
- Do not make Food Sense image-heavy just because the reference uses event cards.
- Use the visual tone, spacing, card softness, and olive accent.
- Keep Food Sense focused on `查食物 / 记饮食 / 记症状`.

## Next Decision

Current working choice:

```text
Warm Utility structure + soft olive reference style
```

Still to confirm during first clickable build:

1. Exact olive shade.
2. Whether home actions should be stacked rows or compact cards.
3. How rounded cards and buttons should feel before becoming too soft.
