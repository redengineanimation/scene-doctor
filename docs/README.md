# Scene Doctor docs (MkDocs site)

The Scene Doctor manual.

## Preview locally

```bash
pip install -r docs/requirements.txt
mkdocs serve            # http://127.0.0.1:8000
```

## Before first deploy

1. Push this repo to GitHub.
2. Edit `mkdocs.yml` — set `site_url` and `repo_url` to your GitHub Pages
   URL and repo (replace `YOURNAME`).
3. In the GitHub repo: **Settings → Pages → Source = GitHub Actions**.
4. Push to `main`/`master`. The `.github/workflows/docs.yml` workflow
   builds and publishes to GitHub Pages.

The workflow uses `mike`, so the published URL is versioned like
`https://YOURNAME.github.io/scene-doctor/latest/checks/#flipped-normals`.

## Manual deploy

```bash
mike deploy --push --update-aliases latest
mike set-default --push latest
```

## Notes

- This `mkdocs.yml` currently documents **Scene Doctor**. When Project
  Packer needs its own manual, give it a separate site (its own
  `mkdocs.yml` + `docs/` under that product) rather than mixing nav here.
