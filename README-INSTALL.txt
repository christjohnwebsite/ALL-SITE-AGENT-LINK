ALL SITE AGENT LINK — INSTALLATION CHECKLIST

1) Create a NEW Supabase project for this website (use this separate ALL SITE AGENT LINK project).
2) In Supabase Authentication > Users, create your private admin account. Turn OFF public signups in Authentication settings.
3) Copy the admin user's UUID. Open supabase_schema.sql and replace YOUR_ADMIN_AUTH_USER_UUID with that UUID, then run the complete file in Supabase SQL Editor.
4) In Supabase Project Settings > API, copy Project URL and the publishable key (or legacy anon key). Put them in config.js. Never use service_role/secret key in frontend files.
5) Upload all extracted project files to a NEW GitHub repository.
6) Cloudflare Dashboard > Workers & Pages > Create > Pages > Connect to Git. Select the new repo, framework None, no build command, root directory /, then deploy.
7) Open https://YOUR-SITE.pages.dev/admin.html and log in. Add a test link and check the public homepage in another tab. Test edit, hide/show, delete, Facebook/Telegram settings, logo upload and analytics.
8) Replace the placeholder APK URL in index.html with your own release URL, or change/remove the download button if you do not have an APK yet.

Database features: player_links, site_settings, analytics_events, admin_users, and agent-logos Storage bucket.
Security: public visitors can read active links and social links, submit visit/click analytics, and view public logos. Only the UUID allowlisted in admin_users can manage links/settings/logos and read admin analytics.

Note: This package is prepared from the uploaded ZIP, but it has not been connected to your Supabase, GitHub, or Cloudflare accounts and has not been live-tested.
