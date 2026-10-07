# A2Zsoltution · AI IT Helpdesk
Next.js + TypeScript + Tailwind + Supabase (Postgres, Auth, RLS), deployable on Vercel.

## Setup
1. Create a Supabase project. Run `supabase/migrations/001_init.sql` in the SQL editor.
2. `cp .env.example .env.local` and fill the values.
3. `npm install && npm run dev`
4. Sign up at `/login?mode=signup`: this creates your isolated organization, seeds roles/permissions and makes you Organization Owner.

## Deploy to Vercel
Push to GitHub, import in Vercel, add every variable from `.env.example` (plus `NEXT_PUBLIC_SITE_URL`), deploy. In Supabase Auth settings, add your Vercel URL as Site URL and redirect URL.

## Security model
Tenant isolation and permissions are enforced in Postgres RLS (`current_org()`, `has_perm()`), not only in app code. Roles and permissions are rows in `roles` / `role_permissions`, so they are configurable.
