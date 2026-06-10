# yossi eliaz — a living preprint

Personal website for [Yossi Eliaz](https://github.com/zozo123), carrying the full content of the
GitHub profile README — every live essay, demo, stat and planner — styled as an annotated
scientific preprint.

- **Type**: static site, no build step (`index.html` + `css/` + `js/` + `assets/`)
- **Typography**: Fraunces · Spectral · IBM Plex Mono (Google Fonts)
- **Thumbnails**: real screenshots of each live GitHub Pages site, captured with headless Chrome
  (`assets/thumbs/*.jpg`, 760px wide, ~50KB each)
- **Cards data**: edit `js/main.js` (`FIGSETS`) to add or reorder posts

## Preview

```bash
python3 -m http.server 8417
# → http://localhost:8417/
```

## Deploy

Any static host works — GitHub Pages, Netlify (`yossieliaz.netlify.app`), Vercel. No config needed.

## Refresh thumbnails

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless=new --hide-scrollbars --window-size=1280,800 --timeout=15000 \
  --screenshot=shot.png "https://zozo123.github.io/<repo>/"
sips -s format jpeg -s formatOptions 72 --resampleWidth 760 shot.png \
  --out assets/thumbs/<repo>.jpg
```
