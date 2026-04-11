---
project: seedling-swapper
title: Allow users to change their password
status: done
priority: medium
created: 2026-04-11
completed: 2026-04-11
commit: 19331c8db195ec32cd21cc4a067df6ae0fd7d53a
---

Authenticated users should be able to change their password. UI lives in account settings/profile. Requires current password confirmation before accepting the new one. Only applicable to accounts with a passwordHash (not Google OAuth-only accounts).
