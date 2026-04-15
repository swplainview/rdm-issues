---
project: seedling-swapper
title: Wrap AccountPage handlers in useCallback
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #14 (priority: low).

At `packages/frontend/src/pages/AccountPage.tsx:68-140`, handler functions (`handleSaveProfile`, `handleAvatarChange`, `handleChangePassword`) are defined inline without `useCallback`, creating new function references on every render.

**Fix**
Wrap each handler in `useCallback` with appropriate dependency arrays.
