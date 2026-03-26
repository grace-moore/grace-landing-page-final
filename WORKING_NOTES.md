# Working Notes — Grace Moore Personal Landing Page

> **Internal document — not intended for public audiences.**
> This file is for developer and AI assistant reference only. Update it at the end of every working session before closing the project.

---

## 1. How to Use This File (For AI Assistants)

Before suggesting changes or writing any code, follow these instructions exactly:

1. Read this entire file from top to bottom before doing anything else.
2. Read `README.md` for the public-facing project description and goals.
3. Do not change the folder structure or file naming conventions without discussing it first.
4. Follow all conventions listed in Section 8 exactly — do not introduce new patterns without flagging them.
5. Do not suggest any approach listed in Section 10 ("What Was Tried and Rejected").
6. Ask clarifying questions before making large structural changes (adding new sections, changing layout, refactoring CSS architecture, etc.).
7. This project was **AI-assisted** (Replit Agent scaffolded the initial HTML/CSS from the PRD and STANDARDS documents). Refactor conservatively — do not rewrite working code without a clear reason.

---

## 2. Current State

**Last Updated:** 2026-03-26

The site is fully built and rendering correctly in the Replit preview. All five sections are in place with real content from the resume. The CSS is clean, responsive, and follows the STANDARDS.md spec. The project is ready for deployment to Azure Static Web Apps once the GitHub repo is pushed and connected.

### What Is Working
- [x] Sticky top navigation with anchor links
- [x] Hero section — headshot, name, title, tagline
- [x] About section — first-person bio, education block
- [x] Experience section — both roles with resume bullet points
- [x] Skills & Activities section — pill tags and activities list
- [x] Contact section — LinkedIn, GitHub, email (all open in new tab)
- [x] Footer
- [x] Fully responsive layout (320px and wider)
- [x] WCAG 2.2 AA accessibility (contrast, alt text, heading hierarchy, keyboard nav)
- [x] No inline styles anywhere — all CSS in `css/stylesheet.css`
- [x] No resume link or phone number on the site
- [x] No-cache development server (`serve.py`) to prevent stale preview issues
- [x] README.md written and saved

### What Is Partially Built
- [ ] `js/scripts.js` exists but is empty — no JavaScript has been written yet (not currently needed)

### What Is Not Started
- [ ] Deployment to Azure Static Web Apps
- [ ] LICENSE file in GitHub repo (MIT)
- [ ] Contact form
- [ ] Dark mode toggle
- [ ] Project portfolio section
- [ ] Custom domain

---

## 3. Current Task

**What I was working on when I last stopped:** The full landing page was built and verified working in the Replit preview. A README.md and WORKING_NOTES.md were added as supporting documentation files. The site content, layout, and accessibility all meet the requirements in `PRD.md` and `STANDARDS.md`.

**The very next step is:** Push all changes from Replit to the GitHub repository (`grace-moore/grace-landing-page-final`), then connect the repo to Azure Static Web Apps for public deployment.

---

## 4. Architecture and Tech Stack

| Technology | Version | Why It Was Chosen |
|---|---|---|
| HTML5 | — | Required by STANDARDS.md; semantic elements used throughout |
| CSS3 | — | Required by STANDARDS.md; all styles in one external stylesheet |
| Vanilla CSS | — | Chosen over Bootstrap/Tailwind per STANDARDS.md (no framework selected) |
| Inter (Google Fonts) | — | Clean, modern, highly legible — matches the professional/approachable tone |
| Python `http.server` | 3.11 | Simple built-in static file server for Replit dev environment; no install needed |
| `serve.py` (custom) | — | Wraps Python's HTTP server with no-cache headers to prevent browser caching stale files in the Replit preview iframe |
| Azure Static Web Apps | — | Specified in PRD.md as the deployment target |
| GitHub | — | Version control; required by PRD.md |
| Replit | — | Development environment |

---

## 5. Project Structure Notes

