# Neo-Noir Studio: website

Portfolio site for **Neo-Noir Studio**, interior design, Chicago, IL.
Plain HTML/CSS with a little vanilla JS. No build step: GitHub Pages serves the files exactly as they are.

- Live URL (once published): https://neo-noirstudio.com (set by the `CNAME` file; the repo is also reachable at https://neonoirstudio.github.io)
- Repo name: `neonoirstudio.github.io`, branch `main`, served from the root

## Look and feel

The site follows the **Neo-Noir Studio brand guidelines** (logo, color and typography pages): light and quiet,
with Swiss Coffee paper, Noir type, the script N logo as artwork, and plenty of white space. Thin Fog Mist
hairlines separate rows, and there are no gradients or glows. The only motion is a gentle fade-in on scroll, which is
switched off for visitors who prefer reduced motion. The photographs supply the colour. The layout keeps the editorial
structure: a three-part header, project rows, ruled tables and individual project pages. Text aligns left; only the
logo is centred.

## Brand tokens

All of these are CSS custom properties at the top of `assets/css/styles.css` (`:root`).

**Colour** (Benjamin Moore references. The paint codes are the source of truth, and these are the screen values.)

| Token | Hex | Role | Share |
|---|---|---|---|
| `--noir` | `#333333` | Primary: logo, all type, dark fields (the footer) | ~20% |
| `--swiss-coffee` | `#EEECE2` | Primary: page / paper background (BM OC-45) | ~50% |
| `--fog-mist` | `#E1DDD1` | Greige: panels, photo placeholders, hairline rules (BM OC-31) | ~15% |
| `--glacier-white` | `#ECEAE1` | Cooler white: alternate grounds (Contact) (BM OC-37) | ~7% |
| `--whitall-brown` | `#786C5F` | Warm taupe: only for large type (24px+) because it is 4.3:1 on Swiss Coffee. Used for the big project numerals (BM HC-69) | ~5% |
| `--dry-sage` | `#A29F86` | Accent, details only: the short rules above the hero tagline and on the project title rule (BM 2142-40) | ~3% |
| `--rouge` | `#C8102E` | Links and interactive moments **only** (5.0:1 on Swiss Coffee) | links |

Pairings: Noir on Swiss Coffee is 10.7:1, and Swiss Coffee on Noir is 10.7:1 (footer). On Noir (or Whitall Brown)
grounds, links switch to underlined Swiss Coffee. Small captions and eyebrow labels use Noir at 80% opacity
(`--noir-soft`, about 6:1) rather than Whitall Brown, so they stay WCAG AA.

**Typography**: two families, both free from Google Fonts. There is no serif, and words are never set in a script typeface (the
script N is drawn artwork).

| Style | Spec | Used for |
|---|---|---|
| Display | Montserrat Light 300, 44/52, caps, +300 (0.3em) | section titles (Projects, About, Contact) |
| Heading | Montserrat Light 300, 28/36, caps, +280 | project titles, project names |
| Subhead | Montserrat Medium 500, 13/20, caps, +240 | navigation, next-project name |
| Body | IBM Plex Mono Regular 400, 16/26, sentence case | all running text |
| Caption | IBM Plex Mono 400, 13/20 | photo captions |
| Link | IBM Plex Mono 400 in Rouge, 1px underline, 3px offset, hover Noir | text links |
| Label | IBM Plex Mono SemiBold 600, 12/18, caps, +40 | CHICAGO / EST 2026, spec and contact table labels, footer headings, button |
| Eyebrow | IBM Plex Mono 400, 12px caps | small section labels ("The studio", "Selected work") |

Display and Heading scale down on small screens. The page loads only the weights in use (Montserrat 300/500 and
Plex Mono 300/400/600; the Light 300 is only for the footer wordmark). If you need Montserrat 400 later, add it to the
Google Fonts link in each page's `<head>`.

**Logo** (`assets/images/`)

