# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

PT Glory internal team, at two depths on the same dashboard:
- **Executives (ผู้บริหาร):** skim the top KPI row and the "what executives should know" / concentration-facts sections once a month to spot which shops (units), products, or carriers are driving return-shipment losses, and decide where to intervene.
- **Operations staff:** use the same dashboard more often to drill into the detail tables and charts (per-unit rate, per-product, per-region, per-carrier, shipping status, payment method) to chase down and act on specific problems.

Access is restricted to PT Glory team members only, gated by Vercel Authentication (invite-only via Vercel Team membership).

## Product Purpose

A recurring internal reporting dashboard that turns PT Glory's raw return-shipment order data (from a Google Sheet) into a readable monthly summary: how many orders were returned, how much revenue that represents, which units/products/regions/carriers are disproportionately affected (rate, not just raw count), and what the data still can't explain yet. Success is executives and ops correctly identifying the true outliers (rate vs. sales, not raw volume) and knowing what data gap to close next — not just seeing numbers.

## Positioning

Not a market-facing product — an internal single-purpose reporting surface. Its distinguishing move versus a raw data dump is doing the analysis work for the reader: normalizing raw return counts against each unit's actual sales volume to surface true outliers (e.g., flagging UNIT23 at 12.7% as the real problem even though other units return more orders in raw count), and explicitly calling out what the underlying data still lacks (e.g., no "reason for return" column) rather than presenting incomplete data as conclusive.

## Operating Context

- Data originates in a Google Sheet ("สรุปรายการสินค้าตีกลับเดือน ก.ค. 2569") with tabs `Discuse` (full return-order database for the month), `Total_Order on Sell` (sales totals used as the denominator for return-rate %), and `config` (helper formulas, e.g. date-range QUERY for month-scoped sales).
- **No live data connection.** Numbers are manually copied from the Sheet and hand-embedded as static values directly in `index.html` — there is no build step and no API/fetch.
- **Monthly cadence, recurring:** this July 2026 build is the template for future months. The expected workflow each month is: update the Google Sheet → hand-edit the static values/labels in `index.html` → `git push` → Vercel auto-deploys. Same layout and structure, new numbers and month label each cycle.
- Deployed on Vercel as a static site (Framework Preset: Other, no build command/output dir), access-gated via Vercel Authentication so only invited Vercel Team members (PT Glory staff/executives) can view it.
- Return-rate % is deliberately computed against each unit's actual sales volume (not raw return count) to avoid misleading readers, and only for units with enough sales volume (≥300 orders/month) to avoid small-sample distortion.

## Capabilities and Constraints

- Single static HTML file (`index.html`), Thai language (`lang="th"`), no framework, no build tooling, no backend.
- Charts and tables are rendered client-side from data embedded in the page (not fetched at runtime).
- `<meta name="robots" content="noindex, nofollow">` — not meant to be publicly discoverable.
- Light/dark theme both defined via CSS custom properties.
- Update mechanism is manual and static by design (per README) — not a requirement to add live Sheet syncing unless the user asks.

## Evidence on Hand

- The shipped July 2026 report itself (`index.html`) is real embedded data: 3,188 returned orders, ฿1,704,627 in returned merchandise value, 3.4% company-wide return rate against 92,962 July orders (~99%+ of sales matched), 99.7% COD, 95.0% via Flash Express, 94.6% status `SYSTEM_AUTO_RETURN`, per-unit/product/region/carrier breakdowns, and a daily trend for all 31 days.
- The dashboard itself documents known data gaps (a "data enough?" section), notably: **no "reason for return" column exists** in the source data — only shipping status codes, which describe mechanism, not cause. Future work must not fabricate a root-cause field that doesn't exist in the source.
- No customer testimonials, no external benchmarks, no pricing/licensing claims apply — this is an internal ops report, not a marketing surface.

## Product Principles

1. Rate over raw count: always normalize returns against each unit's/segment's own sales volume before calling something an outlier — raw counts alone are misleading and the dashboard exists specifically to correct that instinct.
2. Be honest about data gaps: explicitly surface what the underlying data cannot yet explain (e.g., true return reason) rather than implying the current fields answer more than they do.
3. Static and manual by design: no live Sheet integration is expected or required — the monthly hand-edit-and-redeploy workflow is the accepted, durable process, not a stopgap to be automated away.
4. Internal-only, both audiences at once: the same single page must serve an executive's 30-second skim and an ops staffer's detailed drill-down without a separate "exec view."
5. Same shape every month: this month's layout/structure is the recurring template — future months change data and labels, not structure, unless the user asks for a redesign.

## Accessibility & Inclusion

No product-specific accessibility requirement has been established beyond standard practice; supports both light and dark color schemes already.