```
grace-landing-page-final/       ← Repository root
├── index.html                  ← Single-page site entry point
├── serve.py                    ← Dev server with no-cache headers (Replit only)
├── resume.pdf                  ← Source resume (NOT linked from the site)
├── PRD.md                      ← Product Requirements Document
├── STANDARDS.md                ← Technical and design standards (read before every session)
├── README.md                   ← Public-facing project documentation
├── WORKING_NOTES.md            ← This file
├── replit.md                   ← Replit environment notes (auto-managed)
├── /css
│    └── stylesheet.css         ← All styles; no other CSS files exist or should be created
├── /js
│    └── scripts.js             ← Empty; present for folder structure compliance only
└── /images
     └── headshot.jpg           ← Grace's professional headshot
```

**Non-obvious decisions:**
- `resume.pdf` is stored in the repo root but is **intentionally not linked** from the site (per STANDARDS.md override).
- `js/scripts.js` is empty and present only because STANDARDS.md specifies the `/js` folder in the required structure.
- `serve.py` is a Replit development tool only — it is not needed for Azure deployment.
- The `/css` folder contains only `stylesheet.css`. Do not add additional CSS files without discussion.

**Files that must not be changed without discussion:**
- `STANDARDS.md` — defines all technical and design rules
- `css/stylesheet.css` — must remain the single source of styles
- `images/headshot.jpg` — do not rename or move

---

## 6. Data / Database

This project has no persistent data, database, or server-side logic. It is a fully static site. All content is hardcoded in `index.html`.

---

## 7. Conventions

### Naming Conventions
- **Files:** lowercase with hyphens (e.g., `stylesheet.css`, `headshot.jpg`)
- **CSS classes:** lowercase with hyphens (BEM-lite: `section-name`, `section-name__element`, `modifier-name`)
- **HTML IDs:** match the nav anchor name exactly (e.g., `id="hero"`, `id="about"`, `id="experience"`, `id="skills"`, `id="contact"`)
- **Images:** stored in `/images/`, referenced by relative path only (e.g., `src="images/headshot.jpg"`)

### Code Style
- No inline `style=""` attributes anywhere in HTML
- No `<style>` tags in any HTML file
- All external links use `target="_blank" rel="noopener noreferrer"`
- Heading hierarchy: `<h1>` (name in hero) → `<h2>` (section headings) → `<h3>` (subsection headings, e.g., job titles)
- CSS custom properties (variables) defined in `:root` at the top of `stylesheet.css`

### Color Palette (do not change without discussion)
| Variable | Hex | Usage |
|---|---|---|
| `--color-bg` | `#F8F9FA` | Page background |
| `--color-text` | `#212529` | Body copy |
| `--color-accent` | `#0D6E6E` | Headings, links, technical skill tags |
| `--color-secondary-bg` | `#E9ECEF` | Alternating section backgrounds, cards |
| `--color-white` | `#ffffff` | Nav background, hero background, card backgrounds |

### Git Commit Message Style
- Use imperative mood: "Add contact section" not "Added contact section"
- Prefix with action word: `Add:`, `Fix:`, `Update:`, `Remove:`
- Keep the subject line under 72 characters

---

## 8. Decisions and Tradeoffs

- **Vanilla CSS chosen over Bootstrap/Tailwind:** STANDARDS.md listed all three frameworks but did not select one. Vanilla CSS was chosen as the simplest, most standards-compliant option with no external dependencies. Do not suggest adding a framework.
- **No resume link on the site:** STANDARDS.md explicitly states "Do not link to or embed my resume anywhere on the site." This overrides the PRD's Resume section. The `resume.pdf` file remains in the repo but is not referenced in HTML. Do not add a resume link.
- **No JavaScript used:** The site requires no interactivity. `scripts.js` is empty. Do not add JavaScript unless a specific feature requires it and the user approves.
- **No CSS transitions or animations:** Per task scope, transitions were removed from the stylesheet. Do not re-add them without user approval.
- **Phone number omitted from Contact section:** User decision — only email and social links are shown.
- **Headshot renamed to `headshot.jpg`:** Original filename was `DSC00895.headshot_1774384154591.JPG`. Renamed for clarity and to match the path specified in both PRD.md and STANDARDS.md.
- **`serve.py` added for dev server:** Python's default `http.server` was caching the old "Hello World" page in Replit's preview iframe. A custom server with `Cache-Control: no-store` headers was added to fix this. This is a dev-only file.

