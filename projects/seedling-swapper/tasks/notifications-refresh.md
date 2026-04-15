---
project: seedling-swapper
title: Add refresh mechanism to NotificationsBell
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #12 (priority: medium).

At `packages/frontend/src/components/NotificationsBell.tsx:27-32`, notifications are fetched once on mount with no polling or refetch trigger. Users see stale notifications until they reload the page.

**Fix**
Refetch when the dropdown is opened (simplest approach), or add polling on a reasonable interval (e.g. 30s). Real-time via WebSocket/SSE is a stretch goal.
