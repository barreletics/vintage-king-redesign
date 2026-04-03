# Vintage King Redesign — Session Notes
**Date:** April 3–4, 2026
**Sessions:** 1.8 + 1.9
**Working file:** v2.67 | Live on GitHub Pages: v2.61

---

## File Inventory — GitHub Repo

| File | Purpose | Status |
|---|---|---|
| `VintageKing-Redesign-v2_67-Mar2026.html` | Main prototype — current working file | Current |
| `VintageKing-Redesign-v2_61-Mar2026.html` | Live on GitHub Pages | Live |
| `VK-Microphones-CategoryDemo-v1.html` | Standalone microphones category + filter demo | Fixed |
| `VK-FilterDemo-v1.html` | Old broken version — ignore/delete | Deprecated |
| `VK-Taxonomy-Mar2026.xlsx` | VK Magento taxonomy export (3 tabs) | Upload needed |
| `VK-SessionNotes-Apr2026.md` | This file | Current |
| `CLAUDE.md` | Project brief for new agents | Current |
| `VK-RedesignBrief-Mar2026.docx` | Agency brief | Current |

CLAUDE.md correction: Nav tagline is "New · Used · Vintage · Pro Audio" — NOT "Pro Audio Outfitter" (footer only). Two lines in CLAUDE.md incorrectly reference "Pro Audio Outfitter" as nav tagline — ignore those lines.

---

## Changes This Session

### v2.66 — Nav Refinement
| Element | Before | After |
|---|---|---|
| Nav height | 72px | 80px |
| Logo SVG tube | 22x36px | 28x44px |
| Wordmark .logo-text .name | 14px | 17px |
| Nav link padding | 5px | 14px |
| Nav link font | 13px | 14px |
| Tagline | 12px | 12px (locked) |

### v2.67 — itile Fix
- `.itile-img` — added `background: var(--near-black)` fallback so co-op tile image zones don't show transparent over hero content

### VK-Microphones-CategoryDemo-v1.html
- Standalone microphones category page demo — separate file, separate naming from prototype
- Correct nav extracted from `<template id="nav-template">` (not raw HTML — previous versions used wrong extraction causing all 10 page content to bleed into DOM)
- No injectShared, no page bleed, no SOT form, no studio lightbox
- Hamburger button removed
- Full left filter panel: Type (7), Brand (9), Price (4 tiers + custom range), Condition toggle, Availability
- Active filter chips above grid, clearable individually or all-at-once
- 12 product cards ($99 to $18,900 price mix)
- Badge system: Top Seller (black), New (red), Used (amber), For Beginners (blue)
- Buyer B amber strip — "New to microphones? Mic Buying Guide"
- Talk to a Mic Expert sidebar CTA with live dot indicator
- Working mega menu via setupNav()

---

## Nav Architecture Decision

DECISION: Keep product type at top level. Do not add "Recording" as a nav parent.

### Competitive Benchmark

| Site | Nav Approach | Verdict for VK |
|---|---|---|
| Sweetwater | Shop By Category mega dropdown, rest = editorial | Buries nav. Conversion engine is 12,000 sales reps. Cannot replicate. |
| B&H Photo | Department parents: Photography, Pro Video, Pro Audio, Lighting, Used | "Pro Audio" works for B&H because customers arrive from photography/video. VK customers don't need department wayfinding. |
| CB2 | Product category parents, heavy whitespace, editorial image in mega | Best design reference for VK. One message per zone. |
| REI | Activity-based: Camp & Hike, Climb, Cycle | Wrong model. VK customers self-identify by product type, not activity. |
| VK Prototype | Product type: Microphones, Outboard, Consoles, Vintage & Used, Studio Design, Monitoring, Deals | Correct. Fast for expert buyer. |

Rationale: VK customers arrive already in pro audio mindset. "Recording" describes the entire store, not a section. B&H uses "Pro Audio" as a parent because their customers come from photography and video — VK has no such cross-department traffic. Product type at top = one click to product.

What the team's "Recording" instinct actually solves: better mega menu depth and taxonomy organization — a filter and taxonomy problem, not a nav label problem.

---

## Customer Model — Dual Buyer Strategy

### Buyer A — The Pro (Core)
- Studio engineer, producer, working musician
- Knows exactly what they want — navigates by product type in one click
- Price-insensitive on the right gear, high AOV, repeat buyer
- Currently well-served by VK prototype nav

### Buyer B — Entry Level (Growth Target)
- Aspiring producer, home studio builder, first serious gear purchase
- Needs guidance, price-sensitive, comparison shopper
- Sweetwater's volume base — VK wants to grow this segment via ecom
- Capture online, grow into high-touch sales team purchases over time
- Currently underserved