The logo (updated Sep 30, hi-res file) is a flowing script **N**: long hairline swashes to the left and right, both main
strokes looping at the bottom, and a fine diagonal hairline between them that tapers out from both ends and
breaks midway (as in Maya's file), set above the NEO-NOIR STUDIO wordmark. The mark was
traced to vectors from scratch from Maya's hi-res logo JPEG (1024 px wide artwork). The wordmark is set in Montserrat
outlines, matched to the logo's letter size, weight and per-letter positions (the source measures as Montserrat Regular
400, tracked about 0.56em). No font is needed to display any logo file.

The footer uses Maya's **lowercase monospace wordmark**, "neo-noir studio", as live text (not an image): IBM Plex Mono
Light 300, lowercase, letter-spacing .387em (measured on her file: letter pitch = 0.987 × font size), in Swiss Coffee on
the Noir footer, 16–18px.

| File | What it is | Where it's used |
|---|---|---|
| `logo-lockup.svg` | Primary lockup: script N + NEO-NOIR STUDIO wordmark, Noir (landscape, about 1.67 : 1) | home-page hero, social image |
| `logo-lockup-light.svg` | Same lockup in Swiss Coffee, for Noir grounds | available; the footer now uses the lowercase wordmark |
| `logo-monogram.svg` | Script N alone, Noir (wide, about 2.5 : 1) | header centre |
| `logo-wordmark.svg` | Wordmark alone, Noir | available; not used on the site yet |
| `favicon.svg`, `favicon.ico`, `apple-touch-icon.png` | The N's main strokes on Swiss Coffee (the long swashes are cropped so it reads at 16–32px) | browser tab / home screen |
| `og-image.png` (+ `og-image.svg` source) | 1200 × 630 social-share preview: lockup, "Chicago · Est 2026" and tagline on Swiss Coffee | link previews |

Rules, enforced in the CSS:
- **Clear space:** keep a margin of *x* on every side, where **x = 2 × the cap height of the NEO-NOIR STUDIO
  wordmark**. Measured on the artwork, *x* = 0.209 × the script N's height = 0.0809 × the lockup's width
  (`--x-per-mono-h`, `--x-per-lockup-w`). The header mark and hero lockup are padded by *x*. The footer wordmark
  keeps 2 × its own cap height (about 1.4em) clear through the footer's padding and grid gaps.
- **Minimum sizes:** primary lockup 120px wide; wordmark 120px wide; script N **36px tall (about 90px wide)**. Below
  that, the hairline swashes fade out on standard-resolution screens. On the site, the header mark is 40px tall
  (36px on phones), the hero lockup is 240–352px wide.
  The browser-tab favicon is necessarily smaller; it is an icon, not a logo placement.
- To recolour a logo file, open it in a text editor and change its `fill`.

**Brand copy** taken from the logo artwork and used as written: "Neo-Noir Studio", "Chicago", "Est 2026" and the
tagline "Driven by quality. Chosen by those who know the difference." (under the hero lockup and in every footer).

## Files

```
index.html                  ← home page: hero, projects (2), contact
about.html                  ← About page: the studio as a firm (not a personal bio)
projects/project-1.html     ← Leavitt Street (Beverly)
projects/project-2.html     ← Paulina (West Town)
assets/css/styles.css       ← colours, fonts, layout
assets/js/main.js           ← mobile menu toggle + gentle scroll fade-in (the site works without it)
assets/images/              ← logo files, photos (placeholders for now), favicon, social-share image
CNAME                       ← custom domain for GitHub Pages (neo-noirstudio.com), do not delete
.nojekyll                   ← tells GitHub Pages to skip Jekyll processing
```

Navigation (header and footer): Projects, About, Contact. The site is deliberately simple: there is no
photo of Maya or personal bio, and no separate services section (services are one line on the About page).

## Filling in the text

Every piece of placeholder copy is in **[square brackets]**. To find them all, search `index.html`,
`about.html` and the files in `projects/` for `[`. Replace each one, including the brackets.

**Home page (`index.html`)**
- Meta description (appears twice: once for search engines, once for Open Graph)
- One-line description of each project (2 rows)
- Contact intro
- Instagram handle (in the Contact section **and** the footer)
- Image alt text

