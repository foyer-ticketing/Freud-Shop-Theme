# Navigation & mega-menu setup

This is the setup doc for the new 6-category navigation the client requested, plus the
Kettle's Yard-style mega-menu (colour block + featured photo + link list). Two admin
tasks are involved: building the menu, and configuring which subcategory is "featured"
per top-level item.

## 1. Collections that need to exist first

Several of these are brand-new categories that don't have Shopify collections yet.
Create each one (Products → Collections → Create collection) before building the menu,
so the links below have somewhere real to point. Existing/likely-existing collections
are marked ✅ — confirm their handles are still correct; new ones are marked 🆕.

| Category | Subcategory | Likely status |
|---|---|---|
| Book Your Visit | Admission Tickets | Probably a **product**, not a collection — the museum's ticketing product/page |
| Book Your Visit | Purchase Your Membership | Probably a **product** |
| Book Your Visit | Gift Membership | Probably a **product** |
| Book Your Visit | Admission Gift Vouchers | Probably a **product** |
| Books | Freud Museum Publications | ✅ likely `freud-museum-publications` |
| Books | Books by Freud | ✅ likely `works-by-freud` |
| Books | Psychoanalysis Books | ✅ likely `psychoanalysis-books` |
| Books | Culture and Society | ✅ likely `literature` |
| Books | Introductory | ✅ likely `introductory` |
| Books | Biographies | ✅ likely `biographies` |
| Books | Art and Literature | ✅ likely `art-exhibition-books` |
| Books | Shop All Book Collection | ✅ likely `books` |
| Homeware | Busts and Replicas | 🆕 |
| Homeware | Coasters and Fridge Magnets | 🆕 |
| Homeware | Textiles | 🆕 |
| Homeware | Ceramics | 🆕 |
| Homeware | Prints | 🆕 |
| Homeware | Shop All Homeware Collection | 🆕 |
| Play | Toys | 🆕 |
| Play | Introductory Books | 🆕 (or reuse an existing books collection) |
| Play | Games | 🆕 |
| Play | Sweets | 🆕 |
| Play | Shop All Play Collection | 🆕 |
| Stationery | Postcards and Greeting Cards | 🆕 |
| Stationery | Pens and Pencils | 🆕 |
| Stationery | Notebooks and Journals | 🆕 |
| Stationery | Bookmarks | 🆕 |
| Stationery | Shop All Stationery Collection | 🆕 |
| Style | Scarves | 🆕 |
| Style | Tote Bags and Pencil Cases | 🆕 |
| Style | Jewelry | 🆕 |
| Style | Badges and Keyrings | 🆕 |
| Style | T-shirts | 🆕 |
| Style | Shop All Style Collection | 🆕 |

The Books row handles are the ones we already confirmed from the old live site's HTML —
everything else is a guess at a sensible handle; use whatever Shopify auto-generates
when you create each collection with that title.

## 2. Building the menu

Shopify admin → Content → Navigation → your main menu. Create 6 top-level items, each
with the subcategories nested underneath as sub-links:

- **Book Your Visit** → Admission Tickets, Purchase Your Membership, Gift Membership, Admission Gift Vouchers
- **Books** → Freud Museum Publications, Books by Freud, Psychoanalysis Books, Culture and Society, Introductory, Biographies, Art and Literature, Shop All Book Collection
- **Homeware** → Busts and Replicas, Coasters and Fridge Magnets, Textiles, Ceramics, Prints, Shop All Homeware Collection
- **Play** → Toys, Introductory Books, Games, Sweets, Shop All Play Collection
- **Stationery** → Postcards and Greeting Cards, Pens and Pencils, Notebooks and Journals, Bookmarks, Shop All Stationery Collection
- **Style** → Scarves, Tote Bags and Pencil Cases, Jewelry, Badges and Keyrings, T-shirts, Shop All Style Collection

Top-level item titles matter: Shopify auto-generates a URL handle from each title
(lowercase, spaces → hyphens), and the mega-menu feature blocks below must match that
handle exactly.

| Top-level title | Auto-generated handle |
|---|---|
| Book Your Visit | `book-your-visit` |
| Books | `books` |
| Homeware | `homeware` |
| Play | `play` |
| Stationery | `stationery` |
| Style | `style` |

## 3. Configuring the featured subcategory per category

The colour block + photo treatment is now built into the theme (see
`snippets/header-mega-menu.liquid` and the `FREUD-MEGA-MENU-FEATURED` styles in
`assets/freud-overrides.css`), but which subcategory gets the photo is set per menu
item, in the theme customizer:

1. Customize theme → click the Header section.
2. Add block → "Mega menu: featured subcategory" (repeat for each of the 6 categories).
3. For each block, set:
   - **Menu item handle** — one of the handles from the table above.
   - **Featured subcategory collection** — pick the lead subcategory collection. Its
     title and image are pulled automatically (so upload a good featured image to that
     collection first).

| Menu item handle | Featured subcategory collection |
|---|---|
| `book-your-visit` | Admission Tickets |
| `books` | Freud Museum Publications |
| `homeware` | Busts and Replicas |
| `play` | Toys |
| `stationery` | Postcards and Greeting Cards |
| `style` | Scarves |

If "Admission Tickets" ends up being a product rather than a collection, that one
category won't be able to use the same featured-photo treatment (the block setting
only accepts a collection) — flag this back and we'll adjust, e.g. pointing it at a
simple collection created just to hold ticket-type products, or falling back to the
plain link-list layout for that one category.

Any top-level menu item *without* a matching block just falls back to the existing
plain grid/list layout — nothing breaks if a category is set up before its block is
added.
