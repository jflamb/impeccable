> **Additional context needed**: target platforms/devices and usage contexts.

Adapt an existing design to a different context: another screen size, device, platform, or use case. The trap is treating adaptation as scaling. The job is rethinking the experience for the new context.

**Web only** (mobile web included). This fork ships no native-platform guidance; for an `ios` / `android` / `adaptive` project, apply the platform's own guidelines from general knowledge.

Responsive technique (mobile-first `min-width` queries, content-driven breakpoints, container queries, `pointer`/`hover` media queries, safe-area `env()` insets, `srcset`/`sizes` and `<picture>`, 44px touch targets, print and email constraints) is standard; apply it from what you know. This file is the procedure.

## 1. Assess

- **Source context:** what the design was built for and the assumptions it makes (screen size, mouse and hover, fast connection, focused use).
- **Target context:** device, input method, screen constraints and orientation, connection, usage context (glance vs. focused), and what users expect there. If the target is not stated and not evident from the request, ask once (AskUserQuestion tool).
- **Breakage:** list what won't fit (content, navigation, features), what won't work (hover-only interactions, small targets), and what is inappropriate for the target (desktop patterns on phones, and the reverse).

## 2. Plan

Decide per region how it changes for the target, keeping one information architecture across contexts: what reflows, what collapses behind progressive disclosure, what navigation becomes, how tables and dense data render, and what the primary action looks like within thumb reach. Choose breakpoints where this content breaks, not by device list.

## 3. Implement

Work in the project's existing layout system and tokens. Reflow with grid and flex or container queries, key interaction affordances to input capability rather than screen width, keep every core function available on every target, handle safe areas and landscape, and serve appropriately sized media. Type sizing follows the visitor mode: fixed `rem` on app and Operate screens, fluid `clamp()` allowed on Persuade pages.

**NEVER**: hide core functionality on small screens, rely on hover for anything essential, use device detection instead of feature detection, or fork the information architecture between contexts.

## 4. Verify

Check the target widths and orientations (including 320px and very wide screens) and each input method in one batched round, fix in one batch, and confirm with at most one more round, per SKILL.md's cap. Say which evidence came from emulation and which from real devices.

When the adaptation feels native to each context, hand off to `/impeccable polish` for the final pass.
