---
phase: 10
title: Notifications
status: done
completed: 2026-04-12
---

An opt-in notification system that keeps users informed about activity relevant to them.

## Notification types

| Event | Recipient |
|---|---|
| A followed user adds a new listing | Follower |
| A claim is made on your listing | Listing owner |
| A listing you have claimed is deleted | All claimants |

## Features

### Following
- Users can follow / unfollow other users
- Following is the prerequisite for new-listing notifications
- Follow state visible on public profile pages (phase 9)

### Notifications pane
- Accessible from the navbar (e.g. bell icon with unread badge)
- Lists notifications in reverse-chronological order
- Mark individual notifications as read; mark all as read
- Notifications are opt-in per type (user preferences)

### Notification preferences
- Toggle each notification type on/off independently
- Stored per user in the database

## Schema changes
- `Follow` — `followerId`, `followeeId`, `createdAt`
- `Notification` — `id`, `userId`, `type` (enum), `message`, `read`, `createdAt`, optional `linkUrl` for deep-linking to the relevant listing/profile
- `NotificationPreference` — `userId`, `type`, `enabled` (or a simple JSON blob on `User`)

## Delivery
- In-app only for now (no email / push)
- Notifications are created server-side at the point of the triggering event (claim created, listing deleted, listing created for followers)
- Frontend polls or fetches on navigation; no WebSocket required for v1
