Designs that only work with perfect data aren't production-ready. Harden the interface against the inputs, errors, languages, and network conditions that real users will throw at it. The techniques (truncation and `min-width: 0`, logical properties, `Intl`, plural rules, retry states, debouncing, and so on) are standard; apply them from what you know. This file is the procedure.

## 1. Assess

Read the target and list where it breaks. Check each of these against the real code, not in the abstract:

- **Content extremes:** very long and very short text, empty values, emoji, accents, RTL and CJK scripts, large numbers, 1000+ items, no data at all.
- **Failure paths:** offline, slow, and timed-out requests; each API error class the code can receive (validation, auth, permission, not found, rate limit, server); concurrent or repeated submits.
- **Internationalization:** 30–40% text expansion, RTL mirroring, locale date, number, and currency formats, plural rules.
- **States:** loading (initial, paginated, refresh), empty (no items, no results), permission (view, edit, read-only), partial failure of one component.
- **Access:** keyboard-only paths, focus management, live-region announcements, forced-colors mode, 200% zoom.

## 2. Fix

Work in the project's existing patterns and components; do not introduce a new error or loading system when one exists.

- Containers grow with content; no fixed widths on text. Long strings truncate or wrap deliberately, with the full value reachable.
- Type follows the visitor mode: fixed `rem` sizes on app and Operate screens; fluid `clamp()` sizing is allowed only on Persuade pages. Body text never drops below 16px on mobile (iOS zooms focused inputs below that); 14px only for genuinely secondary text.
- Every error state says what happened and offers the next step (retry, fix the field, contact support), keeps the user's input, and never blocks the whole interface when one component fails.
- Validation is inline, specific, and near the field; server-side validation is still assumed.
- Repeated submits are prevented; optimistic updates roll back on failure.
- Use `Intl` and the project's i18n library for formatting and plurals; logical CSS properties for direction.

**NEVER**: assume perfect input, ship generic "Error occurred" messages, trust client-side validation alone, assume English-length text, or let one failing component take down the page.

## 3. Verify

Exercise the fixes with real edge data: a 100+ character name, emoji in every field, an RTL and a CJK string, network disabled and throttled, 1000+ items, rapid repeated submits, forced API errors, and every empty state. Stay within SKILL.md's two-round inspection cap.

When edge cases are covered, hand off to `/impeccable polish` for the final pass.
