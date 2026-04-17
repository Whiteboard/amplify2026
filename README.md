# Amplify 2026 — Wireframes

Clickable HTML wireframes for the **Ministry Brands Amplify** website redesign, built by [Whiteboard Agency](https://whiteboard.is).

Live preview: _enable GitHub Pages (see below) to publish at `https://whiteboard.github.io/amplify2026/`_

---

## What this is

A complete, navigable wireframe set covering **44+ pages** of the proposed Amplify site architecture. Every page is a single self-contained HTML file — no build step, no framework, no dependencies. Open one in a browser and it works.

The wireframes cover five primary paths:

| Area | Pages |
|------|-------|
| **Home & Platform** | `index.html`, `platform-overview.html`, `request-demo.html`, `login.html`, `search-results.html` |
| **Products** (10) | `giving.html`, `accounting.html`, `people.html`, `websites.html`, `mobile-app.html`, `communications.html`, `streaming.html`, `service-planning.html`, `media.html`, `safety.html` |
| **Bundles** (4) | `complete-bundle.html`, `generosity-bundle.html`, `financial-bundle.html`, `digital-bundle.html` |
| **Who We Serve** | **Roles** — `senior-pastor.html`, `associate-pastor.html`, `finance-treasurer.html`, `communications-director.html`, `worship-pastor.html`<br>**Church types** — `multi-site.html`, `denominations.html`, `large-churches.html`, `growing-churches.html`, `small-churches.html`, `church-plants.html`, `digital-churches.html` |
| **Services** | `services-overview.html`, `service-detail.html` |
| **Healthy Church Hub** | `healthy-church-hub.html` + templates: `blog-post.html`, `podcast-episode.html`, `ebook-landing.html`, `webinar-registration.html`, `customer-story.html` |
| **Partners** | `partners.html`, `partner-detail.html` |
| **Amplify+ HQ** | `hq.html`, `hq-donor.html`, `hq-financials.html`, `hq-arena.html` |

---

## Running locally

No install. No build. Just serve the folder.

```bash
# from the project root
npx serve -l 5151 .
```

Then open <http://localhost:5151>.

> Opening `index.html` directly via `file://` works, but some flows rely on relative links resolving through a server. Use `npx serve` for the full experience.

---

## Hosting on GitHub Pages

Because every page is static HTML, GitHub Pages is a drop-in host.

1. Push this repo to GitHub (`main` branch).
2. Go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**.
4. Set branch to **`main`** and folder to **`/ (root)`**. Save.
5. Wait ~30 seconds. Your site will be live at `https://<org>.github.io/<repo>/`.

To use a custom domain, add a `CNAME` file at the root containing the domain name (e.g. `amplify-wireframes.whiteboard.is`) and point your DNS `CNAME` record at `<org>.github.io`.

---

## Design system

All pages share a consistent visual system:

- **Brand color** — `#46435D` (deep purple)
- **Typography** — [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts
- **Border radius** — `12px` for cards, `16px` for large containers, `999px` for pills
- **Borders** — `0.5px solid` for subtle separation
- **Navigation** — floating pill nav with hover-driven mega menus (Solutions, Who We Serve, Services)
- **Annotations** — sticky-note overlays (see below)

All styles are inline per file. If you're extending the design system, pick a page close to what you're building (e.g. a product page → copy `giving.html`) and modify in place.

---

## The annotation system

Every page includes a strategic annotation layer — floating cards that explain _why_ each section exists, where content moved from, and what persona/intent it serves. This lets clients and teammates review the wireframes without losing the strategic thread.

### Toggling annotations

A floating **"Show / Hide Annotations"** button sits in the bottom-right of every page. Click it to reveal the annotation overlays and the color legend. Annotations are **hidden by default**.

### Annotation types

| Type | Color | When to use |
|------|-------|-------------|
| 📌 **Design Note** | Yellow | Layout decisions, component choices, visual structure |
| 🗺️ **Page Strategy** | Blue | How this page supports the buyer's journey or information architecture |
| 👤 **Persona Focus** | Purple | Why this section matters to a specific audience (Senior Pastor, Finance Leader, etc.) |
| ⚠️ **Gap Identified** | Orange | Known gaps — missing pages, incomplete content, placeholder routes |
| ✅ **Section Moved** | Green | Content that was relocated from elsewhere in the site (tracks IA changes) |

### Adding an annotation

Drop a `<div class="anno anno-page">` (or `anno-persona`, `anno-gap`, `anno-move`) anywhere inside a section. The `::before` pseudo-element renders the colored label automatically. Example:

```html
<div class="anno anno-page">
  <strong>Hero Strategy:</strong> Establishes the brand promise and offers two
  clear paths — demo (high intent) and platform exploration (research mode).
</div>
```

---

## File structure

```
amplify2026/
├── index.html                 # Homepage
├── *.html                     # All other pages (44+ total)
├── .claude/
│   └── launch.json            # Dev server config for Claude Code preview
├── .gitignore
├── LICENSE                    # Proprietary — All Rights Reserved
└── README.md
```

No `src/`, no `dist/`, no `build/`. Every file in the root that ends in `.html` is a live page.

---

## Editing conventions

- **Inline everything.** Styles live in `<style>` blocks at the top of each file. Scripts live in `<script>` blocks at the bottom. Keeps each page portable.
- **Copy-paste is fine.** When building a new page, copy the closest existing page and modify. The nav, footer, and utility bar are meant to be duplicated, not abstracted.
- **Link wiring matters.** When you add a CTA (`Book a Demo`, `Request Demo`, etc.), make it an `<a>` with `href="request-demo.html"`, not a bare `<button>`.
- **Nav and footer are global.** If you change a nav link, update it across all pages (a simple `sed` or Python script works). The repo has been batch-updated this way multiple times.

---

## Credits

- **Agency** — [Whiteboard](https://whiteboard.is)
- **Client** — Ministry Brands / Amplify
- **Year** — 2026

---

## License

Proprietary — see [LICENSE](./LICENSE).
