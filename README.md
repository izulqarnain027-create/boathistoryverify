# Boat History Verify — Website

Static marketing site for Boat History Verify (vessel history reports: boats, yachts, jet skis/PWCs, commercial vessels).

## Files
- `index.html` — Homepage
- `services.html` — Services page (four vessel-class report sections)
- `styles.css` — All styles (single shared stylesheet)
- `script.js` — Mobile nav toggle + scroll reveal (no dependencies)
- `vercel.json` — Enables clean URLs (`/services` instead of `/services.html`)

No build step, no framework, no npm install needed — plain HTML/CSS/JS.

## Deploy via GitHub → Vercel

1. Create a new GitHub repository and push these files to the root:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

2. Go to https://vercel.com/new and import the GitHub repository.

3. Framework preset: choose **"Other"** (no build command, no output directory needed — Vercel will serve the static files directly). Leave build settings blank.

4. Deploy. Vercel will give you a `*.vercel.app` URL.

5. Add your domain:
   - In the Vercel project → **Settings → Domains**, add `boathistoryverify.com` (and `www.boathistoryverify.com`).
   - Point your domain's DNS to Vercel as instructed on that screen (usually an `A` record to `76.76.21.21` and a `CNAME` for `www`).

Every future push to `main` will auto-redeploy.

## Editing content later
- Vessel report checklists live in `services.html` inside each `.plate` section (`#boats`, `#yachts`, `#jetskis`, `#commercial`).
- Coverage/region table is in `index.html` under the `#coverage` section — edit the `.ledger-row` rows as you add or confirm markets.
- Colors, fonts, and spacing are all defined once at the top of `styles.css` under `:root` — change a value there to restyle the whole site.

## Still placeholder / to replace before launch
- Footer legal links (Terms, Privacy, Refund Policy) point to `#` — add real pages before going live.
- `support@boathistoryverify.com` is used as the contact address throughout — update if different.
- Order buttons (`Order Boat Report`, etc.) link to `#` — wire these to your checkout/WooCommerce flow when ready.
