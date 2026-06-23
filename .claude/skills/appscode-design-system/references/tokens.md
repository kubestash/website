# Token Values — AppsCode

Concrete values for the token system. The **naming, tiers, and theming model**
are defined in `token-architecture.md` — read that first. This file is the value
registry. Components consume **semantic** tokens only.

> Values marked `‹from CSS export›` still need exact figures (full hue ramps, the
> other product hexes, exact type/radius/shadow/duration steps). To fill them:
> on the design-system page open **"Figma Variables & CSS Export"**, click
> **"CSS Custom Properties"** (or **"Copy all"**), and paste the text — every
> remaining value resolves exactly. `/* verify */` = read at low resolution.

## Tier 1 — Primitives (raw, product-agnostic)

### Color ramps (named by hue, not product)
- `--ac-gray-{50…950}` — `‹from CSS export — 11-step gray ramp›`
- `--ac-purple-{50…950}` — centered on `--ac-purple-500: #6633BB`; rest `‹from CSS export›`
- Status hues: `--ac-emerald-500: #10B981` /* verify */, `--ac-amber-500: #F59E0B`,
  `--ac-red-500: #EF4444`, `--ac-blue-500: #3B82F6`
- Other product hues: `--ac-indigo-*`, `--ac-sky-*`, `--ac-violet-*` — `‹from CSS export›`

### Scales
- Spacing (4px base): `--ac-space-1:4px … --ac-space-12` — `‹exact steps from export›`
  (typical: 4/8/12/16/24/32/48/64)
- Radius: `--ac-radius-{none|sm|base|md|lg|xl|2xl}` + `--ac-radius-full:9999px` — `‹exact px from export›`
- Type size: `--ac-text-{xs|sm|md|lg|xl|2xl|display}` — `‹from export›`;
  `--ac-leading-*`, `--ac-weight-*`
- Fonts: `--ac-font-mono: "JetBrains Mono", …`; `--ac-font-sans: ‹from export›`
- Elevation: `--ac-shadow-{0…5}` — `‹from export›`
- Motion: `--ac-duration-instant:50ms`, `--ac-duration-fast:100ms` /* verify */,
  `--ac-duration-base:150ms` /* verify */, `--ac-duration-slow:250ms` /* verify */,
  `--ac-duration-slower:400ms` /* verify */, `--ac-duration-slowest:600ms` /* verify */

## Tier 2 — Semantic (theme- & product-aware) — UI CONSUMES THESE

Default = dark theme, KubeStash brand. See `token-architecture.md` for the full
table and the light-theme + per-product overrides.

| Token                 | Default value                | Usage                       |
| --------------------- | ---------------------------- | --------------------------- |
| `--ac-bg`             | `var(--ac-gray-950)`         | Page background             |
| `--ac-surface`        | `var(--ac-gray-900)`         | Cards, panels               |
| `--ac-fg`             | `var(--ac-gray-50)`          | Primary text                |
| `--ac-fg-muted`       | `var(--ac-gray-400)`         | Secondary text              |
| `--ac-fg-subtle`      | `var(--ac-gray-500)`         | Captions, timestamps        |
| `--ac-fg-code`        | `var(--ac-purple-300)`       | Inline code, mono data      |
| `--ac-fg-on-brand`    | `#fff` (dark on light primaries) | Text/icons on brand fills |
| `--ac-link`           | `var(--ac-brand)`            | Interactive text / links    |
| `--ac-border`         | `rgba(255,255,255,.08)`      | Hairlines                   |
| `--ac-border-strong`  | `rgba(255,255,255,.16)`      | Emphasized dividers         |
| `--ac-focus-ring`     | `#6634CC`                    | Keyboard focus ring         |
| `--ac-brand`          | `var(--ac-brand-500)`        | Brand primary (per product) |
| `--ac-brand-hover`    | `#9949EE` /* verify */       | Brand hover                 |
| `--ac-brand-subtle`   | `‹from export›`              | Subtle brand surface        |
| `--ac-brand-border`   | `#361279` /* verify */       | Brand-colored borders       |
| `--ac-brand-solid`    | `#6633BB`                    | Fixed brand fill (buttons)  |
| `--ac-status-success` | `var(--ac-emerald-500)`      | Healthy, passing            |
| `--ac-status-warning` | `var(--ac-amber-500)`        | Degraded, retrying          |
| `--ac-status-error`   | `var(--ac-red-500)`          | Failed, critical            |
| `--ac-status-info`    | `var(--ac-blue-500)`         | Informational, pending      |

## Per-product brand bindings (`data-product`)

Each product theme rebinds the brand ramp to its hue. Hexes from the AppsCode
product palette (KubeStash confirmed; rest `‹from CSS export›`):

| Product       | `--ac-brand-500`        |
| ------------- | ----------------------- |
| `kubestash`   | `#6633BB`               |
| `kubedb`      | `‹from export›`         |
| `kubevault`   | `‹from export›`         |
| `voyager`     | `‹from export›`         |
| `stash`       | `‹from export›`         |
| `kubeshield`  | `‹from export›`         |
| `pharmer`     | `‹from export›`         |
| `gateway`     | `‹from export›`         |
| `kubefd`      | `‹from export›`         |
| `confidancer` | `‹from export›`         |

## Type roles (semantic, consume the size scale)

`display` (hero), `heading-*` (H1–H4), `body-{xl|lg|md|sm}`,
`label-{xl|sm}`, `code-{lg|sm}` (JetBrains Mono), `overline` (uppercase eyebrow).
Heading hierarchy is strict (no skipped levels, one H1 per section). Exact px/
line-heights: `‹from export›`.

## Radius role mapping
`radius-none` data tables/code/architecture · `radius-sm` badges/chips ·
`radius-base` secondary buttons/inputs/menus · `radius-md` primary buttons/tags/
tabs · `radius-lg` cards/panels/drawers/tooltips · `radius-xl` feature/hero.

## Elevation roles
`shadow-0` flat/table rows · `shadow-1` chips/badges · `shadow-2` default cards ·
`shadow-3` raised/active · `shadow-4` mega menus/dropdowns · `shadow-5` modals ·
plus Brand Glow (focus/selected/active nav) and Focus Ring.

## Responsive grid
Tablet 8 cols · Desktop/Wide/Max 12 cols; gutters/margins `‹from export›`.
Patterns: hero (12), feature 3-up (4+4+4), content+sidebar (8+4), narrow article
(centered 8), stats 4-up (3+3+3+3).
