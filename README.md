# HB Casa Cebu landing page

One file: `index.html`. No build step. Open it in a browser, or drop it on any host.

---

## 0. Your logo is already done

Cut from `HB Casa.jpg` and sitting in `img/`. Nothing for you to do here.

| File | Used for |
|---|---|
| `hbmarkwine.png` | The monogram in the nav bar and footer, background removed |
| `hbmarkcream.png` | Same mark in cream, for dark backgrounds. Spare, not used by the page |
| `favicon64.png` | Browser tab icon |
| `appletouchicon.png` | Icon when someone saves the site to their phone home screen |
| `hblogosquare.png` | Square version, 512px. Good for your Facebook page profile picture |

The page palette was also retuned to the exact colours in your logo file:
mark `#511320`, cream `#F0E9CD`.

## 1. Add your photos

Put them in the same `img/` folder as the logo, then replace the 9 placeholder
sources. Search the file for `SWAP:` to find every spot.

| Where | What to put there | Good size |
|---|---|---|
| `--hero-img` (CSS, top of file) | Best wide shot, living area or the view | 1920 × 1280 |
| `img/ogcover.jpg` (Open Graph tags) | The photo Facebook shows when you paste the link | **1200 × 630 exactly** |
| `data-swap="living-room"` | Living area, portrait crop | 1100 × 1350 |
| `data-swap="bedroom"` | The big bed | 1400 × 1100 |
| `data-swap="kitchen"` | Stove + rice cooker | 900 × 900 |
| `data-swap="bathroom"` | Bathroom | 900 × 900 |
| `data-swap="view"` | Lapu-Lapu view from the 5th floor | 900 × 900 |
| `data-swap="pool"` | Village pool | 900 × 900 |
| `data-swap="building"` | Building 303 exterior | 900 × 900 |
| `data-swap="modal-banner"` | Any warm detail shot | 1000 × 400 |

There is also a `<link rel="preload">` near the top pointing at the hero photo.
**Update it to match `--hero-img`**, or the preload does nothing.

### Name files plainly

Lowercase, no spaces, no hyphens: `livingroom.jpg`, `bedroom.jpg`, `ogcover.jpg`.
Some upload tools quietly strip hyphens and spaces from filenames, and then the
page asks for a file that no longer exists and you get a broken image icon.

## 2. Compress before uploading (the big one)

A photo straight off a phone is 4–8 MB. Ten of those is a 50 MB page that will
never finish loading over mobile data, and people leave after about 3 seconds.

Do this to every photo, in this order:

1. **Resize** to the pixel size in the table above (phone photos are ~4000px
   wide, far bigger than any screen needs). Use Photos, Preview, or
   [squoosh.app](https://squoosh.app).
2. **Compress** with [TinyPNG](https://tinypng.com) (drag in up to 20 at once) or
   Squoosh at ~75% JPEG quality.
3. **Check the size.** Aim for **under 250 KB each**, hero under 400 KB.
   The whole `img/` folder should land under about 2 MB.

WebP is smaller still and works in every current browser. Squoosh exports it.
If you use WebP, just change the file extensions in `index.html` to match.

The page already does its share: every image has `loading="lazy"`,
`decoding="async"`, and fixed `width`/`height` so nothing jumps around while
loading. But no amount of that saves a 6 MB JPEG.

## 3. Domain

Set to `https://allainjamesybanez23.github.io/hbcasacebu`. Done.

If you later buy a custom domain, search the file for that URL, replace every
occurrence, redeploy, and re-scrape in the Facebook debugger below.

After the site is live, run the URL through the
[Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) and
click **Scrape Again**. Facebook caches previews aggressively; without this your
old or broken preview can stick around for days.

## 4. Facebook links

Both links are verified working and resolve to your page:

- Page: `https://www.facebook.com/HBCasaCebu`
- Messenger: `https://m.me/HBCasaCebu` → page id `1343625672161125`

To change the handle later, edit the two constants at the top of the `<script>`
block at the bottom of `index.html`:

```js
var FB_PAGE      = 'https://www.facebook.com/HBCasaCebu';
var FB_MESSENGER = 'https://m.me/HBCasaCebu';
```

Every button and link on the page reads from those two, so nothing else needs changing.

## 5. Still to fill in

The page deliberately says "quoted on inquiry" and "arranged with you directly"
rather than inventing numbers. Once you settle on them, update the modal table:

- rates (nightly / weekly / monthly)
- check-in and check-out times
- minimum stay

## 6. Hosting

Any static host works, free tier is plenty:

- **Netlify**: drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop)
- **Vercel**, **Cloudflare Pages**, or **GitHub Pages**: same idea
- Or any web host that serves plain HTML

Put `index.html` and the `img/` folder together at the root.
