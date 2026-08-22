---
name: PT Glory Return Report
description: Warm-neutral executive/ops dashboard where one rust-orange accent marks meaning, mono numerals carry all data, and hairline borders replace shadows.
colors:
  rust-orange: "#c2410c"
  warm-paper: "#f7f6f3"
  panel-white: "#ffffff"
  panel-tint: "#f1efea"
  raised-tint: "#e8e5de"
  ink: "#1c1b19"
  ink-soft: "#57534c"
  muted: "#79746c"
  grid-line: "#e7e4dd"
  baseline-line: "#d9d5cb"
  hairline-border: "#e3e0d8"
  chart-blue: "#35618f"
  chart-green: "#1f7a4d"
  chart-purple: "#6b4fb0"
  chart-pink: "#a83f6c"
  chart-teal: "#1f7d88"
  chart-indigo: "#4a4a9c"
  signal-good: "#1f7a4d"
  signal-warning: "#92600a"
  signal-critical: "#b3271c"
typography:
  display:
    fontFamily: "JetBrains Mono, ui-monospace, SFMono-Regular, Menlo, monospace"
    fontSize: "28px"
    fontWeight: 700
    lineHeight: 1.1
    letterSpacing: "-0.01em"
  headline:
    fontFamily: "Prompt, Noto Sans Thai, system-ui, sans-serif"
    fontSize: "26px"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "-0.01em"
  title:
    fontFamily: "Prompt, Noto Sans Thai, system-ui, sans-serif"
    fontSize: "14px"
    fontWeight: 600
    lineHeight: 1.3
  body:
    fontFamily: "Prompt, Noto Sans Thai, system-ui, sans-serif"
    fontSize: "13.5px"
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "JetBrains Mono, ui-monospace, SFMono-Regular, Menlo, monospace"
    fontSize: "11px"
    fontWeight: 600
    letterSpacing: "0.03em"
    fontFeature: "small-caps (font-variant, not text-transform)"
rounded:
  hairline: "4px"
  chip: "5px"
  icon-chip: "6px"
  control: "7px"
  interactive-row: "8px"
  mark: "9px"
  field: "10px"
  card: "12px"
  overlay: "14px"
  pill: "999px"
spacing:
  xs: "4px"
  sm: "8px"
  md: "12px"
  lg: "16px"
  xl: "24px"
  2xl: "32px"
components:
  button-primary:
    backgroundColor: "{colors.rust-orange}"
    textColor: "#ffffff"
    rounded: "{rounded.mark}"
    padding: "11px 14px"
  button-secondary:
    backgroundColor: "{colors.panel-tint}"
    textColor: "{colors.ink-soft}"
    rounded: "{rounded.control}"
    padding: "5px 10px"
  card:
    backgroundColor: "{colors.panel-white}"
    rounded: "{rounded.card}"
    padding: "20px"
  nav-link-active:
    backgroundColor: "{colors.panel-tint}"
    textColor: "{colors.ink}"
    rounded: "{rounded.field}"
    padding: "10px 12px"
---

# Design System: PT Glory Return Report

## Overview

**Creative North Star: "Clean SaaS Dashboard" (the standing exit)**

The direction contract's own record names the choice explicitly: offered a rolled direction ("postal receipt duplicate") and a pick ("courier waybill label"), the user took the standing exit instead — the category-standard dashboard convention, played straight, built to the craft bar of Stripe Dashboard, Linear, and Notion rather than to either of the offered visual worlds. What shipped honors that choice: no postal-receipt or waybill motifs anywhere in the system. This is a document meant to be read at a glance and trusted at a glance — an executive reads four numbers and one chart in ten seconds, ops drills any row without losing place. Nothing on the page performs; everything on the page reports.

The build refuses the neon-icon-badge SaaS-template default on purpose, and the refusal held: stat cards carry no icon badges, the palette spends its one accent (rust orange) only where a click or a value means something, and depth reads through hairline borders and a soft shadow rather than blocks of color or hard-offset shadows. The ground is warm-neutral in both light and dark — a deliberate departure from the cool blue-black dark mode this build started with, rebalanced mid-build to stay in the same warm hue family as light so the two themes read as one surface, not two products.

