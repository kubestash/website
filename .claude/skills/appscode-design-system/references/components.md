# Components — AppsCode

Product-agnostic. Components consume **semantic** tokens (`--ac-bg`, `--ac-brand`,
`--ac-fg`, …) so the same component themes itself across every product
(`data-product`) and color scheme (`data-theme`). See `token-architecture.md`.

All visual values reference tokens in `tokens.md` (never raw hex/px). Component
radius/elevation choices follow the system's mappings: data surfaces stay sharp,
interactive elements get measured rounding, depth comes from shadow.

> Exact per-component specs (padding, sizes) come from the design-system page's
> Component Library section. Paste the relevant component values from the Figma
> Make code or CSS export to lock these in precisely.

## Table of contents
- [Button](#button) · [Card](#card) · [Navbar](#navbar) · [Form fields](#form-fields) · [Table](#table) · [Status badge](#status-badge) · [Code block](#code-block)

## Button
Variants: primary, secondary, ghost, danger. Sizes: sm, md, lg.
States: default, hover, active, focus-visible, disabled, loading.
- Primary: `--ac-brand` (per product; #6633BB for KubeStash) background, `radius-md`, label uses
  `label-xl`. Hover → `--ac-brand-hover`.
- Secondary/ghost: `radius-base`, border `--ac-border`.
- Danger: `--ac-status-error`.
- Always show a visible focus ring (`--ac-focus-ring`); min target 44×44px.
- Loading shows a spinner and disables interaction.

## Card
Variants: default, interactive (hover lift), bordered.
- Surface with `--ac-border` hairline, `radius-lg`, Level 2 elevation.
- Interactive cards rise to Level 3 / Brand Glow on hover/selected.
- Internal padding on the 4px scale (≈16/24px).

## Navbar
States: default, scrolled, mobile drawer.
- Mega-menu dropdowns use Level 4 elevation.
- Sticky on scroll with a subtle shadow once scrolled.
- (Record the click-vs-hover trigger decision from the KubeStash navbar work.)

## Form fields
Variants: text, select, textarea, checkbox, radio, toggle.
States: default, focus, filled, error, disabled.
- Border `--ac-border`; focus border `--ac-brand` + focus ring; `radius-base`.
- Error state uses `--ac-status-error` for border and helper text.
- Always provide a real label (placeholder is not a label).

## Table
Variants: default, striped, compact.
- `radius-none` — data tables stay sharp-edged.
- Header text uses `--ac-fg-subtle`; row hover gets a subtle tint.
- Right-align numeric columns; keep readable row height.

## Status badge
- Maps system state to status tokens: `--ac-status-success` (healthy/passing),
  `--ac-status-warning` (degraded/retrying), `--ac-status-error` (failed/critical),
  `--ac-status-info` (pending). `radius-sm`.
- Never color-only — include an icon or text label.

## Code block
- JetBrains Mono, `code-lg`; `radius-none`; Level 0/1.
- Used for CLI commands, YAML/CRD snippets, terminal output. Surface advanced
  config here early in the hierarchy (Developer-Native principle).

<!-- Add any other KubeStash-specific components from the Component Library
     section: snapshot cards, backup-schedule widgets, restore flows, etc. -->
