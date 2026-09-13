# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Single user (the developer) studying AC213 Cost Accounting at university. Uses the app on a personal Windows computer during study sessions — no sharing, no deployment, no multi-device access.

## Product Purpose

Interactive T-account workbook that automates the mechanical flow of cost accounting entries. The user fills in known values from problem sets; linked accounts auto-populate and balance. Saves completed exercises by name/date, exports to CSV and PDF for submission or review. Replaces pen-and-paper T-account worksheets with instant recalculation and error visibility.

## Positioning

A focused calculator for cost accounting T-account flows — not a general ledger, not a teaching tool, not an ERP. The value is speed: fill in what the problem gives you, see the downstream accounts update instantly, and check your work by hovering to trace where each number came from.

## Operating Context

Used during homework and exam prep for AC213 Cost Accounting. The user works through textbook problems that specify raw material purchases, labor costs, and overhead — then traces the flow through T-accounts (Materials → WIP → Finished Goods → COGS). Three costing systems: actual cost, normal cost (single department), normal cost (two departments). Sessions are typically one problem at a time, saved with a name like "ข้อ 1 บทที่ 3".

## Capabilities and Constraints

- Three page modes: actual cost, normal cost (single dept), normal cost (2 dept)
- Auto-fill flows: source fields propagate to target accounts per the costing system's rules
- Override: user can manually override any auto-filled value
- Save/load named entries to localStorage
- Export current or saved entries as CSV (UTF-8 BOM for Thai)
- Print/PDF via browser print
- Hover-linked highlighting: hovering a flow-connected field highlights all linked fields
- Terminology reference drawer with 14 cost accounting abbreviations (DM, IDM, DL, etc.)
- Built-in calculator (FAB button)
- PWA with service worker for offline use
- Single HTML file, no build step, no dependencies beyond Google Fonts (Sarabun)
- Thai UI copy throughout

## Evidence on Hand

No brand assets, logos, or external imagery. All content is functional UI copy in Thai. The abacus emoji (🧮) serves as the app icon.

## Product Principles

1. **Instant feedback** — every input immediately recalculates all downstream accounts
2. **Trace the flow** — the user should always be able to see where a number came from
3. **Zero friction** — open and start working, no login, no setup, no network needed
4. **Study-session scoped** — save a problem, load it later, export for records
