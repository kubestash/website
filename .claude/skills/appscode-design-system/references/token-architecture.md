# Token Architecture & Naming — AppsCode

This system is **generic across all AppsCode products** (KubeStash, KubeDB,
KubeVault, Voyager, Stash, …) and **all surfaces** (marketing websites, product
dashboards/app UIs). Follow this architecture so one token source themes every
product and surface.

## Single namespace

Every token is prefixed `--ac-` (AppsCode). There is no per-product prefix in
consumed tokens — product differences live in a theme layer, not in token names.
Retire any `--ks-*` / product-specific prefixes.

Format rules:
- lowercase **kebab-case**.
- Order **category → role → modifier → state** (general → specific).
- State is always the suffix: `-hover`, `-active`, `-focus`, `-disabled`,
  `-selected`.
- Numeric scales stay consistent: color `50–950`, space `1–12`, elevation
  `0–5`, type `xs–display`.

## Three tiers

### Tier 1 — Primitives (reference)
Raw, literal values. Product-agnostic. **Never consumed directly by components.**
Grammar: `--ac-<scale>-<step>`.
- Color ramps named by **hue, not product**: `--ac-gray-{50…950}`,
  `--ac-purple-{50…950}`, `--ac-indigo-*`, `--ac-sky-*`, `--ac-emerald-*`,
  `--ac-amber-*`, `--ac-red-*`, `--ac-blue-*`.
- `--ac-space-{1…12}`, `--ac-radius-{none|sm|base|md|lg|xl|2xl|full}`.
- `--ac-text-{xs…display}` (font size), `--ac-leading-*`, `--ac-weight-*`,
  `--ac-font-{sans|mono}`.
- `--ac-shadow-{0…5}`, `--ac-duration-{instant…slowest}`, `--ac-ease-*`,
  `--ac-z-*`.

### Tier 2 — Semantic (system)
Meaning-based, theme- and product-aware. **This is the only tier UI consumes.**
Grammar: `--ac-<category>-<role>-<state>`. Categories: `bg`, `fg`, `border`,
`brand`, `status`, `focus`.

| Token                  | References (default/dark)        | Role                          |
| ---------------------- | -------------------------------- | ----------------------------- |
| `--ac-bg`              | `--ac-gray-950`                  | Page background               |
| `--ac-bg-subtle`       | `--ac-gray-900`                  | Inset/secondary background    |
| `--ac-surface`         | `--ac-gray-900`                  | Cards, panels                 |
| `--ac-surface-raised`  | `--ac-gray-850`                  | Raised cards, menus           |
| `--ac-fg`              | `--ac-gray-50`                   | Primary text                  |
| `--ac-fg-muted`        | `--ac-gray-400`                  | Secondary text                |
| `--ac-fg-subtle`       | `--ac-gray-500`                  | Captions, timestamps          |
| `--ac-fg-code`         | `--ac-purple-300`                | Inline code, mono data        |
| `--ac-fg-on-brand`     | `#fff`                           | Text on brand fills           |
| `--ac-link`            | `var(--ac-brand)`                | Interactive text / links      |
| `--ac-border`          | `rgba(255,255,255,.08)`          | Hairlines                     |
| `--ac-border-strong`   | `rgba(255,255,255,.16)`          | Emphasized dividers           |
| `--ac-focus-ring`      | `var(--ac-brand-border)`         | Keyboard focus ring           |
| `--ac-brand`           | `var(--ac-brand-500)`            | Brand primary (per product)   |
| `--ac-brand-hover`     | `var(--ac-brand-400)`            | Brand hover                   |
| `--ac-brand-active`    | `var(--ac-brand-600)`            | Brand pressed                 |
| `--ac-brand-subtle`    | `var(--ac-brand-950)`            | Subtle brand surface          |
| `--ac-brand-border`    | `var(--ac-brand-700)`            | Brand-colored borders         |
| `--ac-brand-solid`     | `#6633BB`                        | Fixed brand fill (buttons)    |
| `--ac-status-success`  | `--ac-emerald-500`               | Healthy, passing              |
| `--ac-status-warning`  | `--ac-amber-500`                 | Degraded, retrying            |
| `--ac-status-error`    | `--ac-red-500`                   | Failed, critical              |
| `--ac-status-info`     | `--ac-blue-500`                  | Informational, pending        |
| `--ac-status-*-bg`     | tinted variant of each           | Status background fills       |

