---
project: seedling-swapper
title: Parallelize independent API calls in UserProfilePage
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #8 (priority: medium).

At `packages/frontend/src/pages/UserProfilePage.tsx:80-95`, the profile fetch and follow-status fetch run sequentially despite being independent.

**Fix**
Use `Promise.all` to run both fetches concurrently:

```typescript
const [profile, followStatus] = await Promise.all([
  api.get<UserProfile>(`/users/${id}`),
  me && !isOwnProfile ? api.get<{ following: boolean }>(`/users/${id}/follow`) : null,
]);
```
