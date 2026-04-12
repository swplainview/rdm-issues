---
project: seedling-swapper
title: User account deletion
status: wont-fix
priority: medium
created: 2026-04-11
---

Two deletion paths:

1. **Self-deletion** — any authenticated user can delete their own account from their profile/settings page. Should cascade-delete their listings, claims, and any other owned data. Warn the user before confirming.

2. **Admin deletion** — admin can delete any user account from the user management panel. Same cascade behavior. Should be disabled for the acting admin's own account (use the role toggle's self-guard pattern).

Both paths need to handle the case where the user has active listings in an open swap — either block deletion or soft-delete by anonymizing the listing (e.g., "Deleted user").
