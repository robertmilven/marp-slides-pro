# MARP Slides Pro

Professional presentation decks with AI. Fork of [marp-slides](https://github.com/robonuggets/marp-slides) by RoboNuggets, enhanced by AI Injection.

Give Claude Code a topic and it builds a polished MARP deck with SVG charts, dashboard components, brand theming, and 30+ layout templates. The 22 example decks teach composition, not just components.

## Improvements Over Original

| Feature | Original v2 | Pro v3 |
|---------|-------------|--------|
| Layout templates | 7 components | 15+ (pricing cards, team cards, quotes, SWOT, process flows, stats strips) |
| Brand system | Hardcoded colors | CSS variable system - change 3 vars to retheme |
| Themes | AI Injection not included | AI Injection theme built in |
| Font pairings | 6 tested | 11 tested (added Inter, Poppins, Playfair, Montserrat, Bebas Neue) |
| Slide classes | Basic | Master slide classes (title, section break, content, closing, splits) |
| Directives | Basic | Full directive reference (paginate skip/hold, scoped styles, auto-scaling) |
| Extras | None | QR code slides, gradient mesh backgrounds |

## Quick Start

### 1. Clone

```bash
git clone https://github.com/robertmilven/marp-slides-pro
```

### 2. Add to Claude Code

```bash
claude --add-dir ./marp-slides-pro
```

Or copy into your project's `.claude/skills/` directory.

### 3. VS Code Extension

Install **Marp for VS Code** and enable:

```json
{
  "markdown.marp.enableHtml": true,
  "markdown.marp.allowLocalFiles": true
}
```

### 4. Generate

```
Create a MARP presentation reviewing Q1 sales. Dark theme, stat cards, bar chart.
```

```
Build an AI Injection branded deck about our video pipeline. Include process flow and team cards.
```

```
Make a pitch deck with pricing tiers, testimonials, and a SWOT analysis.
```

## What's Included

```
marp-slides-pro/
├── SKILL.md              # The skill - rules, components, design system, brand variables
└── examples/             # 22 curated reference decks
    ├── marp_facebook-ads.md    # Data dashboard with SVG charts
    ├── marp_coffee.md          # Editorial lifestyle deck
    ├── marp_fitness.md         # Health tracking dashboard
    └── ... 19 more examples
```

## New in v3

### Brand Variable System
Define your brand colors once, every component uses them:
```css
:root {
  --brand-primary: #ff6600;    /* AI Injection orange */
  --brand-secondary: #c8ff00;  /* AI Injection green */
  --brand-bg: #0a0a0a;
}
```

### New Layout Components
- Pricing tier cards (free/pro/enterprise)
- Team/profile cards with avatar circles
- Quote/testimonial blocks
- Stats callout strips (3-4 KPIs in a row)
- Horizontal process flows (numbered steps)
- SWOT matrix (2x2 color-coded grid)
- Two-column and three-column grids
- 60/40 image splits
- QR code closing slides
- Gradient mesh backgrounds

### Master Slide Classes
Consistent layouts per slide type: `lead`, `section-break`, `content`, `closing`

### Advanced Directives
Full reference for `_paginate: skip/hold`, scoped styles, auto-scaling, per-slide overrides.

## All Features

- **Dark and light themes** with 11 tested font pairings
- **Brand variable system** - retheme entire deck by changing 3 CSS vars
- **SVG charts** - line/area, donut/pie, gauges, sparklines, bar, radar
- **Dashboard components** - metric cards, status dots, verdict tags, hover rows
- **Layout components** - pricing cards, team cards, quotes, SWOT, process flows, stats strips, timelines, flowcharts, terminal/browser mockups, chat bubbles
- **Interactive elements** - collapsible sections, tooltips, progress bars, sliders
- **SVG icon library** - 16+ inline icons
- **Master slide classes** - title, section break, content, closing, splits
- **QR code generation** for closing slides
- **Gradient mesh backgrounds** for visual punch

## Export

```bash
npx @marp-team/marp-cli slides.md --pdf --allow-local-files
npx @marp-team/marp-cli slides.md --pptx --allow-local-files
npx @marp-team/marp-cli slides.md --html --allow-local-files
```

## Credits

- Original skill by [RoboNuggets](https://github.com/robonuggets/marp-slides)
- Pro features and brand system by [AI Injection](https://github.com/robertmilven)

## License

MIT
