# Cairn Linux website

A static site: one HTML page, one stylesheet, self-hosted fonts, no build step and no
third-party requests (no Google Fonts, analytics or CDNs).

```
index.html          the page
style.css           all styles
favicon.svg         the logo, cropped for browser tabs
assets/img/         logo, screenshots (.webp shown, .png linked), social-card.png
assets/fonts/       Archivo and JetBrains Mono (SIL Open Font License, files included)
.nojekyll           tells GitHub Pages to serve files as-is
```

## Before you publish: fill in the placeholders

Every placeholder contains `REPLACE_ME` (or `YYYY.MM.DD` for the release date), so you can
find them all with:

```
grep -n "REPLACE_ME\|YYYY.MM.DD" index.html
```

| Placeholder | What goes there |
|---|---|
| `REPLACE_ME_ISO_URL` | Direct link to the ISO (e.g. a GitHub Release asset) |
| `REPLACE_ME_SHA256_URL` | Link to the `.sha256` file `build.sh` writes next to the ISO |
| `REPLACE_ME_SHA256` | The 64-character checksum (first field of that `.sha256` file) |
| `cairn-YYYY.MM.DD-x86_64.iso` | The real file name, in the download box and the dd/checksum commands |
| `REPLACE_ME_SOURCE_URL` | The project's source repository (footer) |
| `REPLACE_ME_SITE_URL` | The site's own address, for link previews (two `og:` tags in `<head>`) |

Tip: the ISO is about 2.4 GB. GitHub Releases allow files up to 2 GB, so host the ISO
somewhere else (SourceForge, a mirror, object storage) or split it, and link to it here.

## Publish on GitHub Pages

1. Create a repository and put these files at its root (or in a `docs/` folder).
2. Settings → Pages → Build and deployment → Deploy from a branch → pick the branch and
   folder.
3. The site appears at `https://<user>.github.io/<repo>/`.

## Publish on Netlify

Drag this folder onto https://app.netlify.com/drop, or connect the repository with no build
command and the publish directory set to the folder containing `index.html`.

## Editing

Colours are CSS variables at the top of `style.css`, taken from `branding/*.svg`. The hero
landscape is the wallpaper SVG inlined in `index.html`; the amber cap stone settles into
place once on load, and stays still for anyone with reduced motion turned on.
