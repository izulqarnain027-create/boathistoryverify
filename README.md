# Boat History Verify — Website

Static marketing site for Boat History Verify (vessel history reports: boats, yachts, jet skis/PWCs, commercial vessels).

## Files
- `index.html` — Homepage
- `services.html` — Services page (four vessel-class report sections)
- `styles.css` — All styles (single shared stylesheet)
- `script.js` — Mobile nav toggle + scroll reveal (no dependencies)
- `vercel.json` — Enables clean URLs (`/services` instead of `/services.html`)

No build step, no framework, no npm install needed — plain HTML/CSS/JS.

# Boat History Verify — Website

Static marketing site for Boat History Verify (vessel history reports: boats, yachts, jet skis/PWCs, commercial vessels).

## Files
- `index.html` — Homepage
- `services.html` — Services page (four vessel-class report sections + pricing)
- `checkout.html` — Order form that collects vessel details, then hands off to Whop checkout
- `styles.css` — All styles (single shared stylesheet)
- `script.js` — Mobile nav toggle + scroll reveal (no dependencies)
- `vercel.json` — Enables clean URLs (`/services` instead of `/services.html`)

No build step, no framework, no npm install needed — plain HTML/CSS/JS.

## Photography
Hero and vessel-class images are hotlinked directly from Unsplash (`images.unsplash.com`), all published under the free-to-use [Unsplash License](https://unsplash.com/license) — no attribution required, safe for commercial use. Because they're hotlinked, no image files need to be uploaded to the repo. If you'd rather host your own images, download replacements into an `/assets` folder and update the `src` attributes in `index.html` and `services.html`.

## Pricing
Three one-time-purchase tiers on `services.html#pricing`, structured the same way as ridesaudit.com/boat:
- **Basic — $54.99**: HIN/VIN decode, title & registration, theft check, recall info, storm/flood damage
- **Standard — $74.99** (Most Popular): everything in Basic + full lien search, salvage history, accident records, ownership history
- **Premium — $94.99**: everything in Standard + auction data, seizure flags, priority processing & support

Edit prices or features directly in the `.price-card` blocks in `services.html`.

## How the order flow works
1. Visitor picks a plan on `services.html#pricing` → goes to `checkout.html?plan=standard`
2. `checkout.html` collects vessel type, HIN/registration number, and email
3. On submit, it redirects to the matching **Whop checkout link**, passing the vessel details as URL query parameters
4. Customer pays on Whop's secure hosted checkout
5. You (or your team) manually pull the vessel details from the query params / Whop's "questions before checkout" answers and email the finished PDF report

### Connecting Whop (you still need to do this part)
1. Create an account at [whop.com](https://whop.com) and set up your business/whop.
2. Create **3 products** (or 3 pricing options under one product) — Basic, Standard, Premium — matching the prices above.
3. For each one, go to **Dashboard → Checkout links → Create checkout link**, set it as a one-time payment, and copy the link.
4. Optional but recommended: in each checkout link's **Advanced options**, turn on **"Ask questions before checkout"** and add fields for HIN/registration number and vessel type — this way you don't have to rely on the URL query params.
5. Paste your 3 real checkout links into `checkout.html`, replacing the placeholders here:
   ```js
   const WHOP_CHECKOUT_LINKS = {
     basic:    "https://whop.com/checkout/YOUR_BASIC_PLAN_ID/",
     standard: "https://whop.com/checkout/YOUR_STANDARD_PLAN_ID/",
     premium:  "https://whop.com/checkout/YOUR_PREMIUM_PLAN_ID/"
   };
   ```
6. Also update the same 3 placeholder URLs inside the `.price-card` buttons in `services.html` if you want the pricing cards to skip the form and link straight to Whop (optional — right now they route through `checkout.html` first).
7. In your Whop dashboard, set a **redirect after checkout** (in the checkout link's Advanced options) to point back to a "thank you" page on this site if you'd like one — not included yet, ask if you want it built.

Reports still need to be delivered manually (or via your own automation) after payment — Whop handles payment, not report generation or email delivery.

## Deploy via GitHub → Vercel

1. Push all files to the root of a GitHub repository.
2. Go to https://vercel.com/new and import the repository.
3. Framework preset: **Other**. Leave Build Command and Output Directory blank.
4. Deploy, then add your domain under Settings → Domains.

Every future push to `main` auto-redeploys.

## Editing content later
- Vessel report checklists live in `services.html` inside each `.plate` section (`#boats`, `#yachts`, `#jetskis`, `#commercial`).
- Coverage/region table is in `index.html` under the `#coverage` section.
- Colors, fonts, and spacing are all defined once at the top of `styles.css` under `:root`.

## Still placeholder / to replace before launch
- Footer legal links (Terms, Privacy, Refund Policy) point to `#` — add real pages before going live.
- The 3 Whop checkout link placeholders in `checkout.html` (see above) — required before checkout will actually work.
- `support@boathistoryverify.com` is used as the contact address throughout — update if different.

