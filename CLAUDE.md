# CLAUDE.md — Vintage King Redesign Handoff

## READ THIS FIRST
This file is the complete briefing for every new Claude agent on this project. Read it fully before touching any file. Working file is v2.65. Never go back to earlier versions.

---

## Project Overview
Vintage King Audio (VK) website redesign and Shopify Plus migration prototype. AJ (Barreletics Ops) is design and strategy lead. Single HTML prototype file, 10 pages, hosted on GitHub Pages.

**Current file:** VintageKing-Redesign-v2_65-Mar2026.html
**Live preview:** https://barreletics.github.io/vintage-king-redesign

---

## Design System (LOCKED)
- Display font: Playfair Display — headings, product names, large stats only
- - Body font: DM Sans — all body copy, labels, buttons, pricing
  - - PRICING RULE: DM Sans ONLY, font-weight:500, color:var(--near-black). Never Playfair on numbers.
    - - --vk-red: #C0392B — primary CTA, eyebrow accents on ecommerce pages
      - - --near-black: #1A1A18 — primary text
        - - --amber: #D4860A — Vintage/Used ONLY. Never use on new gear.
          - - --warm-white: #FDFCFB — primary background
            - - --off-white: #F7F5F2 — section backgrounds
              - - --amber-bg: #F5E6C8 — credential bars, info boxes
                - - --secondary-accent: var(--vk-red) — global toggle for all secondary pages
                  - - Blue #2563EB / #EEF4FF — informational elements only (Open Box badge, buyer guide)
                    - - CB2.com is the foundational design reference: one message per zone, white space as a feature
                      - - Minimum font size: 12px everywhere. Nothing below 12px.
                       
                        - ---

                        ## Page Inventory
                        Page switcher order — all share one HTML file, toggled by JS:
                        1. Homepage (#home) — lines 2444–3052
                        2. 2. Category (#category) — lines 3053–3335
                           3. 3. Product (#product) — lines 3336–3498
                              4. 4. FAQ (#faq) — lines 3499–3670
                                 5. 5. Demo Deals (#deals) — lines 3671–4095
                                    6. 6. Sell or Trade (#sell) — lines 4096–4727
                                       7. 7. Studio Installations (#studio) — lines 5084–5456
                                          8. 8. Tech Shop (#techshop) — lines 4728–5083
                                             9. 9. Financing (#fin-page) — lines 5459–5718
                                                10. 10. Open Box (#openbox) — lines 5719–6198
                                                   
                                                    11. ---
                                                   
                                                    12. ## Build Queue — Next Agent (priority order)
                                                   
                                                    13. ### 1. NAV REFINEMENT (start here)
                                                    14. The navigation needs to match CB2/Apple standard — currently too small and tight.
                                                    15. - Logo wordmark "VINTAGE KING" — CSS class .logo-text .name — currently 14px. Too small. Increase.
                                                        - - Logo icon (SVG mark) — also too small. Scale up proportionally.
                                                          - - Nav overall font feels tight — review .nav-link, .topbar font sizes
                                                            - - "Pro Audio Outfitter" tagline (.logo-text .tagline) — LOCKED. Do not remove. Currently 12px.
                                                              - - Mega menu column headers already bumped to 12px in v2.65 — do not touch
                                                                - - Ask mode before touching nav CSS. Show dry-run diff before applying.
                                                                 
                                                                  - ### 2. TYPE SPEC SHEET
                                                                  - Build as 11th tab in the prototype page switcher. Must be extremely clear for agency handoff.
                                                                  - Contains: full typography scale (H1–body–micro), when to use red vs amber vs near-black vs grey, minimum sizes, font weights, pricing rules, eyebrow rules, badge rules.
                                                                 
                                                                  - ### 3. TAXONOMY + FILTER DEMO (heavy lift — own session)
                                                                  - AJ has the VK taxonomy file (will upload). Also review live vintageking.com taxonomy.
                                                                  - Build a filter demo page showing: collapsed/expanded filter panel, complex category hierarchies, multiple filter states. This is the most technically complex remaining page. The taxonomy is deep — allocate a full session.
                                                                 
                                                                  - ### 4. EDITORIAL HERO BLOCK — Category + Demo Deals
                                                                  - Add toggle to both pages: Standard / With Editorial Hero.
                                                                  - Pattern already proven on Open Box page. 2x2 dark photo grid + full-bleed interruption of product grid. Reuse Open Box pattern exactly.
                                                                 
                                                                  - ### 5. VK-DesignDecisions-Mar2026.md
                                                                  - Update with all decisions made across sessions. Log with rationale.
                                                                 
                                                                  - ### 6. AGENCY BRIEF ADDITIONS
                                                                  - - Load More pattern requires static paginated URLs for crawler indexing
                                                                    - - Secondary pages amber/red CTA toggle decision
                                                                      - - 70,000 redirects — manageable in native Shopify
                                                                       
                                                                        - ### 7. MOBILE PASS
                                                                        - Only after all desktop pages complete and approved.
                                                                       
                                                                        - ---

                                                                        ## Font Patch Script
                                                                        File: patch_fonts.py (in repo root — must be copied to working directory)
                                                                        ALWAYS dry-run first. ALWAYS write to new file. NEVER apply without reviewing diff.

                                                                        Usage:
                                                                          python3 patch_fonts.py file.html --start N --end N --dry-run
                                                                          python3 patch_fonts.py file.html --start N --end N --apply
                                                                          python3 patch_fonts.py file.html --css-pass --dry-run
                                                                          python3 patch_fonts.py file.html --css-pass --apply

                                                                        Tiers:
                                                                          8px/9px → 11px (inline HTML, span/a/em tags only)
                                                                          10px → 12px (requires uppercase + letter-spacing on same line)
                                                                          11px → 13px (requires uppercase + letter-spacing on same line)

                                                                        Skips: <style> block, <svg> elements, color:#999 footnotes, badge patterns

                                                                        ---

                                                                        ## Mandatory Rules (never break)
                                                                        - Never revert or overwrite completed work
                                                                        - - Never use HTML entities (&amp; etc.) in visible UI text
                                                                          - - Never use Playfair Display on prices or numbers
                                                                            - - Amber (#D4860A) reserved for Vintage/Used ONLY
                                                                              - - Form field focus borders always var(--vk-red) regardless of secondary-accent toggle
                                                                                - - Stats block numbers are conversion tools — do not alter
                                                                                  - - "Pro Audio Outfitter" is locked nav tagline — never remove
                                                                                    - - "VK Warranty" throughout — never "Full Warranty"
                                                                                      - - Desktop-first — no mobile pass until all desktop complete
                                                                                        - - Ask mode before building anything new
                                                                                          - - Surgical, precise changes only — use patch script for font changes
                                                                                            - - New version file for every change (v2.65 → v2.66 etc.)
                                                                                              - - Download current version before starting any session
                                                                                               
                                                                                                - ---

                                                                                                ## Agency Context
                                                                                                - Finalists: Hammer (knows VK stack) and Domaine (lower cost, SEO resources)
                                                                                                - - Iamota: eliminated — proprietary theme, no Cursor/GitHub compatibility
                                                                                                  - - Deployment: Cursor AI → Shopify Plus (headed, NOT headless)
                                                                                                    - - Headless Shopify: avoid — breaks app integrations, adds SEO complexity
                                                                                                      - - 70,000 redirects: fully manageable in native headed Shopify
                                                                                                        - - Horizon and Slab (Brickspace Lab) confirmed as non-headless GitHub/Cursor compatible themes
                                                                                                         
                                                                                                          - ---
                                                                                                          
                                                                                                          ## VK Team Open Items
                                                                                                          - Real photography: all secondary pages and Open Box (VK photographer)
                                                                                                          - - Section 179 figures: 2025 currently — update annually
                                                                                                            - - Real seller quote attribution on Sell or Trade
                                                                                                             
                                                                                                              - ---
                                                                                                              
                                                                                                              ## Key Design Decisions (locked)
                                                                                                              - "The Short List" — tabbed product section name on homepage
                                                                                                              - - "Rare Gear" — visible H2 on homepage Vintage section
                                                                                                                - - Open Box excluded from mega-menu (Sweetwater/B&H benchmark)
                                                                                                                  - - Buyer's guide card: between filter bar and product grid
                                                                                                                    - - Mega-menu Ask button hover dropdown: Live Chat / Callback / Video Chat
                                                                                                                      - - Co-op blocks stay inline with Talk to an Expert CTA — never separated
                                                                                                                        - - Navigation = conversion tool, not sitemap. Six parent categories max.
                                                                                                                          - - All Categories CMS page + OPO pre-footer = crawl and GEO solution
                                                                                                                            - - Load More chosen for UX — static paginated URLs must exist for crawlers
                                                                                                                              - - VK Integrations consolidated into main site via utility bar + Studio Design dropdown
                                                                                                                               
                                                                                                                                - ---
                                                                                                                                
                                                                                                                                ## What Was Completed (full version history)
                                                                                                                                - v1.98: mega menu, homepage, category, product, FAQ, demo deals, footer
                                                                                                                                - - v2.17–v2.34: Sell or Trade page complete (3-way header toggle, credential bar, form)
                                                                                                                                  - - v2.35–v2.50: Studio Installations, Tech Shop, global amber/red toggle system
                                                                                                                                    - - v2.41–v2.45: Financing page (Section 179, Trade Program tabs)
                                                                                                                                      - - v2.51–v2.61: Open Box complete — editorial 2x2, product grid, buyer strip, ghost CTAs
                                                                                                                                        - - v2.64: Studio Installations project cards rebuilt (dark caption, white text, red CTA)
                                                                                                                                          - - v2.65: Global font pass — nothing below 12px anywhere in CSS or inline styles
