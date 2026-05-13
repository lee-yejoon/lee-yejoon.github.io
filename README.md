# Ye Joon Lee — personal website

Static HTML site. Four pages: Home, About, Research, CV. No build step.

## Local preview

Open `index.html` in any browser. Or run a tiny local server:

```bash
# Python
python3 -m http.server 8000

# Or with Node
npx serve .
```

Then visit `http://localhost:8000`.

## Deploy to GitHub Pages

1. Create a repo on GitHub. Either name it `<your-username>.github.io` (user site, served at the root) or any name (project site, served at `/repo-name/`).
2. Push these files to the `main` branch.
3. In **Settings → Pages**, set **Source: Deploy from branch**, **Branch: `main`**, **Folder: `/ (root)`**.
4. Wait 30–60 seconds. Your site is live.

## File map

```
index.html        Home
about.html        About — long-form bio, Recent updates, Contact
research.html    Research — papers grouped by status
cv.html           CV — full vita (also links to PDF)

assets/
  site.css        All shared styles
  favicon.svg     Tiny purple "YJL" favicon (replace with NU logo if you have one)
  portrait.jpg    Hero photo
  cv.pdf          Downloadable CV PDF
```

## Things to update before going live

- **Google Analytics ID** — every page has a `gtag` snippet with `G-XXXXXXXXXX`. Create a GA4 property at <https://analytics.google.com>, copy your Measurement ID, and find-and-replace `G-XXXXXXXXXX` across the four HTML files. If you don't want analytics, delete the two `<script>` tags in each file.
- **Social URLs** — `href="#"` placeholders on Google Scholar, LinkedIn, and X. Replace with real URLs.
- **Bio copy** — `[PLACEHOLDER — ...]` strings on Home and About.
- **Recent items** — placeholders on About; fill with real talks, R&Rs, awards.
- **CV PDF** — replace `assets/cv.pdf` with your latest version (keep the filename).
- **Portrait** — replace `assets/portrait.jpg` with your final photo (keep the filename).
- **About portrait** — uses the same file; if you want a different photo there, change the `<img src>` in `about.html`.

## Editing tips

- All styles live in one file: `assets/site.css`. CV-specific styles are inlined in `cv.html` because they're not reused. About-specific styles are inlined in `about.html`.
- Brand color is `#4E2A84` (Northwestern purple). Change `--accent` in `:root` to retheme.
- Body text font is Source Serif 4. Display font is Playfair Display. Both loaded from Google Fonts.
- Email is obfuscated (`yejoon [dot] lee [at] kellogg [dot] northwestern [dot] edu`). It's not a `mailto:` link — visitors copy and type. This reduces spam from scrapers.

## Custom domain

Once you buy a domain (e.g. `yejoonlee.com`):

1. Add a `CNAME` file to the repo root containing just the domain (e.g. `yejoonlee.com`).
2. In your domain registrar's DNS settings:
   - `A` record at `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` record at `www` → `<your-username>.github.io`
3. In GitHub repo **Settings → Pages**, set Custom domain to your domain and enable **Enforce HTTPS**.

DNS can take an hour to propagate.

---

Built April 2026.
