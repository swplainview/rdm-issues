---
project: seedling-swapper
title: Memoize listing search filter in HomePage
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #13 (priority: low).

At `packages/frontend/src/pages/HomePage.tsx:65-70`, the listing search filter recomputes on every render even when neither `listings` nor `search` has changed.

**Fix**
Wrap in `useMemo` with `[listings, search]` as dependencies.
