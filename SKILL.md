---
name: marp-slides-pro
description: Create professional MARP presentation decks with SVG charts, interactive elements, dashboard components, animations, dark/light themes, brand system, and 30+ layout templates. Triggers on 'marp', 'slides', 'presentation', 'deck'.
version: 3.0
updated: 2026-04-10
---

# MARP Slides Pro v3

## Prerequisites
- VS Code extension "Marp for VS Code"
- Settings: `markdown.marp.enableHtml: true` + `markdown.marp.allowLocalFiles: true`
- Export: `npx @marp-team/marp-cli slides.md --pdf --allow-local-files`

## Example Decks (CRITICAL — read before generating)

The `examples/` folder contains 22 curated reference decks. **Before generating any deck, read 2-3 examples that match the requested style.** These are the quality bar — match their composition, spacing, and visual density. Key examples by category:

| Category | Examples to read |
|---|---|
| Data / dashboard | `marp_facebook-ads.md`, `marp_fitness.md`, `marp_comparison.md` |
| Lifestyle / editorial | `marp_coffee.md`, `marp_wine-tasting.md`, `marp_cocktail.md` |
| Guide / how-to | `marp_garden.md`, `marp_houseplant.md`, `marp_home-gym.md` |
| Fun / creative | `marp_kids-party.md`, `marp_board-game.md`, `marp_film-director.md` |
| Travel / location | `marp_travel.md`, `marp_walking-tour.md`, `marp_road-trip.md` |
| Showcase / hero | `marp_hero.md`, `marp_apartment.md`, `marp_wardrobe.md` |
| Reference / sampler | `marp_sample.md` (component showcase) |

## Core Rules
- Slides separated by `---`
- YAML frontmatter controls theme/pagination/styles
- `enableHtml` unlocks SVG, cards, charts, animations, interactive elements
- Default 16:9 (1280x720)

## Dark Starter Template

The dark template uses Outfit 800 for headings and Raleway 100-200 for body text. CSS variables:

```css
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;600;700;800&family=Raleway:wght@100;200;300&display=swap');

:root {
  --accent: #ff6b1a; --accent-hover: #ff8c4a;
  --dark: #000; --card: #080808; --border: #111;
  --body: #999; --label: #666; --muted: #555; --light: #fff;
  --green: #22c55e; --red: #ef4444; --yellow: #f5a623;
}
section { background: var(--dark); color: var(--light); font-family: 'Raleway', sans-serif; font-weight: 200; padding: 56px 72px; }
h1 { font-family: 'Outfit'; font-weight: 800; font-size: 3em; color: var(--light); }
h2 { font-family: 'Raleway'; font-weight: 100; font-size: 1.3em; color: #888; }
h3 { font-family: 'Outfit'; font-weight: 600; font-size: 0.6em; color: var(--muted); text-transform: uppercase; letter-spacing: 0.2em; }
strong { color: var(--accent); font-weight: 300; }
section.lead { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
header { text-align: right; } header img { margin: 0; }
.row:hover { background: #0c0c0c; } .row { transition: background 0.2s; border-radius: 6px; }
details { background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 14px 18px; margin-top: 8px; }
details summary { color: var(--accent); font-family: 'Outfit'; font-weight: 600; font-size: 0.8em; cursor: pointer; }
details p { color: var(--body); font-size: 0.78em; margin-top: 8px; }
.tag { font-family: 'Outfit'; font-weight: 600; font-size: 0.55em; letter-spacing: 0.12em; text-transform: uppercase; padding: 3px 10px; border-radius: 4px; }
abbr { text-decoration: none; border-bottom: 1px dotted #333; cursor: help; }
```

Frontmatter includes: `header: '![w:100](./logo.png)'`

## Light Theme
Swap vars: `--accent: #2563eb; --dark: #fafafa; --card: #fff; --border: #eee; --body: #666; --label: #bbb; --light: #1a1a1a;`
Use Space Grotesk + IBM Plex Mono or Plus Jakarta Sans.

## Heading Hierarchy
- h1 = title slides (white, extra large)
- h2 = subtitle (grey, thin)
- h3 = section label (muted, uppercase, small)

## Font Pairings (Tested)

