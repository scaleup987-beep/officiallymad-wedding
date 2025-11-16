# officiallymad-wedding — #OfficiallyMaD Wedding Website

Live site: https://officiallymad.fun

This repository contains the static website for Deshna & Mehul’s wedding. It is a single-page site (`index.html`) served via GitHub Pages with a custom domain (`CNAME`).

**Repo Structure**
- `index.html`: All markup, styles, and scripts (self-contained)
- `wedding-logo.jpeg`: Logo displayed in the header
- `CNAME`: Custom domain configuration for GitHub Pages

**Local Preview**
- Double-click `index.html` to open in a browser, or serve locally to avoid any asset/path quirks:
	- Python: `python3 -m http.server 8080`
	- Node (serve): `npx serve -l 8080`
	- Then visit `http://localhost:8080`

**Deployment**
- Branch: `main` is published by GitHub Pages.
- Deploy steps: commit to `main` → GitHub Pages rebuilds automatically (usually within 1–2 minutes).
- Custom domain is configured via `CNAME` (https://officiallymad.fun).

**Logo Notes (Visibility Fix)**
- The site uses a global fade‑in animation for images. This can leave images at `opacity: 0` if animations are blocked.
- To ensure the logo always shows, we override the rule in `index.html`:
  
	`.wedding-logo { opacity: 1 !important; animation: none !important; }`
  
- The logo file used is `wedding-logo.jpeg` and referenced near the top of the header.

Recommendation: If you want fade‑in effects, scope them to a class instead of all images. Example:

```
/* Use on selected images instead of img { ... } */
.fade-in-img {
	opacity: 0;
	animation: fadeInImage 1s ease-in forwards;
}
```

**Caching & Hard Refresh**
- GitHub Pages and browsers can cache aggressively. If changes don’t appear:
	- Hard refresh (Mac): Chrome/Edge/Firefox `Cmd+Shift+R`, Safari `Cmd+Option+R`
	- Try an incognito/private window
	- Verify asset availability: `curl -I https://officiallymad.fun/wedding-logo.jpeg`

**Troubleshooting**
- Logo not visible:
	- Confirm the file exists at the repo root: `wedding-logo.jpeg`
	- Confirm the `<img src="wedding-logo.jpeg">` path matches (case sensitive)
	- Ensure the override exists: `.wedding-logo { opacity: 1 !important; animation: none !important; }`
	- Bypass cache with a hard refresh or try incognito
- Broken links or 404s: check paths relative to `index.html` (root), or place assets in `assets/` and update references accordingly.

**Contributing / Editing**
- Keep changes minimal and focused.
- Test locally, then commit to `main`.
- If extracting CSS/JS to separate files later, remember to update paths and consider cache‑busting (e.g., `?v=1`).

— #OfficiallyMaD 💕
