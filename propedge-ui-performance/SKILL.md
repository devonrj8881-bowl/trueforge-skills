---
name: propedge-ui-performance
description: "[Codex] Design, implement, review, and performance-tune PropEdge user interfaces where visual identity, betting-data clarity, accessibility, responsiveness, or runtime speed matter. Do not use for backend-only work with no user-facing UI impact."
---

# PropEdge UI + Performance

Use this as the default workflow for PropEdge frontend work. Combine design judgment, production UI engineering, and evidence-based optimization in one loop.

## 1. Establish the PropEdge job

Before editing code, identify:

- The user and the decision the screen supports.
- The primary action or conclusion the user should reach.
- The data that must be trusted at a glance: player, market, line, odds, edge, confidence, timestamp, source, and status.
- The success measure: faster scanning, clearer comparison, better explanation of a ranking, fewer errors, or a measured performance target.

Ground decisions in the existing repository and design system. Preserve unrelated user changes.

## 2. Define a deliberate visual direction

Create a compact plan before implementation:

- Palette: semantic surface, text, border, positive, warning, negative, and accent tokens.
- Type: purposeful display, body, and data/utility roles with a clear hierarchy.
- Layout: information priority and scanning pattern for desktop and mobile.
- Signature: one memorable visual element tied to PropEdge's analytical world, such as a meaningful ranking or market-state treatment.

Use realistic PropEdge content rather than placeholder copy. Avoid generic dashboard grids, purple gradients, excessive rounding, heavy shadows, decorative numbering, and visual effects that do not improve comprehension. Spend boldness in one signature element and keep the rest disciplined.

Critique the plan before coding: if it could belong to any analytics product, revise the part that is not specific enough to PropEdge.

## 3. Engineer focused, accessible UI

- Prefer small composable components over configuration-heavy components.
- Separate data fetching and state orchestration from presentational components.
- Choose state deliberately: local state for local UI, URL state for shareable filters, server cache for remote data, and global state only when genuinely shared.
- Keep component files focused; split components approaching 200 lines.
- Use semantic HTML, real buttons and form labels, visible keyboard focus, correct heading order, and ARIA only where needed.
- Never use color as the only signal for edge, confidence, injury, availability, or error. Pair color with text, icons, patterns, or labels.
- Provide meaningful loading, error, empty, stale-data, and retry states.
- Handle focus when dialogs, filters, and dynamically updated results change.
- Design mobile-first and verify at 320px, 768px, 1024px, and 1440px. Respect `prefers-reduced-motion`.

Use optimistic updates only when rollback behavior is clear and correctness is preserved.

## 4. Measure before optimizing

For performance work, establish a baseline before changing code. Select measurements based on the symptom:

- Initial load: TTFB, LCP, render-blocking resources, bundle and image weight.
- Interaction lag: INP, long tasks over 50ms, event handlers, and component render cost.
- Scroll or large result sets: DOM size, layout/paint work, list rendering, and memory.
- Data loading: API timing, payload size, waterfalls, duplicate requests, N+1 queries, and cache behavior.

Use repeatable synthetic measurements and real-user data when available. PropEdge defaults are LCP <= 2.5s, INP <= 200ms, CLS <= 0.1, initial JavaScript < 200 KB gzipped, and API response time < 200ms at p95, unless the repository defines stricter budgets.

## 5. Fix only the measured bottleneck

Change one material thing at a time and preserve behavior. Choose the simplest fix supported by evidence:

- Split heavy or rarely used routes and analytics views.
- Paginate, virtualize, or lazy-mount large prop/result collections when profiling shows rendering cost.
- Give images dimensions; use responsive formats and lazy loading below the fold.
- Remove duplicate requests, N+1 queries, unbounded fetches, and avoidable payload fields.
- Stabilize props or memoize expensive work only when profiling shows unnecessary renders or computation.
- Use caching only when freshness and invalidation semantics are explicit.

Do not add `React.memo`, `useMemo`, virtualization, caching, or animation optimizations by habit.

## 6. Verify, decide, and guard

Re-measure using the same command, environment, cache state, sample count, and budget as the baseline. Confirm tests and accessibility remain green.

- Improved beyond normal run-to-run variance and behavior is correct: keep it.
- No measurable improvement: revert it.
- Worse or behavior regressed: revert it.
- A test was weakened, skipped, or deleted to claim a win: treat it as a regression.

Record kept and reverted experiments in the PR or a repository performance ledger so failed ideas are not repeated. Add or update tests, bundle checks, Lighthouse/telemetry checks, and accessibility checks when the project supports them.

## Completion checklist

- [ ] The UI's primary PropEdge decision and action are clear.
- [ ] Visual choices are intentional, distinctive, and derived from real product content.
- [ ] Keyboard, focus, contrast, semantics, reduced motion, and non-color status cues work.
- [ ] Loading, error, empty, stale, and responsive states are handled.
- [ ] The actual performance bottleneck was measured before optimization.
- [ ] Before/after results use comparable conditions and beat variance.
- [ ] Existing behavior and tests remain correct.
- [ ] Useful performance and accessibility guards are in place.
