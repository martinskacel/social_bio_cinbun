# The Social Biography of a Pastry at the Fern

An interactive, scroll-based ethnography by Martin Skacel (Anthropology of Food, Dartmouth College).
Plain HTML, CSS, and JavaScript. No frameworks, no build step, nothing to install.

---

## 1. Folder structure

Create a folder on your Desktop called `pastry-biography` (or unzip `pastry-biography.zip` there).
It must look exactly like this:

```
pastry-biography/
├── index.html                 ← the whole story (all text and quotes live here)
├── .nojekyll                  ← empty file; tells GitHub Pages to serve files as-is
├── README.md                  ← this guide
├── QUOTE-VERIFICATION.md      ← checklist of every quote and fact to confirm
├── css/
│   └── styles.css             ← all colors, fonts, and layout
├── js/
│   └── main.js                ← navigation, diagrams, map, dots, checklist
└── assets/
    ├── icons/
    │   └── favicon.svg        ← the cinnamon-swirl browser tab icon
    ├── images/                ← your 9 photos go here
    │   └── PUT-PHOTOS-HERE.txt
    └── video/                 ← your bakery video goes here
        └── PUT-VIDEO-HERE.txt
```

> Files starting with a dot (`.nojekyll`) are hidden on Mac. In Finder press
> **Cmd + Shift + .** to see them. If it goes missing, the site still works.

---

## 2. Add your photos and video

Name files **exactly** as below: all lowercase, ending in `.jpg`.
GitHub Pages is case-sensitive, so `Hero.JPG` will not load.

| File name (in `assets/images/`) | What goes there | Where |
|---|---|---|
| `hero-kaf-pastry-display.jpg` | KAF pastry display with cinnamon buns, labels, prices | Top of page (tall/portrait) |
| `ch1-fern-pastry-shelves.jpg` | Pastries on glass shelves at the Fern | Chapter 1 |
| `ch1-fern-counter.jpg` | Customer at the Fern counter, employee preparing order | Chapter 1 |
| `ch2-kaf-display-case.jpg` | Finished pastries in a bakery display case | Chapter 2 |
| `ch3-dough-and-scale.jpg` | Dough in large container beside commercial scale | Chapter 3 |
| `ch4-kaf-bakery-rack.jpg` | Tall wheeled bakery rack with trays (portrait) | Chapter 4 map, step 1 |
| `ch4-kaf-delivery-van.jpg` | KAF delivery van parked outside | Chapter 4 map, step 2 |
| `ch4-white-delivery-bins.jpg` | Stacks of reusable white bins at the Fern | Chapter 4 map, step 4 |
| `ch4-fern-register.jpg` | Fern employee at register beside pastry display | Chapter 4 |

| File name (in `assets/video/`) | What goes there |
|---|---|
| `ch3-bakers-cutting-dough.mp4` | Bakers cutting and weighing dough (Chapter 3) |

**Tips**
- iPhone photos are often `.HEIC`. Export as JPEG first (Photos → File → Export).
- Resize photos to about 2000 px on the long side (300–600 KB each). On Mac: open in
  Preview → Tools → Adjust Size.
- **Missing photo?** The site shows a dashed box naming the exact file it expects.
- **Video:** until `ch3-bakers-cutting-dough.mp4` exists, the site embeds your Google
  Drive copy automatically. The Drive file must be shared as *Anyone with the link can view*.
  Keep the MP4 under ~25 MB (GitHub's website uploader rejects bigger files). HandBrake
  (free) shrinks videos easily.
- **Photo cropped badly?** In `index.html`, find the photo and change
  `style="--ratio: 3 / 2"` to match it (`4 / 5` portrait, `4 / 3`, `16 / 9`).
  To show the whole photo without cropping: `style="--ratio: 3 / 2; --fit: contain"`.

---

## 3. Preview on your computer

1. Open the `pastry-biography` folder in VS Code (File → Open Folder).
2. Install the **Live Server** extension (Extensions sidebar → search "Live Server" by Ritwick Dey).
3. Right-click `index.html` → **Open with Live Server**. The site opens in your browser
   and refreshes every time you save.

(Double-clicking `index.html` also works, but Live Server behaves more like the real site.)

---

## 4. Publish with GitHub Pages

**Option A — GitHub website (simplest)**
1. Go to github.com → **New repository**. Name it `pastry-biography`, set it to **Public**, create it.
2. Click **uploading an existing file**. Drag in *everything inside* your `pastry-biography`
   folder (index.html, css, js, assets, .nojekyll …), not the folder itself.
3. Click **Commit changes**.
4. Go to **Settings → Pages**. Under *Build and deployment*, choose
   **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
5. Wait 1–3 minutes. Your site will be at:
   **https://martinskacel.github.io/pastry-biography/**

**Option B — GitHub Desktop** (better for large videos and frequent edits): add the folder
as a repository, publish it, then do step 4 above. Every later change: *Commit* → *Push*.

**After it's live:** in `index.html`, near the top, replace the `og:image` path with the
full URL (`https://martinskacel.github.io/pastry-biography/assets/images/hero-kaf-pastry-display.jpg`)
so link previews show your photo.

---

## 5. How to edit things later

Everything you'd want to change is in `index.html`, in order, with comments marking each
chapter (`CHAPTER 1`, `CHAPTER 2`, …).

**Edit text:** just change the words inside `<p> … </p>`.

**Add a quote:** copy an existing block and change the words and speaker:

```html
<figure class="voice" data-voice="student">
  <blockquote><p>“The quote goes here.”</p></blockquote>
  <figcaption><span class="voice__name">Maddie</span></figcaption>
</figure>
```

- `data-voice` sets the color: `maker` (King Arthur), `fern` (the Fern), `student`.
- Add `voice--feature` to the class (`class="voice voice--feature"`) for a big quote.

**Add a photo:** copy an existing `<figure class="media is-wide">` block, change the
`src`, `alt` (describe the photo for screen readers), and caption. Drop `is-wide` for a
text-width photo.

**Add a citation:** in-text citations look like
`(<button class="cite" type="button" popovertarget="ref-crowther">Crowther 2018</button>)`.
For a new source, copy one of the `<div popover>` boxes at the bottom of `index.html`, give
it a new `id`, use that id in `popovertarget`, and add the full reference to the References list.

**Change colors or fonts:** top of `css/styles.css`, section 1 (Design tokens).

**Change the route labels** (left rail / phone menu): near the top of `index.html`,
inside `<nav class="route">`.

**Change the time-of-day of a section:** its `data-theme` attribute —
`icing`, `dough`, `crust`, `night`, `dawn`, or `golden`.

**Remove an interactive piece:** delete its block in `index.html` (each is commented:
dough diagram, repetition dots, map, ledger, checklist). Nothing else breaks.

---

## 6. Accessibility and performance notes

- Works with keyboard and screen readers; all interactive pieces are real buttons/checkboxes.
- Respects "Reduce motion" settings (no title animation, no autoplay, instant diagrams).
- Readable without JavaScript; the extras simply don't appear.
- Please make each photo's `alt` text describe what's actually in it.
