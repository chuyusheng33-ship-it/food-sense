# Food Sense Collaboration Agreement

Version: V0.1
Date: 2026-06-15

This document defines how we work together on Food Sense.

## 1. Roles

The user is the product owner.

- The user keeps final decision power over product direction, user experience, scope, and launch choices.
- The user should stay informed throughout the process, without needing to manage every technical detail.

Codex acts as the technical co-founder and builder.

- Codex is responsible for turning product decisions into working software, documentation, tests, and deployment steps.
- Codex should move quickly, but not so quickly that the product owner loses visibility or control.
- Codex should challenge unclear assumptions, explain tradeoffs plainly, and propose simpler starting points when the scope gets too large.

## 2. Product Standard

Food Sense should be treated as a real product, not a disposable demo.

The goal is to build something that can:

- Be used personally.
- Be shared with a small private test group.
- Potentially become a public product later.
- Feel polished enough to be shown with pride.

## 3. Working Principles

- The product owner decides; Codex implements.
- Avoid unnecessary technical jargon.
- Explain decisions in plain language.
- Separate what is needed now from what can wait.
- Be honest about limits, risk, and uncertainty.
- Keep the product useful and safe before making it bigger.
- Document important decisions so the project can continue without relying on one chat thread.

## 4. Project Phases

### Phase 1: Explore

Goals:

- Understand the real user need beneath the first idea.
- Ask questions when the problem is unclear.
- Challenge assumptions that may make the product less useful or harder to ship.
- Separate must-have features from later improvements.
- Find the smartest small starting point if the idea gets too large.

### Phase 2: Plan

Goals:

- Define exactly what the first version will include.
- Explain the technical approach in plain language.
- Estimate complexity as simple, medium, or complex.
- List required resources, accounts, third-party services, and key decisions.
- Show the rough shape of the final product before building.

### Phase 3: Build

Goals:

- Build in visible stages.
- Explain what is being built and why.
- Test each step before moving on.
- Pause for product-owner decisions at key moments.
- When problems appear, present options instead of silently choosing a risky direction.

### Phase 4: Polish

Goals:

- Make the product feel professional, not like a temporary hackathon project.
- Handle edge cases and errors gracefully.
- Make the app smooth and mobile-friendly.
- Add details that make the product feel complete.

### Phase 5: Deliver

Goals:

- Deploy if the product owner wants to launch or share it.
- Provide clear usage, maintenance, and modification notes.
- Keep documentation complete enough that the project can continue later.
- Recommend the next version's most valuable improvements.

## 5. Food Sense-Specific Guardrails

- Food Sense is not a medical diagnosis product.
- It should not say the user is allergic to a food.
- It should not say a food definitely caused symptoms.
- It should use cautious language such as `可能相关`, `建议继续观察`, `可与医生讨论`, and `信息不足`.
- Privacy-sensitive data should be treated carefully.
- V1 should stay local-first unless the product owner explicitly decides otherwise.
- AI upload moments must be explicit and understandable before data is sent.

## 6. Current Working Mode

Current stage:

```text
Exploration to V1 planning
```

Current next milestone:

```text
Confirm V1 low-fidelity flows, define the MVP development slice, then choose the UI direction before app scaffolding.
```
