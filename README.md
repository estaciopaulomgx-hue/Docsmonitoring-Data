# DocTrack — Document Monitoring & SLA System

Cloud-connected version with **accounts that work on any device** and
**real-time synchronization**.

## ✅ No setup needed

The cloud backend (database, real-time, file storage) is **already
provisioned and connected** — the credentials in `supabase-config.js`
point to a live backend with all tables and the storage bucket created.

Just open `index.html` (or host the folder anywhere) and use it.

## How it works

- **Accounts (`dt_users`)** are stored in the cloud, so an account created
  on one device can sign in on any other device with the same email and
  password. Account pushes are **merge-safe** — a new device can never
  erase accounts created elsewhere.
- **Documents, activity logs, and notifications** are stored per-user in
  the cloud and stream to all devices in real time.
- **Uploads** go to cloud file storage and the `uploads` table.
- Device-local only (not synced): session, theme.

## Files

| File | Purpose |
|---|---|
| `index.html` | App shell + login-waits-for-cloud guard |
| `style.css` | Styles (unchanged) |
| `script.js` | App logic (unchanged) |
| `sync.js` | Real-time cloud sync layer |
| `supabase-config.js` | Cloud credentials (pre-configured) |
| `supabase-setup.sql` | Reference: schema already applied to the cloud |

## Testing cross-device

1. Open the app on Device A → Sign Up.
2. Open the app on Device B → Sign In with the same email/password. ✅
3. Add/edit/delete a document on either device → it appears on the other
   within a second, including newly added docs. ✅

## Note on security

This demo intentionally keeps the original app logic (passwords checked
in the browser, open database rules). Anyone with the app files can read
the synced data. For production use, switch to real authentication.
