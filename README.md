# ALL SITE AGENT LINK

Static public directory and admin panel, prepared as the standalone ALL SITE AGENT LINK website.

## Features
- Public website that displays active links from Supabase
- Admin login via Supabase email/password
- Add/edit/delete links, categories, descriptions, active/hidden status, and logos
- Editable Facebook and Telegram links
- Visit and click analytics
- PWA manifest and service worker

## Setup from a clean database
1. Create a **new Supabase project** for ALL SITE AGENT LINK.
2. Create the admin account in Authentication > Users; copy its UUID. Disable public signups.
3. In `supabase_schema.sql`, replace `YOUR_ADMIN_AUTH_USER_UUID` with that UUID, then run the entire SQL file once in Supabase SQL Editor. This creates all required tables, RLS policies, helper function, indexes and the `agent-logos` Storage bucket/policies.
4. Put the new project's URL and publishable/anon key in `config.js`. The key is public by design; never use a `service_role`/secret key in browser code.
5. Push all files to a new GitHub repository and connect that repository to Cloudflare Pages (framework: None, build command blank, output directory `/`).
6. Visit `/admin.html`, sign in, and test all admin features and public updates.

## Online update flow
Admin panel writes to Supabase; the public website reads active rows from the same separate Supabase project. Link/settings changes therefore appear without rebuilding the Cloudflare Pages deployment. A code/design change still requires a GitHub commit and Pages deployment.

## Security model
- `admin_users` is an allowlist. Only the UUID inserted by the setup SQL is an admin.
- RLS limits link/settings mutations and analytics reads to that allowlisted user.
- Public users can read active links, social settings and public logos; they can insert basic visit/click analytics only.
- Public signup should remain disabled. Do not share admin credentials.
- The SQL must be run only after replacing the UUID placeholder.

## Important configuration
The APK download URL in `index.html` is a placeholder; replace it with your own GitHub Release URL or remove the download button if no APK is available.

## Notes
This is a prepared starter package, not a live deployment. Supabase, GitHub and Cloudflare must be configured in your own accounts.
