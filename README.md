# Decode Nation — landing page (Manifesto v7)

Static one-page site for Decode Nation, a women-owned California social enterprise. This is the direction the client chose ("Manifesto", v7). It is built from `design_handoff_decode_nation_manifesto_v7/` with high fidelity and the copy used verbatim. There is no build step: open `index.html` or serve the folder from any static host (GitHub Pages works, and `.nojekyll` is included).

## Structure

```
index.html        markup, meta, OG and JSON-LD
css/style.css     design tokens in :root, layout, motion, reduced-motion rules
js/main.js        scroll reveal + contact form
assets/           bg-airport-crowd.webp (fixed background), station.webp,
                  founder-*.webp (+ -640 variants for srcset), logo.jpg (favicon)
```

## Contact form

At the top of `js/main.js`:

```js
var FORM_ENDPOINT = '';
```

- **Empty (the current setting):** a valid submit opens the visitor's mail client. The mail goes to `contact@decodenation.com`, with the subject and body already filled in.
- **Set to a URL** (Formspree, Netlify function and so on): the form POSTs JSON `{name, organization, intent, message}` to it. The button shows the pending, success ("Thank you — we’ll be in touch") and error states. Any non-2xx response counts as an error.

Name and Message are required. Organization and interest are optional. The form also has a honeypot field called `website`.

## Before launch

- [ ] Remove `<meta name="robots" content="noindex, nofollow">` from `index.html`.
- [ ] Add the real LinkedIn and Instagram URLs. Each is marked `<!-- TODO client: URL -->` and currently points to `#contact`.
- [ ] Connect the form: set `FORM_ENDPOINT`, or keep the mailto fallback on purpose.
- [ ] Decide on the hero CTA "Explore What We Do →". Its copy is provisional. To remove it, delete the block between the `PROVISIONAL hero CTA` comments.
- [ ] Self-host DM Serif Display and DM Sans. They load from Google Fonts for now.
- [ ] Get a vector logo (SVG) and replace the `logo.jpg` favicon.
- [ ] Confirm image rights. The background is AI-generated and was supplied by the client; also confirm the portraits and the station render.
- [ ] The background source is only 720×1280. On large desktop screens it is upscaled roughly 2× behind the veil, so get a larger original if one exists.
- [ ] Switch OG image to an absolute URL once the domain is known (some scrapers ignore relative `og:image`).
