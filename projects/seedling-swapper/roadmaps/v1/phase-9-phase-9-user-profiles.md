---
phase: 9
title: User Profiles
status: done
completed: 2026-04-12
commit: 6b76b34deaf000f30c3e63ab80b9186f692c4248
---

Users can build out a public profile and others can browse listings by user.

## Features

### Profile editing (own profile)
- Display name (already exists — editable here)
- Location (free-text, e.g. "Austin, TX")
- Short bio / about text
- Profile photo upload

### Public profile view (`/users/:id`)
- Shows display name, location, bio, and photo
- Lists all active listings by that user in the current swap

### Browse by user
- Listing cards link to the poster's profile
- Profile page shows the user's listings filtered to the active swap

## Schema changes
- Add `location`, `bio`, and `avatarPath` fields to `User`

## Notes
- Profile photo upload follows the same multer pattern as listing photos
- Non-authenticated users should be able to view profiles (public)
