# AGENTS.md - KubeStash Website

Hugo static website for KubeStash documentation. Uses Hugo extended, Node.js 20, PostCSS, and Firebase hosting.

## Prerequisites

- **Hugo v0.128.2** (extended)
- **Node.js 20**
- `npm install` to fetch JS dependencies (postcss-cli, autoprefixer, @fullhuman/postcss-purgecss)
- `git submodule update --init` for the `hugo-product-theme`

## Build Commands

```bash
make run              # Local dev server (config.dev.yaml)
make gen              # Dev build → public/
make gen-prod         # Production build with --minify → public/
make docs             # Aggregate docs using hugo-tools (downloads bin/hugo-tools)
make qa               # Build + deploy to Firebase QA channel
make release          # Build + deploy to Firebase production
make check-links      # Run lychee link checker against localhost:1313
```

There are **no tests** in this project. `npm test` is a stub that exits with an error.

## Running Locally

```bash
npm install
make docs            # Required for full docs content
make run             # http://localhost:1313
```

## Project Structure

```
content/           Markdown content (docs/, features/, overview/, pricing/)
layouts/           Hugo templates (partials/, shortcodes/, _default/, pricing/)
static/            Static assets (images, JS, CSS copied from theme)
data/              JSON config files (config.json, products/, authors/)
themes/            hugo-product-theme (git submodule from appscode/hugo-product-theme)
hack/              Helper scripts
bin/               Downloaded tools (hugo-tools)
```

## Code Style

### HTML Templates (layouts/)

- Use Hugo template syntax: `{{ .Get "param" }}`, `{{ .Inner }}`, `{{ partial "name" . }}`
- Shortcodes in `layouts/shortcodes/` — name files lowercase, kebab-case (`catalogtable.html`)
- Partials in `layouts/partials/` — nest reusable components under `components/`
- Use `markdownify` filter when rendering user-supplied markdown content
- Bulma CSS classes for styling (`is-*`, `has-*`, `columns`, etc.)
- Indent with 2 spaces in HTML templates
- Wrap SVG icons inline, no external icon CDN

### JavaScript (static/assets/js/)

- jQuery 3.6.0 available globally for legacy scripts
- Vue.js used for interactive elements (`vue-elements.js`, `search.js`)
- Use `const`/`let` over `var`
- No transpilation or bundler — write vanilla ES5/ES6 compatible code
- Keep vendor libs minified (`.min.js` suffix)

### CSS (static/assets/css/)

- PostCSS processes `themes/hugo-product-theme/assets/css/main.css`
- PurgeCSS strips unused classes using `hugo_stats.json` as source of truth
- Keep safelist in `process-css.js` for dynamic classes (formserv, owl, headroom, etc.)
- Browserslist: `> 1%, last 2 versions, not ie <= 8`
- Bulma is the primary CSS framework

### Markdown Content (content/)

- Hugo front matter in YAML format
- Use `docs` layout for documentation pages
- Shortcodes: `{{< notice type="warning" message="..." >}}`, `{{< code title="..." >}}`
- Images go in `static/assets/images/`

### JSON Data Files (data/)

- `config.json` — site-wide config (repo URLs, search keys)
- `products/`, `authors/`, `services/` — structured content
- Run `make set-version VERSION=x.y.z` to update doc version redirects
- Run `make set-assets-repo ASSETS_REPO_URL=url` to update asset repo URL

## Configuration

- **Dev**: `config.dev.yaml` — Firebase preview URLs, test domains
- **Prod**: `config.yaml` — production URLs, kubestash.com base
- Goldmark renderer uses `unsafe: true` for raw HTML in markdown
- Output formats: HTML + JSON (search index)

## Deployment

- **PR preview**: Auto-deployed via `.github/workflows/preview-website.yml` to Firebase hosting
- **QA**: Tag with `-alpha.X` or `-beta.X` suffix → deploys to QA channel
- **Release**: Tag without alpha/beta suffix → deploys to production
- Firebase project: `kubedb-new-e7965`
- Search index updated post-release to MeiliSearch at `search.docs.appscode.com`

## CI/CD

CI (`.github/workflows/ci.yml`) runs `make gen-prod` on all PRs and pushes to master.
Lint/typecheck: **none configured** — validate by ensuring `make gen-prod` succeeds.

## PR Conventions

- Squash merge via Kodiak (`.github/.kodiak.toml`)
- Auto-approve for `1gtm` and `tamalsaha` bot users
- Delete branch on merge enabled
