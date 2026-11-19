# Neo-Noir Studio: website

Portfolio site for **Neo-Noir Studio**, interior design, Chicago, IL.
Plain HTML/CSS with a little vanilla JS. No build step: GitHub Pages serves the files exactly as they are.

- Live URL (once published): https://neo-noirstudio.com (set by the `CNAME` file; the repo is also reachable at https://neonoirstudio.github.io)
- Repo name: `neonoirstudio.github.io`, branch `main`, served from the root

## Canva branding

The local `canva-branding` branch uses the actual Canva script N and Fira Code wordmark.
Its colors are `#F6F4F0`, `#222222`, and `#000000`. Text links use underlined ink instead of Rouge.
The site self-hosts Open Sauce One and Fira Code. Cormorant Garamond is the free display fallback for Calgary.

[CANVA-BRANDING.md](CANVA-BRANDING.md) records the font sources, licenses, logo measurements, and local-only scope.
The site keeps the existing content and placeholders, with two projects. Designer portraits have been removed from the About page.

## Files

```
index.html                  ← home page: hero, projects (2), contact
about.html                  ← About page: the studio as a firm (not a personal bio)
projects/project-1.html     ← Leavitt Street House (Beverly)
projects/project-2.html     ← Paulina Street Penthouse (West Town; coming soon in 2027)
assets/css/styles.css       ← colours, fonts, layout
assets/js/main.js           ← mobile menu toggle + gentle scroll fade-in (the site works without it)
assets/images/              ← logo files, photos (placeholders for now), favicon, social-share image
CNAME                       ← custom domain for GitHub Pages (neo-noirstudio.com), do not delete
.nojekyll                   ← tells GitHub Pages to skip Jekyll processing
```

Navigation has Projects, About, and Contact. Services remain one line on the About page.

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
- Specs: Year and Scope (Location and Type are filled in; Paulina Street Penthouse also has Year 2027 and Status). Delete any row you don't want to show.
- Project description
- Image alt text

Confirmed by Maya: Leavitt Street House is a 1920s Dutch Colonial in Beverly; Paulina Street Penthouse is a midcentury condo in
West Town, coming soon in 2027. The type shows in the Type spec on each project page, under the project name on the home page,
and in the "Next project" block.
Each name appears on its own page, in its row on the home page, and in the "Next project" block on the other project's page.

**Instagram:** replace `[@instagram-handle]` with the link shown in the comment just above it, e.g.
`<a class="text-link" href="https://www.instagram.com/HANDLE/" rel="noopener">@HANDLE</a>`.
Do this in `index.html` (Contact) and in the footer of every page.

## Swapping in photos

Right now the site uses light placeholder SVGs (Fog Mist panels with a Noir label naming the file that
replaces them). To use real photos:

1. Export each photo as a JPG with exactly these names and put them in `assets/images/`
   (`N` is 1 for Leavitt Street House, 2 for Paulina Street Penthouse):

   | File | Used for | Shape | Recommended size |
   |---|---|---|---|
   | `project-1.jpg`, `project-2.jpg` | Main photo of each project: home-page row (wide image), top of its project page, "Next project" block. **`project-1.jpg` (Leavitt Street House) is also the framed photo under the logo on the home page** (cropped to 16:9 on desktop, 4:3 on phones, so keep the subject near the middle). | 4:3 landscape | 2400 × 1800 px |
   | `project-N-2.jpg` | Tall detail next to the main photo on the home page; left of the pair on the project page | 4:5 portrait | 1200 × 1500 px |
   | `project-N-3.jpg` | Right of the pair on the project page | 4:5 portrait | 1200 × 1500 px |
   | `project-N-4.jpg` | Full-width photo right after the project description | 3:2 landscape | 2400 × 1600 px |
   | `og-image.png` (optional replacement) | Social share preview | 1.91:1 | 1200 × 630 px |

   `project-2.jpg` and `project-2.webp` are already in place: Maya's pencil sketch of the Paulina Street Penthouse building (native 1540 × 1021). The home-page row and project hero show that sketch alone, uncropped (`object-fit: contain`). Additional Paulina Street Penthouse slots (`project-2-2` through `project-2-4`) are still placeholder SVGs until photos are added.

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
