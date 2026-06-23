# Page Patterns — KubeStash

Reusable section blueprints, derived from the KubeStash homepage. Use these when
composing landing or marketing pages so layout and rhythm stay on-brand.

## Theme rule (important)

KubeStash runs **two themes**:
- **Light theme** — marketing / landing / public website pages (the homepage).
- **Dark theme** — the product UI/app surfaces and the design-system reference.

Pick the theme by surface type. Tokens (`tokens.md`) apply to both; the brand
purple `#6633BB` and semantic status colors are shared across themes.

## Section blueprints

Each major section opens with a small uppercase **overline** eyebrow
(`overline` type role) above its heading.

### Hero
- Left: badge pill (announcement) → big headline with one brand-purple emphasis
  word (e.g. "Recover" in `--ac-brand`, #6633BB for KubeStash) → supporting subhead → primary CTA
  (`Start Free Trial`, brand-solid) + secondary CTA (`Watch Demo`, ghost) →
  "TRUSTED BY" logo row.
- Right: a realistic **product UI card** (e.g. a Backup Status table with
  type/size/status rows, a live indicator, a `helm install` snippet, and a
  "Last restore" stat). Show the product, don't just describe it.

### Stats bar
Four-up metric strip directly under the hero: big number + label
(e.g. `25+ Database Engines`, `10K+ Active Databases Protected`,
`30-Day Free Trial License`, `99.9% Uptime SLA`).

### How it works ("Backup in 4 steps")
Four numbered cards (01–04), each: step title, one-line description, and a small
**monospace code chip** showing the real artifact (`kind: BackupConfiguration`,
`✓ Restore verified`, `kubectl restore --pitr …`). Reinforces Developer-Native.

### Capability grid ("Built for production reliability")
6-card grid (3×2). Each card: icon + a small category **tag badge**
(Core / Recovery / Security / Storage / Performance / Deployment) + title +
2-line description. Cards use `radius-lg`, Level 2 elevation.

### Database support grid
Category cards, each headed by a colored status dot + label (Relational, NoSQL,
Search, Analytics, Messaging, Coordination) containing **monospace chips** for
each engine. Close with a "Need a different database? Contact us →" link.

### Workflow tabs ("From policy to restore")
Tabbed switcher (Define / Monitor / Restore). Left: subhead + 3 checkmark
bullets. Right: a **YAML CRD code block** (JetBrains Mono, `radius-md` panel).

### Solutions by persona ("Built for every team")
4 cards (Platform Engineers, SREs, DevOps Teams, DBAs). Each: a muted
pain-point line, the solution copy, then a row of **tag chips**
(e.g. Policy as Code · GitOps · ArgoCD). Speaks to each audience's real job.

### Outcomes ("What production looks like")
3 large outcome stats with a short attributed quote each
(`50%` faster recovery, `100%` automated backups, `10×` cost reduction).

### Final CTA band
Eyebrow + headline ("Ready to protect your Kubernetes workloads?") + subhead +
primary/secondary CTAs + a row of checkmark trust points. Light-purple tinted
panel with a soft brand glow accent.

### Footer
5-column link grid (Product · Databases · Solutions · Resources · Company) with
brand mark + tagline on the left, legal links (Privacy · Terms · Security · SLA)
and copyright on the bottom row. Always on the deepest surface.

## Composition rules
- One H1 per page (the hero). Every section below is H2 with an overline eyebrow.
- Lead with the product/artifact (code, real UI) high in the hierarchy.
- Keep copy direct and precise; let content lead, chrome stays minimal
  (see the principles in `ui-ux-audit.md`).
- Marketing pages are light; product surfaces are dark.
