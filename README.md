# thilina · things I make

A one-page index of everything I've shipped or am building, linking out to each product's own
site, store listing or repo. Plain HTML and one stylesheet: no build step, no JavaScript, no
third-party requests. Deployed on Vercel with the same security headers as `pickcard-site`.

| File | What it is |
| --- | --- |
| `index.html` | The page: photo, social links, about, then "Out now" and "In the works". One `<li>` per product. |
| `styles.css` | All styles. Light and dark follow the system setting. |
| `404.html` | Not-found page (Vercel serves it automatically). |
| `vercel.json` | Clean URLs plus a strict CSP: only same-origin styles and images, no scripts. |
| `assets/me.svg` | Photo placeholder until `assets/me.jpg` exists. |
| `assets/icons/` | Product icons, 128 px WebP (shown at 56 px, so sharp on 2x screens) or SVG. |
| `og.png` | 1200×630 link preview. |
| `favicon.svg`, `apple-touch-icon.png` | Site icon. |

## Launch checklist

- [ ] **Inkstride store link.** It's marked Live but has no link yet. Add
      `<p class="links"><a href="https://apps.garmin.com/apps/…">Connect IQ Store</a></p>`
      under its description.
- [ ] **Patternwise website URL.** Set to `https://thilinaa.github.io/patternwise-site/`
      (the GitHub Pages default for that public repo). Confirm it is the live address.
- [ ] **Domain.** After buying it, add it in Vercel, then in `index.html` add
      `<link rel="canonical">` and `og:url`, and make `og:image` absolute
      (`https://<domain>/og.png`). Most link previewers ignore a relative `og:image`.
- [ ] **Product subdomains (optional).** Point `pickcard.<domain>`, `sweetregret.<domain>` and
      so on at the existing Vercel projects. The old `*.vercel.app` URLs keep working, so update
      App Store Connect only once the new ones are live.

## Keeping it current

- **Your photo:** save a square photo (at least 300×300) as `assets/me.jpg`, then in `index.html`
  change `src="/assets/me.svg"` to `src="/assets/me.jpg"`. `me.svg` is only a placeholder.
- **About:** the paragraph under "About" in `index.html` is a draft. Rewrite it in your own words.
- **Social links:** add or remove `<a>` tags in `<nav class="social">`.
- **A product ships:** move its `<li>` from "In the works" to "Out now", and swap the
  `<span class="tag">` for its links.
- **New icon:** export at 128×128 WebP into `assets/icons/`. Use `class="icon app"` for iOS
  icons (rounded corners), `icon round` for watch faces, plain `icon` for anything that
  already has its own shape.
- Copy style: no em dashes, short sentences, say what it does rather than how it's built.

## Preview locally

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```
