# Design

## Visual World

Dual-theme system: **Ledger Paper** (light) and **Financial Terminal** (dark), switchable via a theme toggle button in the app bar. The light theme defaults when the OS is in light mode; the dark theme activates on dark OS preference or explicit toggle. Theme preference persists in localStorage.

### Ledger Paper (Light)

Physical ruled-ledger metaphor. Cream paper ground (`#f5f0e6`), blue-black ink for debit (`#1a2744`), red ink for credit (`#c2342e`), pencil-gray for auto-computed values (`#9a9a8e`). Card borders in warm stone (`#c8c0ae`). Accent is a muted blue (`#7a9ec0`). Numbers render in Sarabun (the body face) with tabular-nums.

### Financial Terminal (Dark)

Bloomberg-style dense data terminal. Dark glass ground (`#141820`), panels at `#1c2230` with subtle amber inset glow. Amber accent (`#e6a520`) for connection lines, navigation highlights, and FAB. Teal for debit (`#4da8b8`), coral for credit (`#e07070`), muted green for auto-filled (`#68a868`). Numbers render in IBM Plex Mono for an LCD readout feel.

## Typography

| Role | Face | Weight | Notes |
|------|------|--------|-------|
| Body / UI | Sarabun | 300, 400, 600, 700 | Thai-first, tabular-nums for all numeric display |
| Numbers (dark theme) | IBM Plex Mono | 400, 500, 600 | LCD-style readout, switches via `--num-ff` token |
| Calculator display | IBM Plex Mono | 600 | Both themes |
| Terminology abbreviations | IBM Plex Mono | 600 | Both themes |

## Color Tokens

All colors are defined as CSS custom properties on `:root` (light) and overridden for dark via `@media (prefers-color-scheme: dark)` guarded by `:root:not([data-theme="light"])`, plus `:root[data-theme="dark"]` for explicit toggle.

Key tokens: `--bg`, `--card`, `--card-b`, `--hdr`, `--hdr-t`, `--dr`, `--cr`, `--in-bg`, `--in-b`, `--au-bg`, `--au-b`, `--au-t`, `--txt`, `--txt2`, `--lbl`, `--line`, `--rule`, `--acc`, `--flash`, `--div`, `--neg`, `--focus-c`, `--focus`, `--nav-act`, `--sub-act`, `--fab-bg`, `--fab-t`, `--fab-sh`, `--calc-num`, `--calc-fn`, `--caret`, `--sel`, `--sb`, `--hl-bg`, `--hl-b`, `--hl-sh`, `--num-ff`.

## Layout

Two-column grid (`grid-template-columns: 1fr 1fr`) at >700px, single column below. Max content width 980px centered. T-account cards use a two-column inner grid for debit/credit sides, collapsing to single column at <=460px.

## Motion

One authored moment: card entrance animation (`card-in`, 280ms ease-out, staggered by 20-30ms per card). Respects `prefers-reduced-motion`. Calculator panel scales in from 92% with fade. FAB scales on hover/active. Auto-filled values flash on update.

## Browser Surfaces

- Selection: themed (`--sel` token)
- Caret: themed (`--caret` token)
- Scrollbar: themed (`--sb` token on thumb, `--bg` on track)
- Focus: 2px solid `--focus-c` with offset, inputs get box-shadow instead

## Component Architecture

Single-file HTML with all CSS and JS inline. No build step. Components:

- **App bar**: sticky, dark header with title, theme toggle, and clear button
- **Navigation**: tab-style with active underline; sub-navigation for normal cost variants
- **T-account cards**: header + two-column body (debit/credit), input rows, auto-sum totals with double-rule border
- **Calculator**: fixed panel with expression display, keypad grid, and insert-to-field button
- **Toolbar**: centered row of text buttons (save, load, CSV, print, terminology)
- **Save dialog**: centered modal overlay
- **Drawers**: right-sliding panels for saved entries list and terminology reference
- **FAB**: fixed bottom-right, hides when calculator opens

## Service Worker

Cache version: `cost-v4`. Cache-first for app assets, network-first for Google Fonts.