**Key Characteristics:**
- One accent (rust orange), spent only on brand, navigation, focus, and hover interaction, plus exactly one alert chip — never a plain chart color.
- All numeric and tabular values render in mono with tabular figures; all prose and labels render in Prompt (Thai body text).
- Cards are flat at rest (hairline border + a whisper of shadow), lift only on hover or as overlays — never neobrutalist, never ambient-only.
- Icons are 100% custom-drawn inline SVG at a consistent stroke weight; there is no unicode glyph anywhere in the shipped file.
- Bar charts ship in two deliberate variants (roomy, compact) chosen by available card width, not by chart type.

## Colors

The palette is warm-neutral paper and ink at rest, with color reserved for two non-overlapping jobs: one accent that marks meaning and interaction, and a fixed set of muted hues that exist only to tell chart series apart.

### Primary
- **Rust Orange** (`#c2410c` light / `#ff9142` dark): the single accent. Used only for the brand mark, the active sidebar nav item (background chip + icon), the focus-visible ring, interactive hover states (links, the expand-button border/text, list-row title on hover), the sort-direction triangle on table headers, and exactly one "needs attention" stat-delta chip (`.flag`, paired with the critical signal color). It is never used as a plain chart series color — the codebase corrected this once already (see Named Rules).

### Categorical (Charts Only)
Six muted hues exist solely to distinguish data series in charts and are never applied to UI chrome, buttons, links, or any interactive element:
- **Chart Blue** (`#35618f` / `#6e97e0`): default single-series bar color (unit returns, daily trend line) and the "at/below average" band in the rate chart.
- **Chart Green** (`#1f7a4d` / `#2ed48e`): one region-donut slice.
- **Chart Purple** (`#6b4fb0` / `#ab8af5`): status breakdown bars, one region-donut slice.
- **Chart Pink** (`#a83f6c` / `#f07eb4`): sales-channel bars, one region-donut slice.
- **Chart Teal** (`#1f7d88` / `#4fd2d8`): payment-method bars, one region-donut slice.
- **Chart Indigo** (`#4a4a9c` / `#8b8ef2`): product-breakdown bars, the largest region-donut slice. Added specifically to take over categorical duty that had originally, incorrectly, used the brand accent.