**About page (`about.html`)**: about the studio as a firm
- Meta description (appears twice)
- Studio statement (1–2 sentences on the studio's point of view)
- About the studio (a short paragraph on what the firm does and how it works with clients)
- Services (a short list or one sentence)
- "Based in Chicago, IL" and "Established 2026" come from the logo artwork; delete either row if not wanted.

**Each project page (`projects/project-N.html`)**
- Meta description (in the `<head>`)
- Specs: Year and Scope (Location and Type are filled in). Delete any row you don't want to show.
- Project description
- Image alt text

Confirmed by Maya: Leavitt Street is a 1920s Dutch Colonial in Beverly; Paulina is a midcentury condo in
West Town. The type shows in the Type spec on each project page, under the project name on the home page,
and in the "Next project" block.
Each name appears on its own page, in its row on the home page, and in the "Next project" block on the other project's page.

**Instagram:** replace `[@instagram-handle]` with the link shown in the comment just above it, e.g.
`<a class="text-link" href="https://www.instagram.com/HANDLE/" rel="noopener">@HANDLE</a>`.
Do this in `index.html` (Contact) and in the footer of every page.

## Swapping in photos

Right now the site uses light placeholder SVGs (Fog Mist panels with a Noir label naming the file that
replaces them). To use real photos:

1. Export each photo as a JPG with exactly these names and put them in `assets/images/`
   (`N` is 1 for Leavitt Street, 2 for Paulina):

   | File | Used for | Shape | Recommended size |
   |---|---|---|---|
   | `project-1.jpg`, `project-2.jpg` | Main photo of each project: home-page row (wide image), top of its project page, "Next project" block. **`project-1.jpg` (Leavitt Street) is also the framed photo under the logo on the home page** (cropped to 16:9 on desktop, 4:3 on phones, so keep the subject near the middle). | 4:3 landscape | 2400 × 1800 px |
   | `project-N-2.jpg` | Tall detail next to the main photo on the home page; left of the pair on the project page | 4:5 portrait | 1200 × 1500 px |
   | `project-N-3.jpg` | Right of the pair on the project page | 4:5 portrait | 1200 × 1500 px |
   | `project-N-4.jpg` | Full-width photo right after the project description | 3:2 landscape | 2400 × 1600 px |
   | `og-image.png` (optional replacement) | Social share preview | 1.91:1 | 1200 × 630 px |

   Photos in other shapes are fine too. They're center-cropped to fit (`object-fit: cover`), but matching
   these shapes gives you control over the crop. Aim for **under ~400 KB each** (the large hero/full-width ones
   may be up to ~600 KB; use JPG quality around 75–80, e.g. via squoosh.app) so the site stays fast.

2. Change the file extensions from `.svg` to `.jpg` in `index.html` and `projects/*.html`.
   From a terminal you can do it in one step:

   ```sh
   sed -i.bak -E 's#(assets/images/)(project-[1-2](-[2-4])?)\.svg#\1\2.jpg#g' index.html projects/*.html && rm index.html.bak projects/*.bak
   ```

   If only some photos are ready, change just those file names by hand.

3. Update each image's `alt="[Alt text: …]"` with a short description of the photo
   (e.g. what room it is and what stands out). This matters for accessibility and SEO.

4. Delete the placeholder SVGs (`project-*.svg`) once they're no longer referenced.

## Adding a project later

Copy `projects/project-2.html` to `projects/project-3.html`, update the name, location and image names inside
(`project-3`, `project-3-2` … `project-3-4`), copy a whole `<li class="project-row …">` block in `index.html`,
and point the "Next project" links so they loop (1 → 2 → 3 → 1).

## Preview locally

```sh
cd neo-noir-site
python3 -m http.server 8000
# open http://localhost:8000
```

## Publish (later)

Create the public repo `neonoirstudio.github.io` under the `neonoirstudio` account, push `main`,
then in **Settings → Pages** set Source to "Deploy from a branch" → `main` / `(root)`.
The `CNAME` file sets the custom domain to `neo-noirstudio.com`. The domain's DNS also needs to point at
GitHub Pages (see GitHub's "Managing a custom domain" docs) before that address works.
