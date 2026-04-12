---
phase: 2
title: Notification Triggers & API
status: done
completed: 2026-04-12
commit: 26ff10229c8d82e27fb3197b8bb51302a3eebcc0
---

Server-side notification creation and the full notifications API.

## Schema
- `NotificationType` enum: `NEW_LISTING`, `CLAIM_MADE`, `LISTING_DELETED`
- `Notification` model: `id`, `userId`, `type`, `message`, `read`, `linkUrl?`, `createdAt`
- `NotificationPreference` model: `@@id([userId, type])`, `userId`, `type`, `enabled`
- Add relations to `User`

## Triggers (woven into existing routes)
- `POST /listings` — fan out `NEW_LISTING` notifications to all followers of the poster who have that type enabled
- `POST /listings/:id/claim` — create `CLAIM_MADE` notification for the listing owner (if enabled)
- `DELETE /listings/:id` — create `LISTING_DELETED` notifications for all claimants (if enabled)

## API endpoints
- `GET /notifications` — current user's notifications, newest first (limit 50)
- `PATCH /notifications/read-all` — mark all as read
- `PATCH /notifications/:id/read` — mark one as read
- `GET /notifications/preferences` — return preferences for all 3 types (default enabled if not set)
- `PUT /notifications/preferences` — bulk upsert all 3 preferences
