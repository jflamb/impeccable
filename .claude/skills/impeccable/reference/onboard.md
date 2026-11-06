> **Additional context needed**: the "aha moment" you want users to reach, and users' experience level.

Get users to first value as fast as possible. Onboarding's job is not to teach the product. Its job is to get people to the moment that proves the product is worth their time. The patterns (welcome steps, empty states, contextual hints, short tours, sample data, progressive disclosure) are standard; apply them from what you know. This file is the procedure.

## 1. Define the target

From PRODUCT.md and the code, state: the aha moment, the one key action that reaches it, the minimum a user must learn to get there, and the users' experience level and motivation. If the aha moment or the audience is not knowable from the repository and request, ask once (AskUserQuestion tool); these are intent questions.

## 2. Map the current path

Walk the first-run path in the real product and note every step between arrival and the aha moment: required fields, blank screens, unexplained concepts, dead ends, and places where a returning user would be shown first-run material again.

## 3. Design the shortest path

- Remove or defer every step the key action does not need; collect extra information later.
- Teach inside the real product, at the point of use, one concept at a time. No separate tutorial mode.
- Turn each empty state into the next step: what will appear here, why it matters, and a clear action (create, import, start from a template). Distinguish first use, user-cleared, no results, no permission, and load failure.
- Use a guided tour only for a genuinely complex workflow: three to seven steps, interactive, skippable, replayable.
- Keep skip visible, record completion and dismissals, and never show the same onboarding twice.

**NEVER**: force a long sequence before the product is usable, patronize with obvious explanations, block the whole UI during a tour, or hide the skip option.

## 4. Verify

Run the path end to end as a new user and as a returning user, within SKILL.md's two-round inspection cap. Report the number of steps to the aha moment before and after.

When users hit the aha moment fast and don't drop off, hand off to `/impeccable polish` for the final pass.
