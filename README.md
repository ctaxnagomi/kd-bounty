# KRACKED_OS - Slide Studio

**Ghibli low-poly sketch interface** built for the KrackedDevs creative bounty, straight from `krackeddevs-nav-ghibli-template.json`. A full-viewport single-screen experience: three grease-pencil particle brains with mouse-wheel parallax, a floating **360° hold-and-rotate** navigation dial, and a lightweight **Slide Studio** - upload a deck or paste prompts, pick one of four KD background themes, then present fullscreen.

[![Made with: HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white&style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![Made with: CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white&style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![Made with: JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black&style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Built with: Vite/none - Vanilla](https://img.shields.io/badge/Vanilla-F5F5F5?logo=javascript&logoColor=black&style=flat-square)](https://github.com/ctaxnagomi/kd-bounty)
[![Deployed on: Cloudflare Pages](https://img.shields.io/badge/Cloudflare%20Pages-F38020?logo=cloudflare&logoColor=white&style=flat-square)](https://pages.cloudflare.com/)
[![Repo: Public](https://img.shields.io/badge/Repo-Public-181717?logo=github&logoColor=white&style=flat-square)](https://github.com/ctaxnagomi/kd-bounty)

## Try it

## Try it

```
npx serve .
# or any static server
```

Open `index.html`. No build step, no frameworks, no bundler. HTML + CSS + vanilla JS only.

## The experience

1. **Start** - a hand-drawn intro greets you. Press **✦ Surprise me** (a random watercolour sticker + palette each time), then **scroll down** (`mwheeldown`) to enter the stage.
2. **Brains** - three low-poly particle brains (`BUILD / LEARN / EARN`) sit horizontally. The mouse wheel shifts them on the **X axis only** - different depths (`0.4× / 0.7× / 1.0×`) move at different speeds. The page never scrolls vertically.
3. **Navigate** - press and **hold the floating ParentSelector for 180 ms**, then **rotate 360°**. The ring follows your finger/mouse, the DisplayName updates live, and the Indicator panel (left) tracks every child page. Short tap = next child. `PgUp / PgDown` work too.
4. **Slide Studio** (the new section) - open `STUDIO → SlideStudio`:
   - **Upload your slides** - drag & drop or click: `.pptx` is unzipped **in the browser** (no server, no library — `DecompressionStream`), `.md/.txt` parse from headings and `---` breaks, `.key`/`.pdf` give you a friendly nudge to paste instead.
   - **Paste your Slides/keynote/pptx prompts** - type `Slide 1: Title` + bullets, separate slides with `---`. Every line you write stays on the slide.
   - **Limit**: Maximum **15 slides** per deck for optimal performance and readability.
   - **Background slides - choose one of four KD themes:**
     - `KD Theme` - ghibli low-poly teal
     - `KD Pink theme` - watercolour rose
     - `KD Gamified theme` - arcade scoreboard
     - `KD Doodle theme` - paper + marker ink
5. **Present fullscreen** — one click. Lightweight tools only where you'd want them.

## Presenter tools

| Key | Action |
| --- | --- |
| `← →` / `Space` / swipe / click zones | navigate |
| `G` | grid overview (jump to any slide) |
| `P` | pen (draw on the slides) |
| `L` | laser pointer |
| `C` | clear ink |
| `T` | timer |
| `M` | cycle the 4 KD themes live |
| `B` | blackout |
| `F` | fullscreen |
| `?` | shortcuts panel |
| `Esc` | exit |

Ink is stored per slide; notes (speaker notes inside `.pptx` or `notes:` lines in pasted prompts) show at the bottom of each slide.

## Navigation data model (from the design source)

- `PARENTITEM1 · ParentPage1 · Home` — FeaturedDevelopers · BulletinBoard · x Feed · UpcomingHackathon · AgenticQualifier2026
- `PARENTITEM2 · ParentPage2 · CSR/Learning` — CSRProjects · VolunteerForm · Vision & Goals · CoursesHTML-CSS-JS · x Milestone · Gallery
- `PARENTITEM3 · ParentPage3 · Studio` — SlideStudio · PresentMode · RepoNotes

`DisplayName` renders as `Display{ParentItem}{NavTabItem}Name` and updates live as the dial rotates.

## Fixed rules honoured (viewport-safe)

- `html, body` locked to `100%`, `overflow: hidden`, `position: fixed`, `overscroll-behavior: none`
- `meta viewport` with `maximum-scale=1, user-scalable=no`
- Inputs forced to `16px` — no iOS auto-zoom
- `gesturestart / gesturechange / gestureend` prevented — no pinch-zoom
- `-webkit-touch-callout: none` — no long-press popup
- `env(safe-area-inset-*)` respected on all fixed chrome
- Everything stays inside the viewport on every device

## Magnific MCP

The submission workspace declares the Magnific MCP server in `opencode.json`:

```json
{
  "mcpServers": {
    "magnific": { "url": "https://mcp.magnific.com" }
  }
}
```

(opencode format: `{"mcp":{"magnific":{"type":"remote","url":"https://mcp.magnific.com","enabled":true}}}`.)

## Assets

`assets/icons/` holds 53 watercolour stickers cropped from `watercolor-hand-made-icon-pack.png` (the original pack plus the other bountied design assets live in `assets/` on disk; the largest binaries are git-ignored to keep the repo light).

## Files

| File | Purpose |
| --- | --- |
| `index.html` | single-page shell: intro, stage, indicator, telemetry, dial, content panel, presenter |
| `styles.css` | doodle-box system, Ghibli palette, four slide themes, responsive + safe-area rules |
| `app.js` | particle brains, wheel parallax, intro/surprise, ParentSelector press+hold+rotate, telemetry |
| `presenter.js` | deck parsing (text + in-browser PPTX zip reader), theme picker, fullscreen presenter tools |
| `opencode.json` | Magnific MCP server declaration |
| `krackeddevs-nav-ghibli-template.json` | the design source of truth for this build |

## Credits

- Design source: **KRACKED_OS Ghibli-LowPoly** template by KrackedDevs
- Watercolour stickers: Watercolor-made-icon-pack (design asset pack)
- Fonts: [Gaegu](https://fonts.google.com/specimen/Gaegu) + [Spline Sans Mono](https://fonts.google.com/specimen/Spline+Sans+Mono)

Built for the **KrackedDevs creative bounty 2026** · grind on @krackeddevs