# accion-delivery-handbook
Accionlabs Delivery Handbook

## What’s included
- MkDocs site configured with Material theme (`mkdocs.yml`)
- Starter docs at `docs/index.md`
- GitHub Actions workflow to deploy to GitHub Pages (`.github/workflows/publish.yml`)
- Python requirements (`requirements.txt`)
- `.gitignore` tuned for MkDocs builds

## Prerequisites
- Python 3.10+
- Optional (macOS): Homebrew for installing Pandoc (`brew`)

## Setup and local preview
```bash
# Create a virtual environment (recommended)
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Serve locally
mkdocs serve
# Open the URL shown, typically http://127.0.0.1:8000
```

## Convert your Word document to Markdown
You have two reliable options. Pandoc gives you the most control.

### Option A: Pandoc
- Install Pandoc (macOS):
```bash
brew install pandoc
```
- Convert a `.docx` to GitHub-Flavored Markdown and extract images to `docs/assets/`:
```bash
pandoc \
  "path/to/Your Document.docx" \
  -t gfm \
  --extract-media=docs/assets \
  -o docs/converted/your-document.md
```
- Review the generated `docs/converted/your-document.md` and images in `docs/assets/`.

Tips:
- Large documents convert better when split into logical sections (create multiple `.md` files).
- Use headings (`#`, `##`) consistently in Word before converting to improve the TOC structure.

### Option B: Mammoth (simple styles mapping)
- Install Mammoth CLI (Node):
```bash
npm install -g mammoth
```
- Convert:
```bash
mammoth "path/to/Your Document.docx" > docs/converted/your-document.md
```

## Organize pages and navigation
- Place Markdown files under `docs/` (e.g., `docs/processes.md`, `docs/standards.md`).
- Add images and media to `docs/assets/`.
- Update the navigation in `mkdocs.yml` under `nav:`. Example:
```yaml
nav:
  - Home: index.md
  - Processes: processes.md
  - Standards: standards.md
  - Guides:
      - Onboarding: guides/onboarding.md
      - Delivery Playbook: guides/playbook.md
```

## Deploy to GitHub Pages
The workflow `.github/workflows/publish.yml` builds and deploys on pushes to `main`.

One-time repo setup:
1. In GitHub, go to Settings → Pages
2. Set Build and deployment → Source to “GitHub Actions”
3. (Optional) Set a custom domain or enforce HTTPS
4. Update `site_url` in `mkdocs.yml` to your Pages URL, e.g. `https://<org>.github.io/<repo>/`

Manual run:
- Push to `main` or trigger the workflow via Actions → Deploy MkDocs to GitHub Pages → Run workflow

## Common tasks
- Lint/fix Markdown after conversion
- Add callouts using admonitions, e.g.:
```markdown
!!! note
    This is a note.
```
- Use tabs for variants:
```markdown
=== "Option A"
Content A

=== "Option B"
Content B
```

## Troubleshooting
- If the deploy fails with Pages permissions: ensure Pages is enabled and the workflow has `pages: write`.
- If images don’t show: verify their paths under `docs/` and that they are committed.
- If local serve fails: confirm your venv is active and `pip install -r requirements.txt` ran successfully.
