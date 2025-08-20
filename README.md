
# Delivery Finder CDN (Vercel)

This is a tiny static project that serves your `delivery-rules.combined.json` with the right CORS and caching headers.

## Deploy (two options)

### A) Vercel CLI
1. Install: `npm i -g vercel`
2. In this folder, run: `vercel` (first time) then `vercel --prod`
3. Your file will be at: `https://<your-deployment>.vercel.app/delivery-rules.combined.json`

### B) GitHub → Vercel
1. Push these files to a GitHub repo.
2. Import the repo in Vercel (New Project → Framework: **Other**).
3. Build settings: none (static). Output directory: `public`.
4. Deploy, then grab the URL for: `/delivery-rules.combined.json`

## Headers
Configured in `vercel.json`:
- `Access-Control-Allow-Origin: *` (so Shopify can fetch it cross-origin)
- `Cache-Control: public, max-age=86400, stale-while-revalidate=604800`
- `Content-Type: application/json; charset=utf-8`

## Update workflow
- Replace `public/delivery-rules.combined.json` with a new version.
- Deploy again (`vercel --prod`) or let Vercel auto-deploy on push.
- Optionally version the filename like `delivery-rules.v2.json` and update your Shopify section setting.
