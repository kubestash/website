# Brand Principles, Voice & UX Guidance — KubeStash

This is the judgment layer of the design system: the principles, voice, and
do/don't rules that tokens alone can't express. Apply these when building new UI
and when auditing existing UI. The audience is Platform Engineers and SREs who
"write YAML at 2am during incident response" — design for signal over noise.

## The four principles

### 1. Reliability First
Every visual choice signals dependability. Use structured layouts, high-contrast
type, and measured motion — never decorative chrome that could undermine trust.
Infrastructure engineers expect certainty, not surprise.
- **Do:** use consistent component patterns; communicate system state clearly;
  prefer clarity over cleverness.
- **Don't:** add animation purely for aesthetics; use vague or ambiguous labels;
  hide critical status behind interactions.

### 2. Precision over Decoration
The design system is surgical: every element earns its place. Whitespace is
intentional, color is semantic, motion is purposeful.
- **Do:** let content lead the hierarchy; use color to encode meaning; apply
  motion only to guide attention.
- **Don't:** use gradients as decoration; apply large radius to data containers;
  animate elements without a state-change reason.

### 3. Developer-Native
The design system speaks the audience's language: monospace for data, structured
grids for scanning, dark surfaces that don't burn eyes during long sessions.
- **Do:** expose code snippets early in the hierarchy; use tabular layouts for
  configuration data; support keyboard-first navigation.
- **Don't:** force mouse-only interactions; hide technical detail behind
  marketing copy; ship light-mode-only components.

### 4. Honest Complexity
Kubernetes backup is genuinely complex; don't pretend otherwise. Help users
navigate complexity with clear information architecture, progressive disclosure,
and contextual documentation.
- **Do:** surface advanced options via expandable sections; link to docs from UI
  components; use status indicators that reflect real system states.
- **Don't:** over-simplify technical concepts; use euphemisms for errors or
  failures; hide complexity without a clear reveal path.

## Voice & tone (how we sound)

- **Authoritative**, not arrogant: know the domain deeply and speak with
  confidence, but welcome questions.
- **Precise**, not pedantic: use exact language because accuracy matters in
  infrastructure; avoid jargon for its own sake.
- **Direct**, not blunt: get to the point — users are busy; don't bury the lead.
- **Calm**, not cold: even during incidents, communicate with composure; don't
  panic in error states.

## Accessibility (non-negotiable)

- Meet WCAG AA contrast on dark surfaces.
- Every interactive element has a visible keyboard focus ring
  (`--ac-focus-ring` / Focus Ring elevation).
- All motion has a non-animated equivalent and respects
  `prefers-reduced-motion`.
- Status is never conveyed by color alone — pair with icon/label.

## Audit checklist

When reviewing a UI, check each area and cite the token/rule it violates:

1. **Hierarchy** — strict heading order (no skipped levels, one H1 per section);
   content leads, not chrome.
2. **Color** — semantic only; status colors used for status; no decorative
   gradients; AA contrast.
3. **Typography** — roles used correctly; JetBrains Mono for all technical data
   (tokens, CLI, versions, YAML).
4. **Spacing** — values are multiples of the 4px base unit; consistent rhythm.
5. **Radius** — sharp edges for data/tables/code; rounding only for interactive
   affordance.
6. **Elevation** — depth via shadow, not background lightness; correct level for
   the surface type.
7. **Motion** — functional only; within duration budget (≤400ms except page
   transitions); reduced-motion safe.
8. **Accessibility** — focus states, keyboard nav, non-color status cues.
