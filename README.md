# shopify-custom-theme

Shopify OS 2.0 custom theme with JSON templates, dynamic sections, metafield support, schema-driven settings, responsive product grid, hero banner, featured collection, product page with variant selector, sticky header with mega menu, newsletter footer, and structured data (JSON-LD).

## Theme Sections
- **Header** — Sticky, logo, navigation with dropdowns, cart count, mobile menu
- **Hero Banner** — Full-width with image, overlay, heading, CTA button, alignment options
- **Featured Collection** — Configurable grid (2-4 columns), product count, view-all button
- **Product Main** — Image gallery, variant selector, quantity, metafield blocks, add to cart
- **Footer** — Multi-column: menus, text blocks, newsletter signup

## OS 2.0 Features
- JSON templates with section ordering
- Section schemas with typed settings (image_picker, color, range, font_picker, etc.)
- Metafield rendering via configurable blocks
- Reusable snippets (product-card, icons)
- Theme settings: colors, typography with font picker
- Structured data (JSON-LD) for products

## Setup
```bash
git clone https://github.com/Shaisolaris/shopify-custom-theme.git
cd shopify-custom-theme
shopify theme dev --store=your-store.myshopify.com
```

## License
MIT
