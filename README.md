# RAAM Group Smart Lead Conversion Console: Vercel deployment

This folder is a static site: `index.html` (the whole app) + `vercel.json` (security headers). No build step, no dependencies, no environment variables.

## Deploy (pick one)

**A. GitHub (recommended)**
1. Create a GitHub repository and upload these files (`index.html`, `vercel.json`, `README.md`, `.gitignore`) at the repository root.
2. Go to vercel.com, then Add New, then Project, and import the repository.
3. Framework Preset: **Other**. Leave Build Command, Output Directory and Install Command empty. Click **Deploy**.

**B. Vercel CLI (no GitHub needed)**
```
npm i -g vercel
cd raam-vercel
vercel          # first run: log in, accept the defaults (framework: Other)
vercel --prod   # publish to your production URL
```

After deploying, open the URL. The app signs in automatically as HOD in prototype mode; use the role dropdown at the top right to switch to Sales Manager or Sales Executive.

## How data works on Vercel (important)
- The site is static, so records (leads, assignments, call logs) are saved in each visitor's own browser (localStorage). They persist across refreshes on that browser and device, but are **not shared** between users or devices.
- Vercel's serverless functions have no permanent disk, so a shared multi-user database needs an external database (for example Neon Postgres, Upstash Redis or Turso) plus API routes in an `/api` folder. If you add working `/api` routes later, this page switches to them automatically when `/api/health` returns `{"ok":true}`.
- Customers submitting the enquiry form on your live URL would only save to their own browser. For real lead capture, connect a database first.

## Not connected
Telephony, WhatsApp, email/SMS and any CRM are not integrated. The Live Monitor shows saved activity plus clearly labelled DEMO events.

## Custom domain
Vercel Project, Settings, Domains, then add your domain and follow the DNS instructions.
