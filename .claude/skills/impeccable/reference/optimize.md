Performance is a feature. Identify the actual bottleneck for THIS interface, fix it, then measure. Don't optimize what isn't slow. The techniques (image formats and `srcset`, code splitting, font subsetting, batching layout reads and writes, `content-visibility`, virtualization, Core Web Vitals targets of LCP < 2.5s, INP < 200ms, CLS < 0.1) are standard; apply them from what you know. This file is the procedure.

## 1. Measure

Record a baseline before changing anything: Lighthouse or the browser's performance panel on the target, Core Web Vitals, bundle and asset sizes, request count, and, for interaction problems, a trace of the slow interaction. Measure with mobile throttling, not only fast desktop.

## 2. Find the bottleneck

Name what is slow (initial load, an interaction, an animation, scrolling), what causes it (an oversized image, a blocking script, a heavy dependency, layout thrashing, re-renders, an unbounded list), how bad it is, and who it affects. Rank by user-facing impact and work the top item first.

## 3. Fix

Make the smallest change that removes the named cause, in the project's existing build and framework conventions. Typical moves: right-size and lazy-load below-the-fold media (never the LCP element), split or defer non-critical code, preload what the first viewport needs, reserve space for media and embeds, animate `transform` and `opacity` rather than layout properties, bound expensive paint effects, virtualize long lists, and cut unnecessary re-renders.

**NEVER**: optimize without a measurement, sacrifice accessibility or break functionality for speed, lazy-load above-the-fold content, scatter `will-change`, or chase micro-optimizations while a major bottleneck stands.

## 4. Verify

Re-run the same measurement and report before and after numbers for the metrics you targeted. Confirm nothing regressed functionally. Stay within SKILL.md's two-round inspection cap.

When the user-facing numbers move, hand off to `/impeccable polish` for the final pass.
