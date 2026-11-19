# Canva branding reference

This branch restyles the existing static site locally. It does not publish the site or change DNS, Squarespace, or Canva.

## Sources

The logo design is Canva `DAHXnSLKw7U`. The brand-guide copy is `DAHaWAhCC-k`.
The extracted originals are in `/workspace/brand-guide/canva/` on the box.
The prepared artwork is in `/workspace/brand-guide/assets/`.

The connector lists two kits, but does not expose their colors, fonts, or logo inventories.
The colors and typography below come from the exported design, not a claimed Brand Kit inventory.

## Colors

- `#F6F4F0` is the exported logo background and the site's paper color.
- `#222222` is the exported wordmark ink and the site's text color.
- `#000000` appears in the Canva typography specimen and is the text-link hover color.
- Hairline rules use ink at 18% or 32% opacity. Footer rules use paper at 30% opacity. These are decorative blends, not extra brand colors.

Text has no reduced-opacity treatment. Body-copy links stay underlined.
Ink on paper and paper on ink have a contrast ratio of 14.48:1. Black on paper has a ratio of 19.12:1.
Both pairs pass WCAG AA at normal text sizes.

## Fonts and licenses

The site self-hosts WOFF2 files. It makes no font requests to third-party servers at runtime.
Font license notices are in `licenses/`.

| Role | Typeface | Source | License |
| --- | --- | --- | --- |
| Display | Cormorant Garamond Regular 400 | [Google Fonts](https://fonts.google.com/specimen/Cormorant+Garamond/license) | SIL OFL 1.1 |
| Body | Open Sauce One Light 300, Regular 400 available | [Author's repository](https://github.com/marcologous/Open-Sauce-Fonts) | SIL OFL 1.1 |
| Labels and captions | Fira Code Regular 400 | [Google Fonts](https://fonts.google.com/specimen/Fira+Code/license) | SIL OFL 1.1 |
| Logo wordmark | Original outlined Fira Code artwork | Canva logo pages 3 and 4 | Exported artwork, no font dependency |

Calgary is not installed or embedded. [Jen Wagner's Calgary page](https://jenwagner.co/products/calgary-an-essential-serif/) requires a web license for live website text.
No Calgary web license was supplied. Cormorant Garamond is a visual fallback for its narrow, high-contrast serif character, not a claim of an exact match.
The former no-serif rule is superseded by Canva's Calgary display specimen.

Open Sauce One came from the author's `fonts/ttf/OpenSauceOne-Light.ttf` and `OpenSauceOne-Regular.ttf` files.
Google Fonts supplied the Cormorant Garamond and Fira Code TTF files through its public CSS endpoint.
The local WOFF2 files are format conversions of those licensed sources. Open Sauce One's embedded copyright and OFL notice are retained with the OFL text.

## Logo geometry

The header uses the actual Canva N. The home hero uses the prepared stacked lockup. Every footer uses the original outlined uppercase wordmark.
The light footer artwork uses verified paper `#F6F4F0`, not an unverified white surface.
The favicons, social image, and placeholder graphics also use the new artwork, colors, and caption typeface.

The SVG trace follows the Canva raster silhouette and smooths minor edge irregularities. It does not add original detail.
The original vector wordmark preserves Canva's glyph shapes and spacing.

Clear space remains twice the native wordmark's cap height. Its source cap height is 41.84 units.
The CSS rounds the padding up to 0.363 times the N height and 0.095 times the lockup or wordmark width.
The N is 40px tall on desktop and 36px on phones. The lockup and wordmark stay at least 120px wide.
Browser favicons are necessarily smaller than the page-logo minimum.

## Content parity

The branch started from `portraits-optimized` at `1b0c72c`.
On 19 Nov 2026, the About page "Meet the designer" portrait gallery, its CSS, and all `Headshot_*` image files were removed at Maya's request. Later the same day, the About page itself and all About links were removed at Maya's request.
The two projects were renamed to Leavitt Street House and Paulina Street Penthouse.
Paulina Street Penthouse uses Maya's pencil sketch as its main photo, marked Coming soon · 2027.
All other site copy and bracketed placeholders are retained. The footer's old lowercase live-text logo is replaced by Canva's uppercase artwork.

## Local verification

Preview widths are 1440px for desktop and 390px for phones.
The verification also checks 320px, 768px, and 1024px across all four pages.
Checks cover text contrast, horizontal overflow, loaded fonts, missing requests, logo size and clear space, and the mobile menu.
The box keeps full results in `/workspace/neo-noir-canva-verification.json` and the four requested preview PNGs.

Final browser checks passed in all 20 page-and-width combinations. The minimum visible text contrast was 14.48:1.
No horizontal overflow, missing requests, or console errors remained. Mobile menu open and Escape-close checks passed.
Header, hero, and footer logo measurements passed their minimum-size and clear-space checks.
Full-page screenshots use reduced motion so scroll reveals do not hide content in the captured page.
