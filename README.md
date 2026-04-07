# shopify-custom-theme

> **Preview:** Install [Shopify CLI](https://shopify.dev/docs/themes/tools/cli), then run `shopify theme dev --store=your-store.myshopify.com`. The theme renders with all sections visible in the theme editor.


![CI](https://github.com/Shaisolaris/shopify-custom-theme/actions/workflows/ci.yml/badge.svg)



Shopify OS 2.0 custom theme with 5 dynamic sections, JSON templates, schema-driven settings, metafield blocks, and responsive product grid.

## Quick Start

```bash
git clone https://github.com/Shaisolaris/shopify-custom-theme.git
cd shopify-custom-theme
shopify theme dev --store=your-store.myshopify.com
```

Shopify OS 2.0 custom theme with JSON templates, dynamic sections with schema-driven settings, metafield support via configurable blocks, responsive product grid, hero banner with overlay controls, featured collection with column settings, product page with variant selector, sticky header with navigation, newsletter footer, and theme-level color/typography settings with font picker.

## Stack

- **Platform:** Shopify OS 2.0
- **Templates:** JSON-based with section ordering
- **Sections:** Dynamic with typed schema settings
- **Styling:** CSS custom properties from theme settings

## Sections

### Header (`sections/header.liquid`)
- Sticky positioning, logo with image picker
- Navigation from menu link list
- Cart count badge, mobile menu toggle
- Configurable background and text colors

### Hero Banner (`sections/hero-banner.liquid`)
- Full-width background image with overlay opacity control (0-100%)
- Heading with configurable font size (24-72px)
- Text alignment (left/center), rich text body
- CTA button with primary/secondary/outline styles
- Preset available for drag-and-drop in theme editor

### Featured Collection (`sections/featured-collection.liquid`)
- Collection picker from Shopify admin
- Configurable product count (2-12) and columns (2-4)
- Show/hide vendor names
- "View All" button toggle
- Responsive grid (collapses to 2 columns on mobile)

### Product Main (`sections/product-main.liquid`)
- Image gallery for all product images
- Variant selector dropdown with price and availability
- Quantity input with add-to-cart form
- Sold out state handling (disabled button)
- Description rendered as rich text
- Metafield blocks: configurable namespace/key/label for displaying product metafields

### Footer (`sections/footer.liquid`)
- Block-based: add menu columns or newsletter signup
- Menu blocks with link list picker
- Newsletter block with Shopify customer form
- Copyright with dynamic year
- Responsive multi-column grid

## Snippets

- **product-card.liquid** — Reusable product card with image, sale/sold-out badges, compare-at pricing, vendor display, hover image swap

## Theme Settings (`config/settings_schema.json`)

| Setting | Type | Description |
|---|---|---|
| Primary color | color | Main brand color |
| Secondary color | color | Accent / sale color |
| Heading font | font_picker | Typography for headings |
| Body font | font_picker | Typography for body text |

## Templates

- `templates/index.json` — Homepage: Hero Banner → Featured Collection
- `templates/product.liquid` — Product Main → Featured Collection

## Architecture

```
shopify-custom-theme/
├── layout/theme.liquid                    # Base HTML, head tags, header/footer sections
├── sections/
│   ├── header.liquid                      # Sticky nav, logo, cart, mobile menu
│   ├── hero-banner.liquid                 # Full-width hero with overlay + CTA
│   ├── featured-collection.liquid         # Product grid from collection
│   ├── product-main.liquid                # PDP: gallery, variants, add to cart, metafields
│   └── footer.liquid                      # Block-based: menus + newsletter
├── snippets/product-card.liquid           # Reusable product card component
├── templates/
│   ├── index.json                         # Homepage section ordering
│   └── product.liquid                     # Product page sections
├── assets/
│   ├── theme.css                          # Full stylesheet with CSS custom properties
│   └── theme.js                           # Mobile menu toggle
├── config/settings_schema.json            # Theme-level colors + typography
└── locales/en.default.json                # i18n strings
```

## Setup

```bash
git clone https://github.com/Shaisolaris/shopify-custom-theme.git
cd shopify-custom-theme
shopify theme dev --store=your-store.myshopify.com
```

## Key Design Decisions

**JSON templates for section ordering.** The homepage uses `index.json` which defines which sections appear and in what order. Store owners can rearrange, add, and remove sections via the theme editor without touching code.

**Schema-driven settings.** Every section declares its settings via `{% schema %}` JSON blocks. This generates the sidebar controls in the Shopify theme editor: color pickers, range sliders, image pickers, collection selectors, and font pickers.

**Metafield blocks on product page.** Instead of hard-coding metafield access, the product section uses configurable blocks where the store owner specifies the namespace, key, and display label. This makes metafield display reusable across different product types without code changes.

**CSS custom properties from settings.** Theme colors and fonts are set via Liquid in the CSS file (`:root { --primary: {{ settings.color_primary }}; }`). This gives store owners live preview of color/font changes in the editor while keeping CSS maintainable.

**Responsive grid with CSS Grid.** Product grids use `grid-template-columns: repeat(N, 1fr)` with a media query breakpoint at 768px. The column count is controlled by the section schema, so no CSS changes are needed when the store owner adjusts layout.

## License

MIT