---

## 9. What Was Tried and Rejected

- **`python3 -m http.server 5000` as the workflow command:** This worked for serving files but caused severe browser caching in the Replit preview iframe. The old "Hello World" page persisted after the new `index.html` was written. Replaced with `serve.py`.
- **Inline `style=""` attributes:** Rejected. STANDARDS.md explicitly prohibits them.
- **`<style>` tags in HTML:** Rejected. STANDARDS.md explicitly prohibits them.
- **Linking to `resume.pdf` from the site:** Rejected. STANDARDS.md explicitly states not to link or embed the resume. Do not suggest this.

---

## 10. Known Issues and Workarounds

- **Browser caching in Replit preview iframe:**
  - **Problem:** Python's default HTTP server does not send no-cache headers. The Replit preview iframe aggressively cached the old `index.html` ("Hello World"), making updated content appear not to load even after workflow restarts.
  - **Workaround in place:** `serve.py` sends `Cache-Control: no-store, no-cache, must-revalidate`, `Pragma: no-cache`, and `Expires: 0` headers on every response. Also sets `allow_reuse_address = True` so the server can restart cleanly without waiting for the port to release.
  - **Do not remove `serve.py` or revert to `python3 -m http.server`** without verifying the caching issue is resolved another way.

---

## 11. Browser / Environment Compatibility

- **Tested in:** Replit preview (Chromium-based iframe)
- **Expected to work in:** Chrome, Safari, Firefox (latest versions)
- **Responsive breakpoints:** 640px (tablet) and 375px (small mobile); minimum supported width is 320px
- **No known incompatibilities**
- **Dev environment:** Replit (NixOS, Python 3.11)
- **Production environment:** Azure Static Web Apps (static file hosting, no server-side runtime)

---

## 12. Open Questions

- Should a `favicon.ico` be added? Currently the browser logs a 404 for favicon on every page load (harmless but present).
- Should `scripts.js` remain empty or be removed? STANDARDS.md requires the `/js` folder, but an empty file adds no value.
- Will the email link (`mailto:`) cause issues on mobile? Should a copy-to-clipboard fallback be considered?
- Once the site is on Azure, should `serve.py` be listed in `.gitignore`?

---

## 13. Session Log

### 2026-03-26
- Built complete `index.html` and `css/stylesheet.css` from scratch using content from `resume.pdf`, `PRD.md`, and `STANDARDS.md`
- Renamed headshot from `DSC00895.headshot_1774384154591.JPG` to `headshot.jpg`
- Created `/css` and `/js` folder structure; `scripts.js` left empty
- Resolved Replit preview caching issue by replacing default Python HTTP server with `serve.py` (no-cache headers)
- Wrote `README.md` with project description, features, contributing guide, license, author, contact, and acknowledgements
- Wrote `WORKING_NOTES.md` (this file)
- Left incomplete: Azure deployment, pushing to GitHub, LICENSE file in repo
- Next step when resuming: Push all changes to GitHub, then connect repo to Azure Static Web Apps

---

## 14. Useful References

- [STANDARDS.md](./STANDARDS.md) — Read before every session; defines all technical and design rules
- [PRD.md](./PRD.md) — Product requirements; defines sections, content, and goals
- [MDN: HTML5 Semantic Elements](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#semantics_in_html)
- [MDN: CSS Custom Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [WCAG 2.2 Guidelines](https://www.w3.org/TR/WCAG22/)
- [Google Fonts — Inter](https://fonts.google.com/specimen/Inter)
- [Azure Static Web Apps Quickstart](https://learn.microsoft.com/en-us/azure/static-web-apps/getting-started)
- [GitHub: Connecting a repo to Azure Static Web Apps](https://learn.microsoft.com/en-us/azure/static-web-apps/github-actions-workflow)
- AI assistant (Replit Agent) — Used to generate the initial HTML/CSS structure, resolve the caching issue, write README.md and WORKING_NOTES.md. All content reviewed and approved by the author.
