# Uji — Publish Guide

A **pure static site** (just `index.html`). No server, no database, no build step.
The contact form is **already wired and working** — messages go straight to
**suliman.khaled12@gmail.com**.

---

## ✅ Already done (no action needed)

- **Contact form backend** — uses **FormSubmit** (free, no server, no monthly cost).
- **Activated** — the FormSubmit confirmation link was clicked, and a live test message
  was delivered successfully to `suliman.khaled12@gmail.com`.
- When you hit **Reply** on a submission, it goes back to the customer's own email.
- The email is also shown as a clickable link in the Contact section, so visitors can
  email **suliman.khaled12@gmail.com** directly too.
- **Instagram** link in the footer points to https://www.instagram.com/uji.spot
- All content is bilingual (Arabic default / English), RTL, no ordering, no reviews,
  address set to الرياض، شارع الأمير بندر بن عبدالعزيز، حي الأندلس.

> The form is set up in the `<script>` at the bottom of `index.html`:
> ```js
> const CONTACT_EMAIL = 'suliman.khaled12@gmail.com';
> // posts to https://formsubmit.co/ajax/<CONTACT_EMAIL>
> ```
> To change the destination inbox later, just edit that one line. If you change it to a
> new address, the next submission will send a one-time "Activate Form" email to that
> address — click it once and it's live again.

---

## STEP 1 — Put the site online (2 min)

### Easiest — Netlify Drop
1. Go to https://app.netlify.com/drop
2. Drag the **`uji-spot-site`** folder onto the page
3. It's instantly live at a `something.netlify.app` URL
4. Sign up (free) to keep it and attach your domain

Alternatives that work identically: **Vercel** (vercel.com), **Cloudflare Pages**.

> Only `index.html` is needed to host the site. `serve.js` is just for local preview.

---

## STEP 2 — Connect your custom domain

### 2a. Buy a domain (if you don't have one)
| Registrar | Notes |
|-----------|-------|
| **Cloudflare** | Cheapest (at-cost), free email routing, best if using Cloudflare Pages |
| **Namecheap**  | Cheap `.com` (~$10/yr), free email forwarding included |
| **GoDaddy**    | Popular, pricier |
| **.sa domain** | Needs a Saudi commercial registration (CR) — via a `.sa` accredited registrar |

### 2b. Point the domain at your site (Netlify example)
1. Netlify dashboard → your site → **Domain settings → Add a domain**
2. Enter your domain (e.g. `ujispot.com`) → **Verify**
3. Netlify shows DNS records. At your registrar, either:
   - Change **nameservers** to the ones Netlify shows (simplest), **or**
   - Add an `A` record → `75.2.60.5`, and a `CNAME` for `www` → `your-site.netlify.app`
4. Wait a few minutes — **HTTPS is set up automatically** (free SSL)

---

## Optional — switch to a branded email later

Right now everything goes to your Gmail, which works perfectly. If you later want a
professional address like `hello@ujispot.com`:

1. At your registrar, set up **email forwarding**: `hello@ujispot.com` → your Gmail
   - **Namecheap:** Domain → *Email Forwarding*
   - **Cloudflare:** *Email → Email Routing*
2. In `index.html`, change `CONTACT_EMAIL` to the new address, and update the
   `mailto:` link in the Contact section.
3. Re-upload — the first submission triggers a one-time activation email; click it once.

---

## Recommended fastest path
1. **Netlify Drop** the `uji-spot-site` folder  *(Step 1)*
2. **Namecheap or Cloudflare** domain → add it in Netlify  *(Step 2)*

The form already works, so once it's on your domain you're fully live —
about **10 minutes** total.

---

## Files in this project
```
uji-spot-site/
├── index.html    ← the whole site (bilingual AR/EN, RTL, contact form)
├── serve.js      ← local preview server only (not needed for hosting)
└── PUBLISH.md    ← this file
```
