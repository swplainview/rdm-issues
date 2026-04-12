---
phase: 5
title: User account deletion (self and admin)
status: not-started
---

Allow users to delete their own account and allow admins to delete any user account.

## Self-deletion

- Authenticated user can delete their own account from the Account page
- Confirmation dialog shown before proceeding
- Cascades: deletes listings, claims, notifications, preferences, follows

## Admin deletion

- Admin can delete any user from the user management panel
- Disabled for the acting admin's own account (mirrors the role-toggle self-guard)
- Same cascade behavior as self-deletion

## Edge cases

- If the user has active listings in an open swap, either:
  - Block deletion with an explanation, or
  - Soft-delete by anonymizing listings to "Deleted user"
- Decision should be consistent between self and admin deletion paths

## Acceptance criteria

- [ ] `DELETE /users/me` deletes the authenticated user and cascades
- [ ] `DELETE /users/:id` (admin only) deletes any user and cascades
- [ ] Self-deletion is blocked or handled gracefully when active listings exist
- [ ] Frontend Account page has a "Delete account" section with confirmation
- [ ] Admin user management table has a delete action (disabled for self)
- [ ] Deleted user's JWT is invalidated on next request
