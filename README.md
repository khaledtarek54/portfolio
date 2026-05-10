# khaledtarek.dev — portfolio site

Single-file static portfolio. No build step. Drop it on any static host.

## Files

- `index.html` — the entire site (Tailwind via CDN, fonts via Google Fonts)
- `resume.pdf` — your CV PDF (you need to add this — drop your final CV here as `resume.pdf`)
- `vercel.json` — Vercel config for clean URLs (optional)
- `CNAME` — for GitHub Pages custom domain (only if you go that route)

## Local preview

```bash
# any static server works; pick one
python3 -m http.server 8080
# or
npx serve .
```

Open http://localhost:8080

## Deploy options (pick one)

### Option A — Vercel (recommended, takes 2 minutes)

1. Push this folder to a new GitHub repo (e.g., `khaledtarek54/portfolio`):
   ```bash
   cd /Users/khaled/Desktop/khaledtarek-portfolio
   git init
   git add .
   git commit -m "feat: initial portfolio site"
   gh repo create khaledtarek54/portfolio --public --source=. --push
   ```
2. Go to [vercel.com/new](https://vercel.com/new), import the repo, click Deploy.
3. After deploy: Settings → Domains → Add → `khaledtarek.dev`. Vercel will give you 2 DNS records to add at your registrar.

### Option B — GitHub Pages (free, slightly slower setup)

1. Create a repo named exactly `khaledtarek54.github.io`:
   ```bash
   cd /Users/khaled/Desktop/khaledtarek-portfolio
   git init
   git add .
   git commit -m "feat: initial portfolio site"
   gh repo create khaledtarek54/khaledtarek54.github.io --public --source=. --push
   ```
2. Settings → Pages → Source: `main` / `/ (root)` → Save.
3. Site lives at `https://khaledtarek54.github.io` within a few minutes.
4. For `khaledtarek.dev`: keep the `CNAME` file containing your domain, then point your domain to GitHub Pages with these DNS records:
   ```
   A    @    185.199.108.153
   A    @    185.199.109.153
   A    @    185.199.110.153
   A    @    185.199.111.153
   CNAME www khaledtarek54.github.io
   ```

## What you still need to do

1. **Add `resume.pdf`** — drop your final CV PDF here as `resume.pdf` so the "Download CV" button works
2. **Update LinkedIn URL** — once you customize your slug (e.g., `khaled-tarek-eng`), grep for `khaled-tarek-3596401b1` and replace
3. **Buy `khaledtarek.dev`** — Cloudflare Registrar (cheapest) or Namecheap, ~$12/year
4. **Add screenshots later** — the project cards are text-only; once you have screenshots, replace the placeholders

## Upgrading from Tailwind CDN to a build step (optional, later)

The CDN works fine for a portfolio site. If you want to remove the dev-mode console warning and squeeze the CSS:

```bash
npm init -y
npm install -D tailwindcss@latest @tailwindcss/cli
npx tailwindcss --input ./src/input.css --output ./dist/styles.css --minify
```

Then swap `<script src="https://cdn.tailwindcss.com"></script>` for `<link rel="stylesheet" href="./dist/styles.css">`.
