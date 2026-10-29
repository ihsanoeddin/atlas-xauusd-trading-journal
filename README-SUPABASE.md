# ATLAS — Supabase setup

## What this version does
- Email/password login and account creation through Supabase Auth.
- Loads and saves trade rows in `public.trades`.
- Uses the configured Supabase project URL and publishable key in the frontend.
- Offers migration of existing browser-local trades when the signed-in account has no cloud trades.
- Keeps the starting balance in this browser's localStorage; it is not synced across devices yet.

## Deploy
1. Replace the existing repository `index.html` with this file.
2. Commit the change and wait for GitHub Pages to redeploy.
3. In Supabase Authentication URL Configuration, make sure the GitHub Pages URL is in the allowed Redirect URLs.
4. Confirm that the `public.trades` table has the columns used by the app and RLS policies restricting each row to `auth.uid() = user_id`.
5. Test login, add a small test trade, reload, edit, delete, and then log out/in.

## Important
- Do not put a `service_role` key or database password in this file.
- Existing browser trades are only migrated if you choose OK in the migration prompt. Do not clear browser storage until you verify the cloud records.
- Email confirmation may be required depending on Supabase Auth settings.
- If login or queries fail, inspect the browser console and Supabase Logs. This file has not been tested against your live Supabase project from this environment.
