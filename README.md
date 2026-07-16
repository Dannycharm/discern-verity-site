# discern-verity-site

Public static website for **Discern Verity — Independent Fleet Risk Analytics**.  
Plain HTML + CSS, no build step, no framework. Designed for GitHub Pages.

---

## Publish to GitHub Pages

### 1. Create the public GitHub repo

```bash
# From inside this folder:
cd /path/to/discern-verity-site

git init
git add .
git commit -m "Initial site — Discern Verity public website"

# Create the public repo on GitHub (requires GitHub CLI):
gh repo create discern-verity-site --public --source=. --remote=origin --push

# — OR — create it manually at github.com, then:
git remote add origin https://github.com/<your-github-username>/discern-verity-site.git
git branch -M main
git push -u origin main
```

### 2. Enable GitHub Pages

**Option A — GitHub CLI:**
```bash
gh api repos/<your-github-username>/discern-verity-site/pages \
  --method POST \
  --field source='{"branch":"main","path":"/"}'
```

**Option B — GitHub web UI:**
1. Go to `https://github.com/<your-github-username>/discern-verity-site`
2. Click **Settings → Pages**
3. Under **Source**, select **Deploy from a branch**
4. Branch: `main` · Folder: `/ (root)`
5. Click **Save**

GitHub Pages deploys in ~1 minute.

---

## Your live URL

```
https://<your-github-username>.github.io/discern-verity-site/
```

Replace `<your-github-username>` with your actual GitHub username.

---

## Updating the site

```bash
# Edit any file, then:
git add .
git commit -m "Update: <what changed>"
git push
# GitHub Pages redeploys automatically within ~1 minute.
```

## Updating the PDFs

```bash
# Copy fresh PDFs from the private repo output folder:
cp /path/to/Discern_Verity/output/*.pdf assets/
git add assets/
git commit -m "Update PDFs"
git push
```

---

## Structure

```
discern-verity-site/
├── index.html            Home page (problem, deliverables, 3 layers, CTA)
├── documents.html        Four PDF cards with view/download links
├── about.html            Founder bio + photo
├── site.css              All styles — colors mapped 1:1 from theme.py
├── assets/
│   ├── sample_scorecard.pdf
│   ├── methodology_onepager.pdf
│   ├── program_stacking_sheet.pdf
│   ├── differentiation_onepager.pdf
│   └── profile.jpg
└── README.md
```

## Brand note

All hex colors in `site.css` are sourced directly from
`src/discern_verity/reporting/theme.py` in the private `Discern_Verity` repo.
CSS custom properties are named to match the Python constants (`--navy`, `--accent`, etc.).
Do not introduce new colors without updating both files.
