# CLAUDE.md — Vintage King Redesign Handoff

## Project Overview
Vintage King Audio (VK) website redesign and Shopify Plus migration prototype. AJ (Barreletics Ops) is design and strategy lead. This file briefs every new Claude agent on the full project state.

## Current File
**VintageKing-Redesign-v2_65-Mar2026.html** — working prototype, 10 pages, single HTML file.
Live preview: https://barreletics.github.io/vintage-king-redesign

## Design System (LOCKED — never change without explicit instruction)
- **Display font:** Playfair Display (headings, product names, large stats)
- **Body font:** DM Sans (all body copy, labels, buttons, pricing)
- **Pricing rule:** DM Sans ONLY, font-weight:500, color:var(--near-black). Never Playfair on prices.
- `--vk-red: #C0392B` — primary CTA, eyebrow accents on ecommerce pages
- `--near-black: #1A1A18` — primary text
- `--amber: #D4860A` — Vintage/Used ONLY. Never use on new gear.
- `--warm-white: #FDFCFB` — primary background
- `--off-white: #F7F5F2` — section backgrounds
- `--amber-bg: #F5E6C8` — credential bars, info boxes
- `--secondary-accent: var(--vk-red)` — global toggle for all secondary pages (red/amber)
- Blue #2563EB / #EEF4FF — informational elements only
- CB2.com is the foundational design reference: one message per zone, white space as a feature

## Page Inventory (page switcher order)
1. Homepage (`#home`)
2. Category (`#category`) — lines 3053–3335
3. Product (`#product`) — lines 3336–3498
4. FAQ (`#faq`) — lines 3499–3670
5. Demo Deals (`#deals`) — lines 3671–4095
6. Sell or Trade (`#sell`) — lines 4096–4727
7. Studio Installations (`#studio`) — lines 5084–5456
8. Tech Shop (`#techshop`) — lines 4728–5083
9. Financing (`#fin-page`) — lines 5459–5718
10. Open Box (`#openbox`) — lines 5719–6198

## Completed Work
- All 10 pages built and functional
- Global amber/red CTA toggle (`--secondary-accent`) across all secondary pages
- Global font pass complete: nothing below 12px in CSS or inline styles
- Open Box: editorial 2x2 hero block, product grid, buyer confidence strip, condition guide
- Studio Installations: project cards rebuilt (dark caption strip, white text, red CTA)
- Tech Shop: amber accent, Notable Restorations, Ship/Diagnose/Approve/Return process
- Financing: Section 179 tab, Trade Program tab (2025 figures — update annually)
- Sell or Trade: 3-way header toggle, How It Works, What We Buy, form
- "VK Warranty" throughout — never "Full Warranty"
- Pricing: DM Sans weight:500 near-black everywhere

## Font Patch Script
`patch_fonts.py` — ChatGPT-authored surgical patch tool. Always dry-run first.
Usage:
  python3 patch_fonts.py file.html --start N --end N --dry-run
    python3 patch_fonts.py file.html --start N --end N --apply
      python3 patch_fonts.py file.html --css-pass --dry-run
        python3 patch_fonts.py file.html --css-pass --apply
        Tiers: 8/9px→11px (inline only), 10px→12px (uppercase+letter-spacing), 11px→13px (uppercase+letter-spacing)
        Skips: style block, SVG, color:#999 footnotes, badge patterns

        ## Active Build Queue (priority order)
        1. **Nav refinement** — logo wordmark size, nav font sizing, "Pro Audio Outfitter" tagline — bring to CB2/Apple level
        2. **Type spec sheet** — add as 11th tab in prototype. Typography scale, color rules, usage rules for agency
        3. **Editorial hero block** — add to Category and Demo Deals pages with toggle (Standard / With Editorial Hero)
        4. **Filter demo page** — VK taxonomy file available. Build collapsed/expanded filter panel demo
        5. **CLAUDE.md** — this file (done)
        6. **VK-DesignDecisions-Mar2026.md** — update with all session decisions
        7. **Agency brief additions** — Load More / static URL crawler requirement
        8. **Mobile pass** — after all desktop complete

        ## Immediate Next Task: Nav Refinement
        The nav needs to match CB2/Apple/high-end standard. Issues flagged:
        - Logo wordmark "VINTAGE KING" — currently 14px — too small
        - Nav overall feels small/tight
        - "Pro Audio Outfitter" tagline is locked in design (do not remove)
        - Mega menu labels already bumped to 12px in v2.65

        CSS classes to review: `.logo-text .name` (14px), `.logo-text .tagline` (12px), `.nav-link`, `.topbar`

        ## Mandatory Rules (never break)
        - Never revert or overwrite completed work
        - Never use HTML entities in visible UI text
        - Never use Playfair Display on prices or numbers
        - Amber (#D4860A) reserved for Vintage/Used ONLY
        - Form field focus borders always var(--vk-red) regardless of toggle
        - Stats block numbers are conversion tools — do not alter
        - "Pro Audio Outfitter" is locked nav tagline
        - Desktop-first: no mobile pass until all desktop work complete
        - Ask mode before building anything new
        - Surgical, precise changes only — no global find/replace without patch script

        ## Agency Context
        - **Finalists:** Hammer (knows VK stack) and Domaine (lower cost, SEO resources)
        - **Iamota:** eliminated — proprietary theme
        - **Deployment path:** Cursor AI → Shopify Plus (headed, not headless)
        - **70,000 redirects** — fully manageable in native Shopify
        - **Load More** pattern requires static paginated URLs for crawler indexing (flag in agency brief)

        ## VK Team Open Items
        - Real photography needed: all secondary pages, Open Box
        - Section 179 figures: 2025 currently — update annually
        - Real seller quote attribution on Sell or Trade

        ## Key Design Decisions (locked)
        - "The Short List" — tabbed product section name on homepage
        - "Rare Gear" — visible H2 on homepage Vintage section
        - Open Box excluded from mega-menu
        - Buyer's guide card: between filter bar and product grid
        - Mega-menu Ask button hover: Live Chat / Callback / Video Chat
        - Co-op blocks stay inline with Talk to an Expert — never separated
        - Navigation = conversion tool, not sitemap. Six parent categories max.
        - All Categories CMS page + OPO pre-footer = crawl and GEO solution