| Heading | Body | Use |
|---|---|---|
| Outfit 800 | Raleway 100 | Dashboard, data (default) |
| DM Serif Display | DM Sans 300 | Recipes, editorial |
| Space Grotesk 700 | IBM Plex Mono 300 | Travel, light themes |
| Sora 700 | Sora 200 | Product comparisons |
| Urbanist 800 | Urbanist 100 | Music, Spotify-style |
| Plus Jakarta Sans 800 | Plus Jakarta Sans 200 | Retros, team decks |

## Images

CRITICAL: Relative paths only. `./image.png` works. Absolute paths break in preview.

- Logo header: `header: '![w:100](./logo.png)'` — hide per slide: `<!-- _header: '' -->`
- Photo bg: `![bg brightness:0.15](https://unsplash.com/photo-ID?w=1400)`
- Split: `![bg right:35% brightness:0.2 blur:3px](url)` or `![bg left:30%](url)`
- CDN logos: `<img src="https://cdn.jsdelivr.net/gh/homarr-labs/dashboard-icons/png/name.png" style="width:200px;" />`
- Centered inline: wrap img in `<div style="display:flex; justify-content:center;">` with border-radius and border

## Dashboard Components

### Metric Card (gradient top border)
Card with `position:relative; overflow:hidden;` and absolute div at top with `background:linear-gradient(90deg, var(--accent), transparent); height:2px;`. Icon + label + big number + trend arrow.

