# Navigation & mega-menu

The Kettle's Yard-style mega-menu (colour block + featured photo + link list) is now
fully automatic — driven entirely by the order of links already set up in each
category's dropdown in Shopify's Navigation menu editor. There's no separate
configuration step in the theme customizer anymore.

For every top-level menu item that has sub-links, the dropdown renders as:

- **Colour block** (brand green, leftmost) — the top-level item's own title, linking
  to wherever that top-level item points.
- **Photo tile** — automatically uses the **first** sub-link in that category. If the
  first sub-link points to a collection or product, its image and title are pulled in
  directly (so make sure that collection/product has a good image set).
- **Plain link list** — every other sub-link, in the order they're listed.
- **"View all" CTA** — the **last** sub-link in that category is pulled out and
  styled distinctly (bold, bottom-right, divider above it), rather than blending into
  the plain list.

So the only thing that needs maintaining is the order of links within each category in
Content → Navigation — put the lead subcategory first, everything else in the middle,
and the "shop all" link last. No handles, no block setup, nothing theme-side to touch
when collections change.

If a top-level item's first or last link points somewhere without an image (e.g. a
plain page or an external URL), the photo tile just renders without an image — nothing
breaks.
