# Mobile prototype — parity with desktop (source of truth)

This document is the **single place** to align the mobile HTML prototype with the **desktop demos**. Update it when desktop versions bump or when mobile parity milestones are completed.

---

## 1. Source of truth (desktop)

| Role | File (canonical) | Notes |
|------|------------------|--------|
| **Full site / home / messaging / structure** | `VintageKing-Redesign-v2_67-Mar2026.html` | Primary reference for pages, tone, and layout intent. |
| **Mega menu / top-level IA** | `mega-menu/VintageKing-MegaMenu-CursorLab-v2.html` | Nav hierarchy and mega behavior → maps to mobile drawer or hub. |
| **Category PLP — filters, two rows, facets** | `mega-menu/VK-Microphones-CategoryDemo-v4-refined.html` | Collections + quick refinements + See more → full filters. |
| **Demo hub / links** | `VK-Prototype-Index.html` | Entry point for demos. |

**Taxonomy** (labels, facet order, SEO vs filter-only rules) should match your spreadsheet / written policy — **one taxonomy** for desktop and mobile; do not invent a second tree on mobile.

---

## 2. Mobile prototype (implementation target)

| Item | Value |
|------|--------|
| **File** | `VintageKing-MobileSimulator-v1_9-Apr2026.html` |
| **In-page version** | **v1.9** (title + footer; April 2026 full parity build) |
| **What it is** | Static simulator (phone chrome + in-phone pages). Not production Shopify. |

**Open locally:** paste in the browser address bar:

`file:///Users/andrewnehra/Alternate-projects/vintage-king-redesign/VintageKing-MobileSimulator-v1_9-Apr2026.html`

or run: `open "/Users/andrewnehra/Alternate-projects/vintage-king-redesign/VintageKing-MobileSimulator-v1_9-Apr2026.html"`

---

## 3. How to work (recommended)

| Mode | Use for |
|------|--------|
| **Cursor (this repo)** | Implementing and iterating the mobile HTML/CSS/JS, keeping parity with the desktop files above. |
| **Claude (or similar)** | Optional: copy polish, stakeholder narrative, critique of flows — **not** the canonical prototype location. |

**Process:** Desktop = spec. Mobile = narrow presentation (drawers, sheets, thumb-friendly targets) of the **same** IA, messaging hierarchy, and filter groups.

**Firewall (Cursor):** For mobile parity, desktop HTML is **read-only** — no edits, formatting passes, or **git revert/restore/checkout** on desktop paths to “fix” mobile work unless you **explicitly** ask for a desktop change. Implement only in `VintageKing-MobileSimulator*.html` and this doc. Rules: `vk-mobile-parity`, `vk-desktop-prototype-readonly`, and (in this repo) **`vk-mobile-desktop-firewall-always`** (always-on when the workspace root is `vintage-king-redesign`). If you use a parent folder as the workspace, rely on the first two rules when mobile or desktop files are open.

---

## 4. Parity checklist (fill as you go)

Use this to track what’s done vs still borrowed or simplified. Add rows for any desktop section that matters for launch.

| Area | Desktop reference (section / behavior) | Mobile equivalent (component / state) | Status |
|------|----------------------------------------|----------------------------------------|--------|
| Home | v2.67 hero, messaging, key modules | In-phone home page | ✅ |
| Global nav / IA | Mega v2 structure | Hamburger → drawer or hub | ✅ |
| Category PLP | v4 refined: row 1 + row 2 + See more | Same pattern + filter drawer | ✅ |
| Filters / taxonomy | Facet groups + labels | Drawer sections + chips (match taxonomy) | ✅ |
| PDP | v2.67 product template | In-phone product page | ✅ |
| Support / FAQ / static | As in v2.67 | Matching pages in simulator | ✅ |
| Footer / trust | v2.67 | Mobile footer | ✅ |

*Replace ☐ with ✅ when verified against desktop.*

---

## 5. Suggested next milestones (order)

1. **Nav + taxonomy entry** — Mobile drawer or hub reflects mega v2 L1/L2 (labels from taxonomy).  
2. **Home** — Align modules and hero messaging with v2.67 mobile intent.  
3. **PLP** — Full parity with v4 refined (already partially started: two rows, drawer, Pills/Inline).  
4. **PDP + remaining pages** — Match v2.67 structure and copy hierarchy.  
5. **Rename / version** — Bump filename (e.g. `…-v1_9-…`) when you cut a stable client handoff.

---

## 6. Progress at a glance (update when something ships)

Use this table for **where we are** in plain terms. When a milestone is done enough to show, set **Status** to **Done** and add a short **Notes** line (optional).

| # | Milestone | Status | Notes |
|---|-----------|--------|-------|
| 1 | Nav + taxonomy (menu matches mega v2, one taxonomy) | Done | L1 order fixed (Mics, Outboard, Consoles, Vintage and Used, Studio Design, Monitoring, Deals). L2 labels aligned to mega v2 across all six accordions. |
| 2 | Home (hero + key modules vs desktop) | Done | Hero eyebrow aligned. Category tiles labelled (Outboard & Processing, Consoles & Mixers, Studio Monitoring). "Recently Added" replaced with "The Short List" (4 tabs: New/Used/Open Box/Vintage). "Explore Used" CTA added. "Vintage and Used" label used throughout home. |
| 3 | Category listing + filters (v4 refined pattern on phone) | Done | Row 1: chips aligned (All, Condenser, Dynamic, Ribbon, Tube, USB/digital, Lavalier and headset, Vintage and collectible). Row 2: chips aligned (Under $500, Under $1,000, New, Used, Open box, Vintage, On sale, In stock only). Filter drawer expanded to 8 facet groups matching v4: Collection/sub-type, Price, Condition and listing, Brand, Availability and fulfillment, Polar pattern, Application, Deals. |
| 4 | Product page + other static pages | Done | PDP: short description, condition labels (dash), spec fixes, description tab copy, financing link. FAQ: intl shipping Q, Live Chat card, section titles. Footer: "Pro Audio Outfitter" tagline, expanded Shop + Help columns. |
| 5 | Version bump / file rename for handoff | Done | In-page version bumped to v1.9. File copied to VintageKing-MobileSimulator-v1_9-Apr2026.html. All §4 checklist rows ✅. MOBILE-PARITY.md filename and version updated. |

**Cursor:** project rule `vk-mobile-parity` and skill `vk-mobile-parity` align agent behavior with this doc and desktop `CLAUDE.md` rules.

---

## 7. When desktop bumps

- Update §1 table with new filenames (e.g. `v2_68`, `v5-refined`).  
- Re-run §4 parity for changed areas; refresh §6 if milestone scope changed.  
- Bump mobile prototype version in the HTML and optionally rename the file.

---

*Last updated: April 2026 — v1.9 full parity build. All 5 milestones complete. Aligned with desktop v2.67, category v4 refined, and mega v2.*
