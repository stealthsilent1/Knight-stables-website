# Hosting knightstables.com

This is a static site (a single `index.html`), so it can be hosted for free.
The easiest path is **GitHub Pages**, since the code already lives in this
GitHub repository.

## Option 1: GitHub Pages (recommended, free)

### 1. Publish the site

1. Merge this branch into `main` (or push it directly to `main`).
2. On GitHub, open the repository → **Settings** → **Pages**.
3. Under **Build and deployment**, set:
   - **Source:** Deploy from a branch
   - **Branch:** `main` / `/ (root)`
4. Click **Save**. Within a minute or two the site is live at
   `https://<your-username>.github.io/Knight-stables-website/`.

### 2. Connect the knightstables.com domain

1. Buy `knightstables.com` from any registrar (Namecheap, Cloudflare,
   Porkbun, GoDaddy, etc.) if you haven't already.
2. In your registrar's DNS settings, add these records:

   | Type  | Host/Name | Value                 |
   |-------|-----------|-----------------------|
   | A     | `@`       | `185.199.108.153`     |
   | A     | `@`       | `185.199.109.153`     |
   | A     | `@`       | `185.199.110.153`     |
   | A     | `@`       | `185.199.111.153`     |
   | CNAME | `www`     | `<your-username>.github.io` |

3. Back in GitHub **Settings → Pages**, enter `knightstables.com` under
   **Custom domain** and save. (The `CNAME` file in this repo keeps that
   setting from being lost on future deploys.)
4. Once the DNS check passes (can take from minutes up to ~24h), tick
   **Enforce HTTPS**. GitHub provisions a free SSL certificate
   automatically.

### 3. Updating the site later

Edit `index.html`, commit, and push to `main` — GitHub Pages redeploys
automatically within a minute.

## Option 2: Netlify or Vercel (also free)

1. Sign up at netlify.com or vercel.com with your GitHub account.
2. Click **Add new site → Import from Git** and pick this repository.
3. No build command is needed (it's plain HTML) — deploy.
4. Add `knightstables.com` under the site's **Domain settings** and follow
   their DNS instructions (they also provide free HTTPS).

Netlify has a bonus: built-in form handling. Add `data-netlify="true"` to
the `<form>` tags in `index.html` and contact-form submissions appear in
your Netlify dashboard with email notifications — no Formspree needed.

## Before going live: two TODOs in index.html

1. **Contact + newsletter forms** — the forms point at
   `https://formspree.io/f/YOUR_FORM_ID`. Create a free form at
   [formspree.io](https://formspree.io), and replace `YOUR_FORM_ID` (it
   appears twice) so submissions get emailed to you. (Skip this if you use
   Netlify forms as described above.)
2. **Gallery photos** — the gallery uses placeholder tiles. Put your photos
   in an `images/` folder and swap each
   `<div class="gallery-tile"><span>…</span></div>` to include an
   `<img src="images/your-photo.jpg" alt="…">` inside the tile.