### Status Dots
Inline SVG circles: green (#22c55e) = active, yellow (#f5a623) = learning, red (#ef4444) = paused.
`<svg width="8" height="8" viewBox="0 0 8 8"><circle cx="4" cy="4" r="4" fill="#22c55e"/></svg>`

### Verdict Tags
`<span class="tag" style="background:#22c55e12; color:var(--green); border:1px solid #22c55e22;">Scale</span>`
Swap colors for red (kill) and yellow (review).

### Hover Rows
Wrap content in `<div class="row">` for hover highlight effect.

## SVG Charts

### Line / Area Chart
SVG polyline for the line + polygon with linearGradient fill for area under the line. Add grid lines, dashed target line, circle data points. Use viewBox="0 0 900 240" with preserveAspectRatio="none".

### Pie / Donut Chart
Each segment = separate circle with stroke-dasharray and stroke-dashoffset. Math: circumference = 2*pi*r. For r=110: ~691. Segment = (pct/100)*691. Offsets accumulate negatively. stroke-width controls ring thickness. Always transform="rotate(-90 cx cy)".

### Gauge / Half-Circle Meter
SVG path arc for background + colored value arc. Needle line from center + circle pivot. For scores 0-100. stroke-linecap="round".

### Donut Ring
Single circle stroke-dasharray. circ = 2*pi*r. Offset = circ - (circ * pct/100). For r=74: circ=465. 89%: offset=51.

### Sparkline (inline mini)
`<svg width="50" height="16"><polyline points="0,14 8,12 16,10 24,8 50,2" fill="none" stroke="#22c55e" stroke-width="1.2"/></svg>`

### Stacked Bar
Flex div with colored width-percent segments, border-radius, overflow:hidden.

### Vertical Bar Chart
Flex container align-items:flex-end. Gradient bars: `background:linear-gradient(180deg, var(--accent), #cc5515); border-radius:3px 3px 0 0;`

### Radar / Spider
SVG polygon for hexagonal grid + data shape with fill-opacity:0.1 and stroke outline.

## Interactive Elements

- Collapsible: `<details><summary>Title</summary><p>Content</p></details>`
- Tooltip: `<abbr title="Full text">TERM</abbr>`
- Slider: `<input type="range" style="accent-color:var(--accent);" />`
- Checkbox: `<input type="checkbox" checked style="accent-color:var(--accent);" />`
- Progress: `<progress value="76" max="100" style="accent-color:var(--accent);"></progress>`

## Layout Components

- Before/After Split — two flex panels, border-top red vs green
- Terminal Mockup — traffic light dots + monospace body
- Browser Mockup — dots + URL bar div
- Chat Bubbles — user (left) + agent (right, orange-tinted)
- Flowchart — boxes + SVG arrow connectors
- Timeline — vertical border-left + dot circles
- Card Row — display:flex; gap:14px; with flex:1 children

## SVG Icons

All wrapped in `<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--accent)" stroke-width="1.5">`. Sizes: inline=16, cards=44, features=32.

Dollar: path d="M12 2v20M17 5H9.5a3.5 3.5 0 1 0 0 7h5a3.5 3.5 0 1 1 0 7H6"
Heartbeat: polyline points="22 12 18 12 15 21 9 3 6 12 2 12"
Check (#22c55e): path d="M22 11.08V12a10 10 0 1 1-5.93-9.14" + polyline points="22 4 12 14.01 9 11.01"
Arrow up (#22c55e): polyline points="18 15 12 9 6 15"
Arrow down (#ef4444): polyline points="18 9 12 15 6 9"
X circle (#ef4444): circle cx=12 cy=12 r=10 + two crossing lines
Clock: circle cx=12 cy=12 r=10 + polyline points="12 6 12 12 16 14"
Eye: path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z" + circle cx=12 cy=12 r=3
Lightning: path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"
Warning (#f5a623): triangle path
Search: circle cx=11 cy=11 r=8 + line to corner
Bars: three vertical paths
Users: user silhouette path + circle
Globe: circle + horizontal line + vertical ellipse path
Lock: rect + arch path
Book: two paths for book shape

## Animations (HTML export + preview only)

float: translateY(0) to -8px and back
glow: box-shadow pulse with accent color
blink: border-color toggle for cursors

Stagger with delay: animation: float 4s ease-in-out 0.5s infinite;

## Export

npx @marp-team/marp-cli slides.md --pdf --allow-local-files
npx @marp-team/marp-cli slides.md --pptx --allow-local-files
npx @marp-team/marp-cli slides.md --html --allow-local-files
--pptx-editable needs LibreOffice. Animations + details only in HTML.

## Design Rules

1. One idea per slide. Overflow clips silently.
2. h1 = white. Accent for data highlights only.
3. Body text #999, labels #666. Never darker than #555.
4. Max 6 rows per list slide.
5. Charts over numbers. Mix visual types across slides.
6. Relative paths only for images.
7. Always preview — no overflow warnings in source.
8. Per-slide overrides: _backgroundColor, _header, _paginate, _footer

Custom dimensions: section { width: 540px; height: 720px; } (CSS not size: frontmatter).
Portrait: stack vertically, scale down 15-20%.

---

## Brand Variable System (NEW in v3)

Define brand colors once, retheme the entire deck by changing 3 variables:

```css
:root {
  --brand-primary: #ff6b1a;    /* main CTA, highlights */
  --brand-secondary: #2563eb;  /* secondary actions, links */
  --brand-bg: #000;            /* slide background */
  --brand-surface: #080808;    /* card backgrounds */
  --brand-border: #111;        /* card borders */
  --brand-text: #fff;          /* heading text */
  --brand-body: #999;          /* body text */
  --brand-muted: #555;         /* secondary text */
}
```

To retheme: swap `--brand-primary` and `--brand-bg`. All components use these variables.

### AI Injection Theme

```css
:root {
  --brand-primary: #ff6600;
  --brand-secondary: #c8ff00;
  --brand-bg: #0a0a0a;
  --brand-surface: #111;
  --brand-border: #222;
  --brand-text: #fff;
  --brand-body: #aaa;
  --brand-muted: #666;
}
```

## Master Slide Classes (NEW in v3)

Add `<!-- _class: classname -->` per slide for consistent layouts:

### Title Slide
```markdown
<!-- _class: lead -->
# Main Title
## Subtitle goes here
```

### Section Break
```markdown
<!-- _class: lead -->
<!-- _backgroundColor: var(--brand-primary) -->
# Section Name
```

### Content Slide (default)
Standard left-aligned content with heading + body.

### Two-Column Split
```html
<div style="display:grid; grid-template-columns:1fr 1fr; gap:40px;">
<div>

### Left Column
Content here

</div>
<div>

### Right Column
Content here

</div>
</div>
```

### Three-Column Grid
```html
<div style="display:grid; grid-template-columns:1fr 1fr 1fr; gap:24px;">
```

### 60/40 Image Split
```markdown
![bg right:40% brightness:0.2](image-url)
# Title on the left
Body text with room to breathe
```

### Closing/CTA Slide
```markdown
<!-- _class: lead -->
# Thank You
## Questions? Reach out at **email@example.com**
```

## New Layout Components (NEW in v3)

### Pricing Tier Cards
```html
<div style="display:flex; gap:16px; justify-content:center;">
  <div style="flex:1; background:var(--brand-surface); border:1px solid var(--brand-border); border-radius:12px; padding:24px; text-align:center;">
    <h3 style="color:var(--brand-muted);">FREE</h3>
    <div style="font-size:2.4em; font-weight:800; color:var(--brand-text); margin:8px 0;">$0</div>
    <p style="color:var(--brand-body); font-size:0.75em;">Basic features</p>
  </div>
  <div style="flex:1; background:var(--brand-surface); border:2px solid var(--brand-primary); border-radius:12px; padding:24px; text-align:center; position:relative;">
    <div style="position:absolute; top:-10px; left:50%; transform:translateX(-50%); background:var(--brand-primary); color:#000; font-size:0.5em; padding:2px 12px; border-radius:4px; font-weight:700;">POPULAR</div>
    <h3 style="color:var(--brand-primary);">PRO</h3>
    <div style="font-size:2.4em; font-weight:800; color:var(--brand-text); margin:8px 0;">$29</div>
    <p style="color:var(--brand-body); font-size:0.75em;">All features</p>
  </div>
</div>
```

### Team / Profile Cards
```html
<div style="display:flex; gap:20px; justify-content:center;">
  <div style="text-align:center;">
    <img src="https://i.pravatar.cc/120?u=1" style="width:80px; height:80px; border-radius:50%; border:2px solid var(--brand-primary);" />
    <div style="font-family:'Outfit'; font-weight:700; margin-top:8px; font-size:0.85em;">Name</div>
    <div style="color:var(--brand-muted); font-size:0.65em;">Role</div>
  </div>
</div>
```

### Quote / Testimonial Block
```html
<div style="background:var(--brand-surface); border-left:3px solid var(--brand-primary); border-radius:8px; padding:20px 24px; margin:16px 0;">
  <p style="font-size:1.1em; font-style:italic; color:var(--brand-body); line-height:1.6;">"Quote text goes here. Make it punchy and specific."</p>
  <p style="color:var(--brand-muted); font-size:0.7em; margin-top:12px;">-- Author Name, Title</p>
</div>
```

### Stats Callout Strip (3-4 KPIs)
```html
<div style="display:flex; gap:20px; justify-content:center; margin:20px 0;">
  <div style="text-align:center; flex:1;">
    <div style="font-size:2.6em; font-weight:800; color:var(--brand-primary);">10K+</div>
    <div style="color:var(--brand-muted); font-size:0.7em; text-transform:uppercase; letter-spacing:0.1em;">Users</div>
  </div>
  <div style="text-align:center; flex:1;">
    <div style="font-size:2.6em; font-weight:800; color:var(--brand-secondary);">99.9%</div>
    <div style="color:var(--brand-muted); font-size:0.7em; text-transform:uppercase; letter-spacing:0.1em;">Uptime</div>
  </div>
  <div style="text-align:center; flex:1;">
    <div style="font-size:2.6em; font-weight:800; color:#22c55e;">4.9★</div>
    <div style="color:var(--brand-muted); font-size:0.7em; text-transform:uppercase; letter-spacing:0.1em;">Rating</div>
  </div>
</div>
```

### Process Flow (Horizontal Steps)
```html
<div style="display:flex; align-items:center; gap:8px; justify-content:center;">
  <div style="background:var(--brand-primary); color:#000; width:36px; height:36px; border-radius:50%; display:flex; align-items:center; justify-content:center; font-weight:800;">1</div>
  <div style="color:var(--brand-body); font-size:0.8em;">Research</div>
  <div style="color:var(--brand-muted);">→</div>
  <div style="background:var(--brand-secondary); color:#fff; width:36px; height:36px; border-radius:50%; display:flex; align-items:center; justify-content:center; font-weight:800;">2</div>
  <div style="color:var(--brand-body); font-size:0.8em;">Design</div>
  <div style="color:var(--brand-muted);">→</div>
  <div style="background:#22c55e; color:#000; width:36px; height:36px; border-radius:50%; display:flex; align-items:center; justify-content:center; font-weight:800;">3</div>
  <div style="color:var(--brand-body); font-size:0.8em;">Ship</div>
</div>
```

### SWOT Matrix
```html
<div style="display:grid; grid-template-columns:1fr 1fr; gap:12px;">
  <div style="background:#22c55e10; border:1px solid #22c55e33; border-radius:8px; padding:16px;">
    <div style="color:#22c55e; font-weight:700; font-size:0.8em; margin-bottom:8px;">STRENGTHS</div>
    <ul style="color:var(--brand-body); font-size:0.7em; margin:0; padding-left:16px;"><li>Item</li></ul>
  </div>
  <div style="background:#ef444410; border:1px solid #ef444433; border-radius:8px; padding:16px;">
    <div style="color:#ef4444; font-weight:700; font-size:0.8em; margin-bottom:8px;">WEAKNESSES</div>
    <ul style="color:var(--brand-body); font-size:0.7em; margin:0; padding-left:16px;"><li>Item</li></ul>
  </div>
  <div style="background:#3b82f610; border:1px solid #3b82f633; border-radius:8px; padding:16px;">
    <div style="color:#3b82f6; font-weight:700; font-size:0.8em; margin-bottom:8px;">OPPORTUNITIES</div>
    <ul style="color:var(--brand-body); font-size:0.7em; margin:0; padding-left:16px;"><li>Item</li></ul>
  </div>
  <div style="background:#f59e0b10; border:1px solid #f59e0b33; border-radius:8px; padding:16px;">
    <div style="color:#f59e0b; font-weight:700; font-size:0.8em; margin-bottom:8px;">THREATS</div>
    <ul style="color:var(--brand-body); font-size:0.7em; margin:0; padding-left:16px;"><li>Item</li></ul>
  </div>
</div>
```

## Advanced MARP Directives (NEW in v3)

Directives most people miss:

| Directive | What it does |
|-----------|-------------|
| `<!-- _paginate: skip -->` | Hide page number on title slides |
| `<!-- _paginate: hold -->` | Keep same page number (for continuation slides) |
| `<!-- _header: '' -->` | Hide header on specific slide |
| `<!-- _footer: 'Custom footer' -->` | Per-slide footer override |
| `<!-- _backgroundColor: #1a1a2e -->` | Per-slide background color |
| `<!-- _backgroundImage: url() -->` | Full-bleed background image |
| `<!-- _backgroundSize: cover -->` | Background sizing |
| `<!-- _backgroundPosition: center -->` | Background alignment |
| `<!-- _color: #fff -->` | Override all text color for slide |
| `<!-- _class: lead -->` | Center-aligned layout |
| `@auto-scaling true` | Auto-fit text to slide (frontmatter) |
| `<style scoped>` | Styles that only affect current slide |

## Additional Font Pairings (NEW in v3)

| Heading | Body | Use |
|---|---|---|
| Inter 800 | Inter 300 | Clean SaaS, tech |
| Poppins 700 | Poppins 300 | Friendly, startup |
| Playfair Display 700 | Lato 300 | Elegant, editorial |
| Montserrat 800 | Open Sans 300 | Corporate, enterprise |
| Bebas Neue 400 | Source Sans 3 300 | Bold, impact |

## QR Code Slide (Closing)

Use a QR code API for closing slides:
```html
<div style="text-align:center;">
  <img src="https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=https://your-link.com" style="border-radius:8px;" />
  <p style="color:var(--brand-muted); font-size:0.7em; margin-top:8px;">Scan to visit</p>
</div>
```

## Gradient Mesh Background

For slides that need more visual punch:
```html
<style scoped>
section {
  background: radial-gradient(ellipse at 20% 80%, #1a0a2e 0%, transparent 50%),
              radial-gradient(ellipse at 80% 20%, #0a1a2e 0%, transparent 50%),
              #000;
}
</style>
```