### Semantic
- **Signal Good** (`#1f7a4d` / `#2ed48e`): reserved for positive/normal-range meaning. (Coincides with Chart Green's hex in both themes — a shared value, not a shared role; keep them as separate tokens since one is semantic and one is a chart series assignment.)
- **Signal Warning** (`#92600a` / `#f2a93b`): drives `.stat-delta.caveat` — an interpretive caveat where a number is real but its causal meaning isn't proven yet (e.g. "94.6% automated" flagged "not yet the cause").
- **Signal Critical** (`#b3271c` / `#f2515e`): drives `.stat-delta.flag` — a genuine alert, and the rate-chart / watchlist color for values at or above 2× the company average.

### Neutral
- **Warm Paper** (`#f7f6f3` / `#16130f`): page background.
- **Panel White** (`#ffffff` / `#211c15`): card, sidebar, and modal surfaces.
- **Panel Tint** (`#f1efea` / `#2a231a`): hover fill for rows and nav items, bar-track background, secondary-button fill.
- **Raised Tint** (`#e8e5de` / `#372e21`): tooltip surface.
- **Ink** (`#1c1b19` / `#f4efe6`): primary text.
- **Ink Soft** (`#57534c` / `#b9b0a0`): secondary text (descriptions, table body text).
- **Muted** (`#79746c` / `#8b8172`): tertiary text (labels, meta, legend lines).
- **Grid Line** (`#e7e4dd` / `#302921`): table row dividers.
- **Baseline Line** (`#d9d5cb` / `#3e3427`): table header rule, scrollbar thumb, hover border on stat cards.
- **Hairline Border** (`#e3e0d8` / `#2b2418`): the default 1px border on every card, input, and chip.
- **Overlay Scrim** (`rgba(20,18,14,0.55)`, both themes): the modal backdrop only. A fixed warm near-black at 55% opacity plus a 2px blur — deliberately not a themed token (it doesn't flip with light/dark) since its job is purely to recede the page behind an overlay, not to carry the palette.

### Named Rules
**The Accent-Is-Meaning Rule.** Rust orange appears only where a viewer would want to click, focus, or be alerted — brand, active nav, focus ring, hover, sort indicator, one alert chip. It never fills a chart series and never decorates a surface for its own sake.

**The Categorical-Never-Chrome Rule.** Chart Blue/Green/Purple/Pink/Teal/Indigo are reserved for chart data series. None of them may back a button, link, nav state, or any other interactive element — that vocabulary belongs to the accent alone.

**The Alert-Versus-Caveat Rule.** Critical (red) and Warning (amber) are not interchangeable severities of the same thing. Critical marks a real, actionable problem (`.flag`). Warning marks a number that is correct but not yet proven to mean what it looks like it means (`.caveat`) — this dashboard's core discipline (rate-over-raw-count, no fabricated root cause) is enforced visually through this distinction.

**The Warm-In-Both-Themes Rule.** Dark mode is not a hue-inverted palette; it is the same warm-neutral family (paper/ink, not blue/black) carried into a dark register. Any new dark-mode surface should read as "the same room with the lights off," not a different, cooler product.

## Typography

**Display Font:** JetBrains Mono (with ui-monospace, SFMono-Regular, Menlo fallback)
**Body Font:** Prompt (with Noto Sans Thai, system-ui fallback)
**Label/Mono Font:** JetBrains Mono — same family as Display, distinguished by size/weight, not by a separate face

**Character:** A geometric mono for everything that is a number, set against a warm humanist sans for everything that is a sentence — the pairing itself performs the dashboard's thesis: reportage over decoration.

### Hierarchy
- **Display** (700, 28px, line-height 1.1, mono, tabular-nums): the KPI stat-value — the largest, most confident mark on the page, and the only place the type ramp goes big. The donut-center total (24px) and the gate/brand mark glyph (17px) are the same role at smaller anchor sizes for a smaller focal container.
- **Headline** (700, 26px, line-height 1.2, Prompt): the page `<h1>` title only. Deliberately not larger than the stat-value display size — this is a numbers-first page, not a headline-first one.
- **Title** (600, 14–15px, Prompt): card-head `<h3>` section titles (14px), dialog titles — modal-head `<h3>` (15px) and the gate card's `<h2>` (15px on the mark, 17px on the heading itself, since the gate is a full-screen focal moment and earns slightly more weight than an inline modal header).
- **Body** (400–500, 12–13.5px, Prompt, line-height 1.55): page description (13.5px), table/modal body text and gate copy (12–12.5px), list-row subtitles and modal notes (12px). Page description caps at ~64ch. This role is a deliberate micro-scale, not one fixed size: a data-dense report distinguishes primary body copy from secondary captions from tertiary meta by a half-to-one pixel step rather than a weight or color change alone, so 12/12.5/13/13.5px are all legitimate Body-role instances, chosen by how far the text sits from the primary reading line.
- **Label** (600, 10–11.5px, mono, letter-spacing 0.03em, uppercase or small-caps): stat labels (11px), sidebar nav group label and table column headers (10.5px), chart axis labels (10px), legend lines (11.5px). Same micro-scale principle as Body: the Label role covers a half-step band, not one literal size.

### Named Rules
**The Mono-For-Data Rule.** Every numeric or tabular value — stat values, table numbers, chart values, donut totals, dates in the sidebar footer — renders in JetBrains Mono with `font-variant-numeric: tabular-nums`. Prompt is never used to display a number that means something quantitatively; this is what lets an ops reader's eye lock onto a column and compare rows without re-parsing font shapes.

**The Small-Caps Label Rule.** `.stat-label` uses `font-variant: small-caps`, not `text-transform: uppercase` — a deliberately different mechanism from every other label in the system (nav group label and table headers use uppercase). It is a durable, code-level commitment to a small-caps treatment specifically for KPI labels, kept distinct even though the choice currently reads identically to uppercase on this page's all-Thai label content (Thai has no letter case, so small-caps has no visible effect here). Preserve the mechanism for when a KPI label is set in Latin script.

## Layout

A fixed 250px sidebar (sticky, full viewport height) plus a fluid content column capped at 1320px and centered, with 32px horizontal page padding and 96px of bottom padding for scroll clearance past the last section. Below 900px the sidebar collapses to a horizontal, scrollable top bar and drops its group label and footer; below 760px every grid column stacks to one.

The page is a vertical stack of cards at 24px gaps, each card holding 16px-gapped internal grids (`grid-4`, `grid-3`, or an asymmetric `grid-2` at 1.15fr/0.85fr for donut-plus-list pairings). `grid-4` drops to two columns at 1100px before stacking fully at 760px. Card internal padding is a flat 20px regardless of card type. The rhythm is dense but not cramped: 4px separates the smallest related elements (a label from its icon), 8–16px separates rows and grid cells, 24–32px separates major sections.

## Elevation & Depth

Hairline borders carry the primary depth signal; shadow is a secondary, mostly-at-rest-invisible cue, never a structural device. Every card sits on a 1px `hairline-border` with `shadow-sm` (a near-imperceptible 1px/2px ambient shadow) at rest — this reads as "a sheet of paper on a table," not "a raised block."

### Shadow Vocabulary
- **shadow-sm** (`0 1px 2px rgba(28,27,25,.05)` light / `0 1px 2px rgba(0,0,0,.3)` dark): resting state for every card.
- **shadow-md** (`0 6px 16px -4px rgba(28,27,25,.12), 0 2px 4px -2px rgba(28,27,25,.08)` light): hover/interactive lift — stat-card hover only.
- **shadow-lg** (`0 20px 44px -12px rgba(28,27,25,.22), 0 4px 10px -4px rgba(28,27,25,.1)` light): reserved for overlays — the detail modal and the auth gate card. Never used on an in-flow element.

### Named Rules
**The Hairline-First Rule.** Depth is a border-and-shadow-sm story at rest; shadow only escalates (to md) in direct response to hover/interactive state, and only escalates further (to lg) for content that floats above the page entirely (modal, gate). A card should never need a stronger shadow than `shadow-sm` to justify its own existence on the page.

## Shapes

Corner radius scales with control size rather than following one flat value: 4px on the smallest linear elements (bar tracks/fills, the focus-visible ring), 5px on the stat-delta chip (a small text pill that sits between the linear 4px step and the icon-chip 6px step — its own step, not a rounding of either neighbor), 6px on small icon chips (nav icon slot, watchlist rank badge), 7px on the secondary button, 8px on hover-revealed row backgrounds and small notes, 9–10px on marks/inputs/nav links, 12px on the base card unit, and 14px on anything that floats above the page (modal, gate card). A single pill radius (999px) appears only for true dots and rules — legend swatches and the scrollbar thumb. Borders throughout are 1px hairlines in `hairline-border`; there is no double-border, ring, or hard offset shadow anywhere in the system.

## Components

### Buttons
- **Shape:** radius scales by role — 9px on the primary action (`{rounded.mark}`), 7px on the secondary/ghost action (`{rounded.control}`), 8px on the icon-only close button.
- **Primary:** solid rust orange background, white text, 600 weight, 11px/14px padding (the auth-gate submit button is the shipped example of this pattern). Hover: opacity to 0.9, no color or shape change.
- **Secondary / Ghost:** the `.expand-btn` pattern — panel-tint background, hairline border, ink-soft text, mono 11px/600. Hover swaps border-color and text-color to the accent; background never changes.
- **Icon-only:** `.modal-close` — panel-tint chip, hairline border, custom inline SVG (stroke-width 2, no unicode ✕). Hover swaps border and icon color to critical red, signaling "this closes/discards," not "this is the accent action."

### Cards / Containers
- **Corner Style:** 12px (`{rounded.card}`).
- **Background:** panel-white; `panel-tint` for internal hover surfaces (rows, hover backgrounds).
- **Shadow Strategy:** `shadow-sm` at rest; see Elevation & Depth.
- **Border:** 1px hairline-border.
- **Internal Padding:** 20px, flat across all card types.

### Stat Card (signature component)
The KPI anatomy, used identically for all seven top-row metrics: a small-caps mono label above a large mono tabular-nums value, with an optional inline delta chip (`.flag` critical / `.caveat` warning / `.plain` neutral) immediately after the number. **No icon badge ever precedes the label or value** — this is the concrete rejection of the neon-icon-badge SaaS default the direction contract names. The whole card is a click target (cursor:pointer, hover lifts to `shadow-md` + 2px translateY) that opens the matching detail modal; the affordance is the lift and border-color shift, not a visible button.

### Bar Chart — two variants (signature component)
- **Roomy** (default): `label | track | value` in one row (`grid-template-columns: 150px 1fr 96px`). Used only in the two wide `grid-2` cards (rate-by-unit, unit-returns) where the card has enough horizontal room for a fixed label column.
- **Compact**: label and value share one line, a full-width thin (6px) track sits on the row below (`grid-template-areas: "label value" "track track"`). Used everywhere a bar chart sits in a narrower multi-column card (product, status, payment, channel breakdowns) — the roomy layout was added specifically because the fixed-column variant collapses to invisible slivers under roughly 260px of card width; compact was built as the fix, not a stylistic alternative.
- Bars reveal via `transform: scaleX(0 → 1)` from a fixed `transform-origin: left center` on a `requestAnimationFrame` double-defer, never by animating `width`. **The Transform-Not-Width Rule**: any future bar-style reveal animates a transform, never a layout-triggering property — this is what keeps the reveal cheap regardless of how many bars are on screen.
- The rate-by-unit chart is a distinct threshold-colored variant: bar color itself carries severity (critical at ≥2× company average, warning at ≥1×, chart-blue below), plus a dashed reference line marking the average — color is data here, not decoration.

### Donut + Line Charts
- Donut: hand-drawn SVG arc segments (`--panel-2` track), a mono center total, and a legend list of pill swatches + values below, each row hover-highlighted like a table row.
- Line: SVG path with a low-opacity (12%) fill under the line, 2.25px stroke, only the peak point gets a value label and larger dot — the chart states its own headline finding (the peak day) rather than requiring the reader to find it.

### Table
- **Style:** hairline row dividers (`grid-line`), sticky mono uppercase headers on a `baseline-line` rule, right-aligned mono tabular numeric columns.
- **Sort:** every table header is click-and-keyboard sortable (`enableSort()` — tabIndex, `role="columnheader button"`, `aria-sort`, Enter/Space), numeric-aware (strips non-numeric characters before comparing). The active sort column turns accent-orange with a CSS border-trick triangle (no unicode arrow) pointing in the sort direction.
- **Row hover:** fills with panel-tint; no row-level accent color.

### Navigation
- Sidebar: brand mark (orange, mono initials) + name/sub, then a mono uppercase group label, then nav links. Default state is ink-soft text; hover and active states both fill panel-tint, but only the active link's icon chip fills accent orange with white icon — hover never touches the accent.
- Below 900px: sidebar becomes a horizontal scrollable bar; group label and footer disappear; the pattern degrades to icons+labels only.

## Do's and Don'ts

### Do:
- **Do** spend rust orange only on brand, active-nav, focus, hover, sort-indicator, and the one real alert chip.
- **Do** render every numeric/tabular value in JetBrains Mono with tabular-nums — no exceptions.
- **Do** keep cards at hairline-border + `shadow-sm` rest state; escalate to `shadow-md` only on hover/interactive and `shadow-lg` only for true overlays.
- **Do** draw every icon as inline custom SVG at `stroke-width:2` — the modal-close icon was corrected from a unicode ✕ specifically to hold this line.
- **Do** switch a bar chart from roomy to compact once its card drops below ~260px of usable width, rather than letting the roomy layout collapse.
- **Do** animate bar fills with `transform: scaleX()`, never `width`.
- **Do** keep the warm-neutral hue family in dark mode — same room, lights off, not a different palette.

### Don't:
- **Don't** use any of the six categorical chart hues (blue/green/purple/pink/teal/indigo) on a button, link, nav item, or any other interactive chrome.
- **Don't** use rust orange as a plain chart data-series color — that mistake was already made and corrected once (indigo was added to fix it).
- **Don't** add an icon badge to a stat card — label-over-value is the complete anatomy.
- **Don't** use a hard-offset / neobrutalist shadow anywhere in this system; the only shadow vocabulary is the soft `shadow-sm/md/lg` ramp.
- **Don't** use a unicode glyph for any icon, arrow, or close affordance — every mark is a drawn SVG, including the table sort triangle (CSS border-trick, not `▲`/`▼`).
