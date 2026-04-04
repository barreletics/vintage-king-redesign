# Vintage King prototype — copy, typography & condition-badge spec

**Official name:** VK Prototype Copy, Typography & Badge Spec (say **“type & badge spec”** in meetings).  
**Browser:** `VK-Prototype-Copy-Typography-Badge-Spec.html` · **Last aligned:** April 2026  

This spec covers **type**, **bold/caps**, **tokens**, and **product badges**. There are **two badge treatments** in play:

| Context | File | Style |
|--------|------|--------|
| **10-page desktop prototype grids** | `VintageKing-Redesign-v2_67-Mar2026.html` | **Filled** pills (`.grid-badge`) |
| **Mic category + filters (lab)** | `mega-menu/VK-Microphones-CategoryDemo-v4-refined.html` | **Outline** tags (`.pcard-badge`) |

Do not assume one matches the other—pick per surface until design locks a single system.

---

## Font stacks

| Role | Family | Weights | Notes |
|------|--------|---------|--------|
| **UI / body** | **Roboto**, system-ui, sans-serif | 400, 500, 600, 700 | Navigation, filters, chips, forms, buyer cards (titles), pricing numerals. |
| **Display / editorial** | **Playfair Display**, Georgia, serif | 400, 500 | Category **H1**, **product names** on PLP cards, select editorial headings (e.g. expert module headline). |

**Loading:** Both load from Google Fonts with `display=swap`. `preconnect` to `fonts.googleapis.com` and `fonts.gstatic.com`. Fallbacks (Georgia / system-ui) apply until files arrive—brief FOUT is expected, not broken text.

**H1 “Microphones”:** Prefer **Playfair** for brand/editorial consistency with product names. Optional team variant: **Roboto 600** for a fully sans PLP—document the decision and apply globally if chosen.

---

## When to use **bold**

| Use bold | Do not bold |
|----------|-------------|
| **Strong** in long SEO / crawl copy where you need one emphasis term (e.g. **All filters**). | Full sentences or repeated keywords (hurts scan, looks shouty). |
| Card eyebrow labels are **700** in CSS (buyer guides)—not body `<strong>`. | Inventory line: use **600** on keywords via styled `<span>`, not every word. |
| Filter drawer: checked row label **600** (color + weight). | Unchecked checklist labels—regular **400**. |
| Price “now” stays **500**; strike “was” **400**. | Brand line under product name—**400**, grey. |

---

## When to use ALL CAPS

Use **uppercase + letter-spacing** only for **labels**, not sentences.

| Pattern | Example |
|---------|---------|
| Eyebrow / kicker (11px, ~0.12–0.16em tracking) | `Recording / live / broadcast` |
| Section headers in drawer (`<summary>`) | `Brand`, `Collection / sub-type` |
| Micro-labels | `Quick refinements`, `All filters` title row |
| PLP **condition badges** | See below—always uppercase in UI |
| Buyer card eyebrows | `Buying guide` |

**Avoid:** All-caps paragraphs, all-caps product titles (titles are Title Case or brand casing).

---

## Core color tokens (prototypes)

| Token | Hex | Usage |
|-------|-----|--------|
| **VK red** | `#C0392B` | Primary CTA, links (active/hover patterns), default **New** badge, focus rings, key editorial emphasis. |
| **Near black** | `#1A1A18` | Primary text, active pill (if used). |
| **Charcoal** | `#2C2C2A` | Body secondary text. |
| **Mid grey** | `#6B6B68` | Meta, breadcrumbs, hints, **Demo** badge (text + border). |
| **Amber** | `#D4860A` | **Used** condition badge (text + border)—signals pre-owned, not error. |
| **Vintage brown** | text `#7c5c20`, border `#9a7340` | **Vintage** badge. |
| **Charcoal (open box)** | `#2C2C2A` | **Open box** outline badge (PLP). |
| **Blue (info)** | `#2563EB` | **Open box** filled pill on desktop grid only. |

Background / structure: `--warm-white` `#FDFCFB`, `--off-white` `#F7F5F2`, `--pale-grey` `#EDEDEA`, `--light-grey` `#D8D6D2`.

---

## Desktop prototype — grid badges (filled)

Source: `VintageKing-Redesign-v2_67-Mar2026.html` · `.grid-badge` · **11px** · **600** · padding `4px 10px`.

| Badge | Class | Treatment |
|-------|--------|-----------|
| **New** | `.grid-badge.new` | Bg `#1A1A18`, text white |
| **Used** | `.grid-badge.used` | Bg `#F5E6C8`, text `#D4860A` |
| **Sale** | `.grid-badge.sale` | Bg `#fde8e6`, text VK red |
| **Open box** | `.grid-badge.openbox` | Bg `#EFF6FF`, text `#2563EB` |

---

## Mic category PLP — condition tags (outline)

Source: `mega-menu/VK-Microphones-CategoryDemo-v4-refined.html` · **9px**, **uppercase**, **~0.14em** tracking, **500**, **1px border**, **2px radius**, **3px 7px** padding.

| Badge | Class (v4) | Text/border color |
|-------|------------|-------------------|
| **New** | `.pcard-badge` | VK red |
| **Used** (e.g. Used — Excellent) | `.pcard-badge--used` | Amber |
| **Vintage** | `.pcard-badge--vintage` | Vintage brown / border per spec |
| **Demo** | `.pcard-badge--demo` | Mid grey |
| **Open box** | `.pcard-badge--open` | Charcoal |

**Copy shape:** Prefer **New**, **Demo**, **Open box**, **Vintage**; used states as **Used — [grade]** (e.g. Mint, Excellent, Good) for clarity.

---

## Pricing line

- **Current price:** 16px, **500**, near black.  
- **Was price:** 13px, **400**, mid grey, strikethrough, 6px gap—**not** bold.

---

## PLP tile CTA

- Label: **Details →** (or **View product** if team prefers maximum clarity).  
- Style: small caps treatment (11px, **600**, ~0.04em tracking), VK red; whole card remains one link.

---

## Filter UI (drawer)

- **Group titles (`summary`):** Uppercase micro-label, **VK red** in v4 for scan alignment with brand thread.  
- **Visible checkboxes** + **accent-color** VK red.  
- **Selected row:** Red + **600** weight—not underline-only in v4.

---

## Changelog idea

When the production theme changes, update this file and the reference HTML in one pass.
