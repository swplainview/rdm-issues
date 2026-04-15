---
project: seedling-swapper
title: Memoize context provider values to prevent unnecessary re-renders
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #10 (priority: medium).

Context provider value objects are recreated on every render, causing all consumers to re-render unnecessarily.

**Locations**
- `packages/frontend/src/hooks/useListings.tsx:56`
- `packages/frontend/src/hooks/useAuth.tsx:101-103`
- `packages/frontend/src/hooks/useSwap.tsx:50`
- `packages/frontend/src/hooks/useClaims.tsx:55`

**Fix**
Wrap each provider's value object in `useMemo` with appropriate dependency arrays.