### Solution: Two-Track Without Rebuilding Nav
Top nav stays as product type. Mega menu adds Buyer B entry points:
- Resources column: "New to home recording? Start here" buying guide link
- Price column: "Under $500" as first price tier
- "Talk to an Expert" CTA in mega menu bridges Buyer B into sales team
- "For Beginners" badge on entry-level product cards in category pages

This is the Sweetwater flywheel: capture online, convert via human relationship. VK advantage: curation and taste that Sweetwater doesn't have.

---

## Taxonomy Research — VK-Taxonomy-Mar2026.xlsx

### Three Tabs Summary

Tab 1 — FROM MAG (846 rows): Full Magento category export. Active and inactive. Full URL paths.

Active parent categories:
- /recording — highest traffic, highest engagement. Priority for filter demo.
- /instruments — active, team debating scope
- /live-sound-dj — active
- /software — active
- /used-and-vintage — active, key differentiator
- /sale — active
- /features — active (editorial/promo use)
- /ams-neve — brand-specific landing page

Kill / inactive categories:
- /immersive — entire subtree flagged for kill
- /furnishings, /post, /new-arrivals, /servicing — inactive
- /listing-on-hold, /listing-qa, /listing-queue-brandon, /listing-queue-paul — internal workflow, must not migrate to Shopify

Tab 2 — Category Cleanup Suggestions (497 rows): Kill/Merge flags. Active cleanup for Shopify Plus migration. Major kill candidates:
- Entire /immersive subtree (7 sub-categories)
- /instruments/drums sub-categories (Cymbals, Drum Heads, Drum Kits, Snare Drums)
- /instruments/guitar-bass-amps sub-categories
- Various modular synth sub-sub-categories

Tab 3 — Mega Menu Thoughts: Team proposed 7 nav headers: Recording, Instruments, Software, Live Sound & DJ, Deals, New Releases, Used & Vintage. Assessment: Too broad. Instruments and Software indicate expansion beyond core pro audio — needs strategic decision before building into nav.

### Priority Category — /recording/microphones
Highest traffic, highest engagement per VK team direction.

Sub-categories confirmed on live vintageking.com:
Large Diaphragm Condensers, Small Diaphragm Condensers, Dynamic Microphones, Ribbon Microphones, Modeling Microphones, Digital Microphones, USB Microphones, Shotgun Microphones, Lavalier/Clip-on, Headset, Pressure Zone (PZM), Accessories (Cables, Stands, Shock Mounts, Pop Filters, Cases), Used + Vintage Microphones, Microphone Bundles, Best Selling Microphones

---

## Delivery Path — For Cursor + Agency

This prototype is a spec and decision tool, not production code.

Flow: Claude (prototype + decisions) → GitHub → Cursor (Shopify theme build) → Agency review → Shopify Plus

- Main prototype (v2.67) = design spec for agency
- Category demo = UX pattern spec for filter/category page
- Taxonomy xlsx = migration input for Shopify category structure
- Session notes = decision log and agency brief supplement

Agency options: Hammer (knows VK stack) or Domaine (lower cost, SEO resources). Iamota eliminated.
Shopify deployment: headed (NOT headless). Horizon or Slab (Brickspace Lab) are confirmed themes.

---

## Open Questions for Team

1. Instruments and Software in nav: Actively expanding beyond core pro audio, or aspirational? Changes nav item count.
2. "Learn" in primary nav: Recommend moving to topbar utility row to keep primary nav clean and under 7 items.
3. Entry-level price floor: Does VK have a defined range to target (e.g. $99-$500)? Informs filter structure for Buyer B.
4. Taxonomy cleanup sign-off: Tab 2 kill/merge list needs VK team approval before Shopify migration.
5. itile images: Co-op tile image blocks need real photography from VK photographer before launch.

---

## Task Queue

| # | Task | Status |
|---|---|---|
| 1 | Nav Refinement | Done (v2.66) |
| 2 | itile-bg transparent fix | Done (v2.67) |
| 3 | Microphones Category Demo | Done (VK-Microphones-CategoryDemo-v1.html) |
| 4 | Type Spec Sheet (Tab 11 in prototype) | Queued |
| 5 | Editorial Hero toggle — Category + Demo Deals | Queued |
| 6 | Full taxonomy map — all categories doc | Queued |
| 7 | Update CLAUDE.md working file to v2.67 | Queued |
| 8 | Agency Brief additions | Queued |
| 9 | Mobile pass | After all desktop complete |

---

## Mandatory Rules (carry forward)
- Working file: v2.67. Never go back.
- Nav tagline: "New · Used · Vintage · Pro Audio" — not "Pro Audio Outfitter" (footer only)
- Amber (#D4860A): Vintage/Used ONLY
- Playfair Display: headings only, never on prices
- Ask mode before building anything new
- New version number every change
- Desktop-first
- Category demo files named separately from prototype versioning (VK-[Category]-CategoryDemo-v[N].html)
