# CV — source of truth

The `resume.pdf` in this repo is **rendered output**, not the source.

## Where the source lives

Private repo: **[khaledtarek54/cv](https://github.com/khaledtarek54/cv)**
Local checkout: `/Users/khaled/Desktop/cv/`

## How to update the CV

1. Edit `khaled-tarek-cv.html` in the cv repo
2. Run the sync script:
   ```bash
   cd /Users/khaled/Desktop/cv
   ./sync.sh
   ```

`sync.sh` will:
1. Re-render `khaled-tarek-cv.pdf` from the HTML (Chrome headless)
2. Commit + push the cv repo (HTML + PDF)
3. Copy the PDF here as `resume.pdf`
4. Commit + push this portfolio repo
5. Vercel auto-redeploys → live site updates in ~30s

## Do not edit `resume.pdf` directly

Any manual edit to `resume.pdf` here will be **overwritten** on the next sync. Always edit the HTML in the cv repo.

## Why this split?

- The HTML CV contains personal contact info that doesn't need to be public.
- The portfolio repo is public and pages-deployed; only the rendered PDF needs to be here.
- Single source of truth avoids drift between paper-CV and web-CV.
