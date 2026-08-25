# lixinyao11.github.io

Personal academic website of Xinyao Li, built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme.

## How it builds

Unlike the previous Jekyll Now setup, this site is **not** built by GitHub's built-in Jekyll.
al-folio depends on plugins outside the GitHub Pages whitelist (`jekyll-scholar`,
`jekyll-imagemagick`, and others declared in the `Gemfile`), so building happens in CI:

1. Push to `main` triggers `.github/workflows/deploy.yml`.
2. The workflow builds the site with Ruby 3.3 and pushes the output to the `gh-pages` branch.
3. GitHub Pages serves `gh-pages`.

So **Settings → Pages → Source must point at the `gh-pages` branch**, not at "GitHub Actions".
A build failure now means the site does not update — check the Actions tab rather than assuming
the push went through.

## Where the content lives

| What | Where |
| --- | --- |
| Bio, profile photo, homepage text | `_pages/about.md` |
| Publications | `_bibliography/papers.bib` |
| News items on the homepage | `_news/*.md` |
| CV content (rendered page) | `_data/cv.yml` |
| CV file (download button) | `assets/pdf/Xinyao_Li_CV.pdf` |
| Paper thumbnails | `assets/img/` (referenced by `preview={...}` in the bib) |
| Email, GitHub, Scholar links | `_data/socials.yml` |
| Venue badge colors | `_data/venues.yml` |
| Coauthor links | `_data/coauthors.yml` |

## Adding a paper

Add an entry to `_bibliography/papers.bib`, drop a thumbnail into `assets/img/`, and reference it
with `preview={filename}`. Set `selected={true}` to also show it on the homepage. The `abbr` field
becomes the venue badge — add matching colors in `_data/venues.yml`.

## Local preview

The system Ruby on macOS is too old for this theme. Use Docker:

```bash
docker compose up
```

Then open <http://localhost:8080>.
