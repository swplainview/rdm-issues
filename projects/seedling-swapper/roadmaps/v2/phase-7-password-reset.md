---
phase: 7
title: Password reset via email
status: not-started
---

Allow users who have forgotten their password to reset it via a link sent to their email.

## Flow

1. User clicks "Forgot password?" on the login page
2. Enters their email address; a time-limited reset token is generated and emailed to them
3. Clicking the link in the email opens a reset form pre-authenticated by the token
4. User sets a new password; token is consumed and invalidated
5. User is redirected to login

## Data model

- New `PasswordResetToken` model: `id`, `userId`, `token` (hashed), `expiresAt`, `usedAt?`
- Token expires after a short TTL (e.g. 1 hour)
- Token is single-use (marked used on redemption)

## API

- `POST /auth/forgot-password` — accepts `email`, generates token, sends email (always returns 200 to avoid user enumeration)
- `POST /auth/reset-password` — accepts `token` + `newPassword`, validates token, updates password, marks token used

## Email

- Use a transactional email provider (e.g. Resend, Nodemailer + SMTP)
- Template: plain-text or simple HTML with the reset link
- Link format: `<FRONTEND_URL>/reset-password?token=<raw-token>`

## Frontend

- "Forgot password?" link on the login page → `/forgot-password` page with email form
- `/reset-password?token=` page with new password + confirm fields
- Success and error states for both pages

## Acceptance criteria

- [ ] `PasswordResetToken` table exists with hashed token, expiry, and used-at fields
- [ ] `POST /auth/forgot-password` generates and emails a reset link; always returns 200
- [ ] `POST /auth/reset-password` validates token (not expired, not used), updates password, marks token used
- [ ] Expired and already-used tokens are rejected with a clear error
- [ ] Frontend forgot-password and reset-password pages work end to end
- [ ] No user enumeration: the forgot-password form gives the same response regardless of whether the email exists
