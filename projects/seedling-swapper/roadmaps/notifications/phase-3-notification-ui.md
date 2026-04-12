---
phase: 3
title: Notification UI
status: done
completed: 2026-04-12
commit: b8932d3c44aca73d367a036bcc483afedf6dfe32
---

Frontend notification bell and preferences UI.

## Navbar bell
- Bell icon with unread-count badge (hidden when zero)
- Clicking opens a popover listing recent notifications in reverse-chronological order
- Each notification shows message + relative time; clicking navigates to `linkUrl` and marks it read
- "Mark all read" button at the top of the list
- Empty state when no notifications

## AccountPage preferences
- New "Notifications" card with a toggle for each of the 3 types
- Loads preferences on mount; saves immediately on toggle

## Components
- `NotificationsBell` — self-contained; fetches and manages its own state
