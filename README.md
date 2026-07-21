# Glacare Health Sciences — Coming Soon Site

A single-page, SEO-optimized "coming soon" site for glacare.co, ready to deploy on Firebase Hosting.

## Before you deploy — fill these in

The following are placeholders in `public/index.html`. Update them with your real
details before going live:

1. **Phone number** — search for `+910000000000` (two places: the `tel:` link and its
   display text) and replace with your real number.
2. **Email address** — currently set to `info@glacare.co` (appears in the contact
   card, the `mailto:` link, and the JSON-LD structured data). Update if different.
3. **Notify-me form** — the form currently just shows a confirmation message
   client-side and does not store the email anywhere. Before launch, wire the
   `notifyForm` submit handler in `index.html` to a real endpoint — the simplest
   options on Firebase are a Cloud Function or a direct Firestore write from the
   client (needs the Firebase SDK + web config added to the page).
4. **Canonical domain** — all URLs currently point to `https://www.glacare.co/`.
   If you'll be testing on a temporary `*.web.app` / `*.firebaseapp.com` URL first,
   that's fine — just make sure the canonical tag, sitemap, robots.txt, and Open
   Graph URLs are updated to match your final custom domain once it's connected.

Registered office address and CIN were pulled from public MCA records
(U47721MH2024PTC436138) — double check these are still current.

## Deploy to Firebase Hosting

```bash
# 1. Install the Firebase CLI if you don't have it
npm install -g firebase-tools

# 2. Log in
firebase login

# 3. From this project folder, set your Firebase project ID
#    (replace the placeholder in .firebaserc, or run):
firebase use --add

# 4. Deploy
firebase deploy --only hosting
```

Once deployed, connect your custom domain (glacare.co) from the Firebase Hosting
console — Firebase will issue an SSL certificate automatically. You'll update your
GoDaddy DNS records to point at Firebase (Firebase's setup flow gives you the exact
A records / TXT verification record to add).

## After going live — SEO next steps

- Submit `https://www.glacare.co/sitemap.xml` in Google Search Console and Bing
  Webmaster Tools.
- Verify domain ownership in Google Search Console (carry over your existing
  verification if you had one on the GoDaddy site, or add a new one).
- The old GoDaddy site had minimal indexed content, so there's little historic SEO
  equity to preserve — no redirect mapping should be needed beyond making sure
  `glacare.co` and `www.glacare.co` both resolve to this new site.
- Once the full site (beyond this coming-soon page) is ready, expand the
  structured data (`Organization` schema in the `<head>`) with your product/service
  catalog, and add real page content — search engines rank thin "coming soon" pages
  poorly, so this page is meant to be temporary.

## File structure

```
public/
  index.html          — the coming-soon page (all styles/scripts inline)
  robots.txt
  sitemap.xml
  site.webmanifest
  assets/
    glacare-logo.png
    favicon-16.png / favicon-32.png / favicon-192.png / favicon-512.png
    apple-touch-icon.png
firebase.json          — Hosting config (caching, security headers, clean URLs)
.firebaserc             — set your Firebase project ID here
```
