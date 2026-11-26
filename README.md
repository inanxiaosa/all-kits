# All-kits — three-page football jersey shop

Course: **Introduction to Digital Services — DIG001IT1AE-3033 (Chengdu)**
This is the **implementation** part of the course: the site built from my own *Web site plan*
(All-kits, submitted 24 November 2026), published on GitHub Pages for the task
**“Self study + your test site → My GitHub site”**.

Topic from the plan: **All-kits sells club, retro and printed football jerseys from one small shop in
Helsinki.** Target group: supporters aged 16–45 in Finland and the Nordics, shopping on a phone after a
match, who need real stock for the size they want and a size chart in centimetres.

> Three pages, mobile first, **HTML + CSS only — no JavaScript**, and valid HTML5 (0 errors).

---

## Pages

| File | Job (from the plan) |
|---|---|
| `index.html` | Home — promotion: promise, three featured jerseys with price and stock, proof row, shop story, customer quote |
| `size.html` | Size and fit — one jersey, six size buttons, the stock line for the chosen size, the chart in centimetres, the fit note, add to cart, continue |
| `payment.html` | Payment — order summary, edit link, delivery choice, three payment methods, card fields, pay button with the total, payment help |

Assets: `css/style.css` (one stylesheet), `images/` (four SVG illustrations: three jerseys and the shop rail).

## How the plan's controls were implemented

| Plan control | Implemented as | No JavaScript because |
|---|---|---|
| 1 Menu button (under 768 px) | `<input type="checkbox">` + `<label>` with ☰, CSS `:checked ~ .nav` | a checkbox holds the state |
| 2 Cart button with count | link with a static count badge, on all three pages | prototype has one shirt |
| 3 Shop jerseys (primary action) | `.btn-secondary` on the hero, first screen | — |
| 4 Product card | `.card` with image, price, stock label, button | — |
| 5 Footer “Sizes” link | footer list on every page | — |
| Size buttons XS–XXL | six radio inputs, each label 44 px tall | — |
| Stock line per size | one line per size, shown with `.picker:has(#size-xl:checked)` | CSS `:has()` reads the checked radio |
| Size chart | real `<table>`, `caption`, `th scope` | — |
| Fit note | highlighted `.note` above the cart line | — |
| Add to cart / Continue | `<button type="submit">` and a link to the payment page | — |
| Order summary | `<table>` with `tfoot` total | — |
| Edit order | link back to the size page | — |
| Delivery choice (€4.90 / pickup) | two radios; totals and the pay-button label switch with `:has()` | CSS reacts to the checked radio |
| Payment methods | three radios; card fields appear only for card | same mechanism |
| Card fields | three labelled inputs, `inputmode="numeric"`, `autocomplete` | — |
| Pay button with the total | `.pay-std` / `.pay-pick` spans, swapped by the delivery radio | — |
| Payment failed link | anchor to the help block on the same page | — |

Two things the plan describes that a static page cannot do: the “Added” label for three seconds and the
image cross-fade on click. They are left out rather than faked; everything that decides what the visitor
sees before paying works with CSS alone.

## Design decisions carried over from the plan

**Colour roles** (each with one job, all AA against their surface):

| Role | Hex | Used for |
|---|---|---|
| Primary | `#0F3460` | header, footer, primary button, headings |
| Secondary | `#1A5099` | dividers, secondary buttons, links |
| Accent | `#C62828` | out of stock, errors |
| State | `#2E7D32` | in stock |
| Background | `#F8F9FA` | page behind the white cards |
| Text | `#212121` | body copy |

**Type:** Barlow Condensed Bold for uppercase headings, Inter for text, labels and buttons. Headings use
`clamp()` so they land on 28/22/18 px on a phone and 40/32/24 px on a desktop; body text is 16 px everywhere.

**Accessibility:** skip link, 2 px focus ring, 44 px size buttons, visible labels on every field,
`th scope` in both tables, status never carried by colour alone (the word “In stock” / “Out of stock”
is always printed), `prefers-reduced-motion` and a light print stylesheet.

**Images:** the shop is fictional, so the jerseys are drawn as flat SVG illustrations instead of using
brand photography. They are 3 kB each and stay sharp at any size; the whole site is under 60 kB.

## Run it locally

```bash
python -m http.server 8000
# then open http://127.0.0.1:8000
```

Opening `index.html` directly from disk also works.

## Publish on GitHub Pages

1. Create a new **public** repository, for example `all-kits`.
2. Choose **uploading an existing file** and drag in `index.html`, `size.html`, `payment.html`,
   `README.md`, `css/` and `images/`.
3. Commit.
4. **Settings → Pages → Source: Deploy from a branch → main, folder `/ (root)` → Save.**
5. After a minute: `https://<username>.github.io/all-kits/`.

## The two links for Moodle

```
repository: https://github.com/<username>/all-kits
page:       https://<username>.github.io/all-kits/
```

## Credits

- Fonts: Inter and Barlow Condensed, SIL Open Font License, loaded from Google Fonts with local
  fallbacks (`Segoe UI`, `Arial Narrow`).
- Jersey and shop illustrations: drawn for this project as SVG.
- Everything else — text, layout, CSS — written by hand for this assignment.
