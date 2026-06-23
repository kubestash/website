---
name: appscode-design-system
description: >-
  Apply the AppsCode design system (tokens, components, theming, page patterns)
  when building or auditing UI, dashboards, or pages for any AppsCode product,
  even if unnamed.
---

# Appscode Design System

This skill encodes the AppsCode design system: a single, product-agnostic token
architecture plus components, brand principles, and page patterns that theme every
AppsCode product website and dashboard. Products differ only in a thin brand layer
(`data-product`); color scheme is a separate axis (`data-theme`, light for
marketing / dark for product UI). Apply it whenever producing or reviewing UI so
output is consistent across all AppsCode surfaces.

## When to apply

Apply these guidelines whenever the task involves:

- Generating UI: Vue/Nuxt components, HTML, Tailwind/Sass markup, or design
  mockups for any AppsCode surface — any product website or dashboard.
- Theming: adapting UI for a specific product (`data-product`) or color scheme
  (`data-theme`), or defining/naming new tokens.
- Reviewing or auditing an existing interface for consistency, accessibility,
  or visual quality.
- Producing design specs, redlines, token definitions, or component docs.

## How to use this skill

1. Read `references/token-architecture.md` first for the naming convention, the
   three token tiers (primitive → semantic → component), and the
   `data-product` × `data-theme` theming model. This governs how everything else
   is named and consumed.
2. Read `references/tokens.md` for the concrete values registry. Components
   consume **semantic** tokens (`--ac-bg`, `--ac-fg`, `--ac-brand`, …) only —
   never primitives (`--ac-purple-500`) or product names. Never hardcode a value
   that contradicts a token.
3. Read `references/components.md` when building or reviewing a specific
   component (button, card, navbar, form field, table) for variants, states,
   and usage rules.
4. Read `references/ui-ux-audit.md` when auditing or improving a UI — the brand
   principles, voice, and do/don't judgment calls.
5. Read `references/page-patterns.md` when composing full pages — section
   blueprints (hero, capability grid, workflow tabs, footer) and the
   light-marketing / dark-product rule.

## Core principles

These hold across every Appscode surface:

- **One namespace, semantic consumption.** All tokens are `--ac-*`. Components
  consume **semantic** tokens (`--ac-bg`, `--ac-brand`, `--ac-status-success`),
  never primitives or product-specific names — that is what keeps the system
  generic across products and themes. In Tailwind, alias utilities to the
  semantic vars rather than using arbitrary `[12px]`-style values.
- **Product/theme via data attributes, not forks.** Never hardcode a product's
  color. Let `data-product` rebind the brand ramp and `data-theme` flip the
  color scheme; write components once against semantic tokens.
- **Consistency over novelty.** Reuse existing component patterns rather than
  inventing new ones. A new pattern needs a real justification.
- **Semantic color & purposeful motion.** Color encodes meaning, not decoration
  (no decorative gradients). Motion is functional and within budget (≤400ms
  except page transitions) and respects `prefers-reduced-motion`.
- **Sharp for data, rounded for affordance.** Tables, code, and architecture
  surfaces stay sharp-edged; rounding signals interactivity. Use JetBrains Mono
  for all technical data (tokens, CLI, versions, YAML).
- **Accessibility is non-negotiable.** Meet WCAG AA contrast, provide visible
  focus states, and keep interactive targets at least 44×44px.
- **Match the stack.** Output should fit a Vue 3 + Nuxt + Tailwind/Sass
  codebase. Components are composable and prop-driven; styling leans on Tailwind
  utilities with Sass for anything tokens-heavy.

## Output format for components

When asked to build a component, default to a single-file Vue 3 component using
`<script setup>` and Tailwind utility classes, unless the user specifies HTML,
React, or plain CSS. Include the relevant variants and states from
`references/components.md`, and use design tokens for all visual values.

## Output format for audits

When asked to review or audit a UI, structure the response as:

1. **Summary** — one or two sentences on overall state.
2. **Findings** — grouped by area (color, type, spacing, components,
   accessibility), each with the specific issue and the token/rule it violates.
3. **Recommendations** — concrete fixes, referencing the relevant token or
   component rule.