### Tier 3 — Component (optional)
Component-scoped aliases that reference semantic tokens only. Use when a
component needs stable hooks for theming overrides.
Grammar: `--ac-<component>-<part>-<prop>-<state>`.
Examples: `--ac-button-bg`, `--ac-button-bg-hover`, `--ac-card-radius`,
`--ac-input-border-focus`.

## Theming model — two independent axes

Compose **color-scheme** (`data-theme`) and **product** (`data-product`)
separately. A KubeDB dashboard in dark mode = `<html data-product="kubedb"
data-theme="dark">`.

```css
/* color scheme flips surfaces + text */
:root, [data-theme="dark"]  { --ac-bg: var(--ac-gray-950); --ac-fg: var(--ac-gray-50);  --ac-border: rgba(255,255,255,.08); }
[data-theme="light"]        { --ac-bg: #fff;               --ac-fg: var(--ac-gray-900); --ac-border: rgba(0,0,0,.08); }

/* product theme rebinds ONLY the brand ramp; everything else is shared */
[data-product="kubestash"]  { --ac-brand-500: var(--ac-purple-500); /* + 50…950 */ }
[data-product="kubedb"]     { --ac-brand-500: var(--ac-indigo-500); }
[data-product="kubevault"]  { --ac-brand-500: var(--ac-sky-500); }
[data-product="voyager"]    { --ac-brand-500: var(--ac-violet-500); }
[data-product="stash"]      { --ac-brand-500: var(--ac-purple-500); }
```

Because components read `--ac-brand` / `--ac-bg` (never a hue or product name),
the same component themes itself for every product and scheme automatically.

> Mechanism (chosen default): **`data-product` + `data-theme` attributes.**
> Class-based theming (`.theme-light`) works identically if you prefer Tailwind's
> class dark-mode strategy; `light-dark()` can replace the `data-theme` blocks in
> modern browsers. Pick one and keep it consistent.

## Per-product primary color (the core multi-brand rule)

Each product has a different primary; that primary is the **only** thing that
changes between products. Handle it in four moves — set one variable per product,
and the whole brand family follows.

**1. Define each product primary as a full hue ramp in the primitives** (named by
hue, shared by all):

```css
:root {
  --ac-purple-50: …; --ac-purple-500: #6633BB; --ac-purple-950: …;  /* KubeStash */
  --ac-indigo-50: …; --ac-indigo-500: #4F46E5; --ac-indigo-950: …;  /* KubeDB */
  --ac-sky-50:    …; --ac-sky-500:    #0EA5E9; --ac-sky-950:    …;  /* KubeVault */
  --ac-violet-50: …; --ac-violet-500: #7C3AED; --ac-violet-950: …;  /* Voyager */
}
```

**2. Make `--ac-brand-*` a semantic ramp** that defaults to one product, and have
each product theme rebind it (the whole 50–950 ramp, not just 500):

```css
:root {                       /* default brand = KubeStash */
  --ac-brand-50:  var(--ac-purple-50);
  --ac-brand-500: var(--ac-purple-500);
  --ac-brand-950: var(--ac-purple-950);
}
[data-product="kubedb"] {
  --ac-brand-50:  var(--ac-indigo-50);
  --ac-brand-500: var(--ac-indigo-500);
  --ac-brand-950: var(--ac-indigo-950);
}
[data-product="kubevault"] { --ac-brand-500: var(--ac-sky-500);    /* +50…950 */ }
[data-product="voyager"]   { --ac-brand-500: var(--ac-violet-500); /* +50…950 */ }
```

