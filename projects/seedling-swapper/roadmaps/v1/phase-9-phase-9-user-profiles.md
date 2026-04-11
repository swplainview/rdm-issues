---
phase: 9
title: User Profiles
status: not-started
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
