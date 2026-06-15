# User Journey V0.1

## Core Journey

```text
User sees or eats food
-> User checks or records it
-> User records discomfort if it happens
-> Food Sense helps review prior food records
-> Food Sense gradually shows recurring patterns
```

## Scenario 1: Supermarket Product

1. User picks up a packaged food in a supermarket.
2. User wonders: `这个我能吃吗？`
3. User taps `+` and chooses `查食物`.
4. User takes a photo of the ingredient list.
5. Food Sense extracts text and compares it with the user's personal food profile.
6. Food Sense shows matched ingredients and explains the reason.
7. User decides whether to buy or avoid the product.

## Scenario 2: Delivery or Restaurant Menu

1. User is ordering food or looking at a restaurant menu.
2. User uploads a screenshot or photo.
3. Food Sense scans dish names, descriptions, and visible ingredient text.
4. Food Sense flags known or related ingredients where visible.
5. If the information is incomplete, Food Sense asks for more detail or suggests asking the seller.

## Scenario 3: Hot Pot or Complex Meal

1. User is eating hot pot with friends.
2. User does not want to record every dish separately.
3. User chooses `记饮食`.
4. User takes one photo of the table, menu, or order list.
5. User adds a short note such as `牛肉、虾滑、豆腐、青菜、蘸料`.
6. Food Sense suggests tags like `锅底`, `蘸料`, `饮料`, `甜品`, `加工食品`.
7. The record is saved as one complex meal.

## Scenario 4: Symptom Review

1. User feels abdominal pain a few hours after eating.
2. User chooses `记不适`.
3. User records time, symptom type, severity, duration, and notes.
4. Food Sense immediately shows foods recorded in the last 2, 4, 8, and 24 hours.
5. Food Sense highlights known profile matches and repeated foods.
6. User can mark items worth observing.

## Scenario 5: New User Without a Report

1. User starts using Food Sense without a hospital report.
2. User skips profile setup.
3. User records meals and discomfort for several days.
4. Food Sense detects foods that appear repeatedly before discomfort.
5. Food Sense suggests continued observation instead of diagnosis.

## Scenario 6: User With a Report

1. User opens the food profile area.
2. User uploads photos of a hospital or lab report.
3. Food Sense extracts food names, values, and result levels.
4. User confirms or edits the extracted list.
5. Confirmed items become part of the user's personal food profile.
6. Future checks and food logs can use this profile.