**3. Derive every brand role from the ramp once** — because these point at
`--ac-brand-*` (not at a hue), rebinding the ramp cascades through all of them:

```css
:root {
  --ac-brand:        var(--ac-brand-500);
  --ac-brand-hover:  var(--ac-brand-400);
  --ac-brand-active: var(--ac-brand-600);
  --ac-brand-subtle: var(--ac-brand-950);
  --ac-brand-border: var(--ac-brand-700);
  --ac-link:         var(--ac-brand);
  --ac-focus-ring:   var(--ac-brand-border);
}
```

**4. Components reference roles only:**

```css
.button-primary       { background: var(--ac-brand); }
.button-primary:hover { background: var(--ac-brand-hover); }
.card--selected       { box-shadow: 0 0 0 2px var(--ac-brand-border); }
```

A KubeDB dashboard is then just `<html data-product="kubedb" data-theme="dark">`
and every button, link, focus ring, and selected state turns indigo — no
component changes.

### Sharp edges to handle

- **Use full ramps, not a single hex.** Hover/active/subtle/border all pick a
  ramp step. With only a `500` you'd have to compute these at runtime. If a
  product only has a `500`, generate the ramp from it and tune by eye.
- **Contrast on brand fills.** White text fails on lighter primaries, so make the
  on-brand foreground a token: `--ac-fg-on-brand` (default `#fff`). Any product
  with a light primary overrides it to a dark value to keep WCAG AA:
  ```css
  :root                    { --ac-fg-on-brand: #fff; }
  [data-product="gateway"] { --ac-fg-on-brand: var(--ac-gray-950); } /* light primary */
  ```
- **`--ac-brand-solid` is the exception.** It is fixed (`#6633BB`) regardless of
  product — use it only for shared corporate AppsCode fills, not product brand.
- **Theme × product are independent.** `data-theme` only touches surfaces/text;
  `data-product` only touches the brand ramp. All combinations work for free.

## Mapping to DTCG JSON & Tailwind

Token group nesting mirrors the prefix, so the same names round-trip through
Tokens Studio / Style Dictionary and Tailwind:

```jsonc
// W3C DTCG — groups mirror --ac-<category>-<role>
{ "ac": { "color": { "brand": {
  "$value": "{ac.color.purple.500}", "$type": "color",
  "hover": { "$value": "{ac.color.purple.400}", "$type": "color" } } } } }
```

```js
// Tailwind: alias utilities to the semantic vars (theme-agnostic)
colors: {
  bg: 'var(--ac-bg)', fg: 'var(--ac-fg)',
  brand: { DEFAULT: 'var(--ac-brand)', hover: 'var(--ac-brand-hover)' },
  success: 'var(--ac-status-success)',
}
```

## Migration from the KubeStash-prefixed tokens

| Old (`--ks-*`)        | New (`--ac-*`)                                   |
| --------------------- | ------------------------------------------------ |
| `--ks-brand-solid`    | primitive `--ac-purple-500` + semantic `--ac-brand-solid` |
| `--ks-brand`          | `--ac-link` (or `--ac-brand`)                    |
| `--ks-brand-hover`    | `--ac-brand-hover`                               |
| `--ks-brand-subtle`   | `--ac-brand-subtle`                              |
| `--ks-brand-border`   | `--ac-brand-border` / `--ac-focus-ring`          |
| `--ks-text`           | `--ac-fg`                                         |
| `--ks-text-tertiary`  | `--ac-fg-subtle`                                 |
| `--ks-text-code`      | `--ac-fg-code`                                   |
| `--ks-border`         | `--ac-border`                                    |
| `--ks-border-strong`  | `--ac-border-strong`                             |
| `--ks-border-focus`   | `--ac-focus-ring`                                |
| `--ks-success/...`    | `--ac-status-success/warning/error/info`         |
| `--ks-duration-*`     | `--ac-duration-*`                                |
| `--ac-kubestash` etc. | primitive hue ramp + `data-product` theme binding |
