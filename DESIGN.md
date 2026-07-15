# 90s Grunge Rock — Portfolio Style Reference
> photocopied flyers stapled to telephone poles outside Seattle venues — a raw, gritty, anti-design portfolio system where digital precision is intentionally broken.

**Theme:** dark / alternative  
**Version:** 1.0 (Portfolio Zine Edition)

Before grunge had a name, it had a look — hand-scrawled setlists, album art that looked like it survived a basement flood, and photocopied gig posters. This portfolio system operates on the anti-corporate visual language of the early 1990s alternative scene. It rejects slick grids and smooth gradients. 

Typography behaves like a typewriter slamming ink into raw paper (`Courier New`), layouts are treated like a physical punk zine, and project media is disciplined through heavy xerox and noise artifacts. It wasn't designed. It was assembled.

---

## Tokens — Colors

| Name | Value | Token | Role |
|------|-------|-------|------|
| Faded Black | `#2E2E2E` | `--color-faded-black` | Primary page canvas, dark textured surfaces, preventing clinical digital blacks |
| Off-White | `#E9E1D4` | `--color-off-white` | Textured paper background for case studies, metadata cards, and high-contrast text |
| Dirty Yellow | `#B5A642` | `--color-dirty-yellow` | Primary interactive highlights, hover fills, active project tags |
| Muted Red | `#8C2727` | `--color-muted-red` | Project category indicators, structural borders, danger states |
| Olive Drab | `#6B8E23` | `--color-olive-drab` | Decorative elements, inactive tags, background layers |
| Concrete Grey| `#7A7A7A` | `--color-concrete-grey`| Timestamps, secondary metadata, borders when contrast needs to drop |

---

## Tokens — Typography

### Courier New — The Voice of the Underground
The only font family permitted. A raw monospace typewriter aesthetic that communicates raw intent. Readability is pushed to its limits through tight display tracking and intentional column bleeding. · `--font-grunge`

### Type Scale

| Role | Size | Line Height | Letter Spacing | Token | Context |
|------|------|-------------|----------------|-------|---------|
| caption | 0.875rem | 1.3 | 0.5px | `--text-caption` | Project metadata, tags, small timestamps |
| body | 1rem | 1.6 | 0 | `--text-body` | Case study text, about me intro (max 72ch) |
| subheading | 1.5rem | 1.3 | -0.5px | `--text-subheading` | Project roles, tool stack titles, section markers |
| heading | 2.25rem | 1.1 | -1px | `--text-heading` | Standard section titles, back-to-top links |
| display | clamp(2.5rem, 5vw, 4rem) | 1.0 | -2px | `--text-display` | Monolithic project titles, landing hero text |

---

## Tokens — Layout & Spacing

### Spacing Scale
Based on a balanced but raw 8px rhythm unit.
*   `--spacing-08`: 8px
*   `--spacing-16`: 16px
*   `--spacing-24`: 24px
*   `--spacing-48`: 48px
*   `--spacing-gap`: clamp(4rem, 8vw, 8rem) (Extreme vertical breathing room between project blocks)

### Layout Principles
*   **Max Width:** 1280px centered content container with 1.5rem side padding.
*   **The Anti-Grid:** Strictly **no** equal-width multi-column layouts. Projects are presented asymmetrically (e.g., Project 01 takes 7 columns starting from the left; Project 02 takes 5 columns pushed heavily to the right).
*   **Collapsing Behavior:** All asymmetric layouts collapse into a singular vertical stream below 768px with absolute zero horizontal overflow.

---

## Components

### 1. Zine Header (Navigation)
*   **Structure:** No persistent blurred backgrounds. A flat, solid `--color-faded-black` surface bar bounded by a 2px raw border. 
*   **Content:** Left-aligned raw text name placeholder. Right-aligned utilities: `[ WORK ]`, `[ UNDERGROUND/ABOUT ]`, `[ CONNECT ]`. Text weights switch to 700 when an index is active.

### 2. Chaotic Hero Landing
*   An asymmetric explosion of type and texture. The main title (`--text-display`) is stacked vertically like a wheat-pasted street poster. 
*   Includes raw decorative primitives like inline SVGs simulating duct-tape overlays or torn paper margins holding the introductory bio.

### 3. The Xerox Media Container (Project Showcase)
*   **The Look:** Portfolio screenshots must not look clean. All preview media applies a default style: `filter: grayscale(100%) contrast(140%) brightness(90%)` layered with a CSS noise overlay to mimic a bad photocopier.
*   **The Interaction:** On hover, the image undergoes a raw 200ms transition: the grayscale filter drops to 0%, the contrast normalizes, and a slight physical tilt (`transform: rotate(-1deg)`) occurs to simulate a loose poster.

### 4. Raw Utility Buttons
*   **Primary Button:** 8px (`0.5rem`) sharp corner radius. Solid `--color-dirty-yellow` or `--color-faded-black` fill with high contrast text. 
*   **Hover/Active:** On hover, shifts color and moves down/right 2px (`transform: translate(2px, 2px)`) with an immediate solid box-shadow change, producing a brutalist, clicky interaction. No fluid gradients or outer glows allowed.

---

## Do's and Don'ts

### Do
*   **Do** embrace chaotic, layered layout composition. Let elements overlap slightly using controlled z-indexes (`base: 0`, `sticky: 100`, `overlay: 200`).
*   **Do** keep text line-lengths for project explanations strictly under `72ch` to preserve typewriter readability.
*   **Do** use standard keyboard primitives (`[x]`, `-->`, `*`, `===`) for decorative dividers and list pointers instead of clean icon fonts.
*   **Do** treat your portfolio like a physical, self-published music zine.

### Don't
*   **Don't** use pure digital black (`#000000`). Always use `--color-faded-black` (`#2E2E2E`) to maintain the characteristic ink-washed tone.
*   **Don't** introduce smooth modern sans-serifs (Inter, Roboto) or elegant serifs. `Courier New` is the absolute rule.
*   **Don't** build a 3-column equal grid for your projects. It kills the alternative anti-design posture.
*   **Don't** use standard AI copy catchphrases ("Elevate your business", "Seamless next-gen portfolios"). Keep project copy direct, clinical, or raw.

---

## Quick Start Technical Specs

### Raw CSS Variables
```css
:root {
  /* Grunge Alternative Palette */
  --color-faded-black: #2E2E2E;
  --color-dirty-yellow: #B5A642;
  --color-muted-red: #8C2727;
  --color-off-white: #E9E1D4;
  --color-olive-drab: #6B8E23;
  --color-concrete-grey: #7A7A7A;

  /* Typography Settings */
  --font-grunge: 'Courier New', Courier, monospace;
  
  /* Core Spacing & Shapes */
  --radius-grunge: 8px;
  --transition-grunge: 200ms cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Photocopied/Xerox Portfolio Image Base Rule */
.portfolio-media-container {
  background: var(--color-faded-black);
  border: 2px solid var(--color-faded-black);
  position: relative;
  overflow: hidden;
}

.portfolio-media-container img {
  filter: grayscale(100%) contrast(140%) brightness(95%);
  transition: filter var(--transition-grunge), transform var(--transition-grunge);
}

.portfolio-media-container:hover img {
  filter: grayscale(0%) contrast(100%) brightness(100%);
  transform: scale(1.02) rotate(-1deg);
}

/* Brutalist Tactile Button */
.btn-grunge {
  font-family: var(--font-grunge);
  font-weight: 700;
  background-color: var(--color-dirty-yellow);
  color: var(--color-faded-black);
  border: 2px solid var(--color-faded-black);
  border-radius: var(--radius-grunge);
  padding: 12px 24px;
  box-shadow: 4px 4px 0px 0px var(--color-faded-black);
  transition: transform 100ms ease;
}

.btn-grunge:active {
  transform: translate(4px, 4px);
  box-shadow: 0px 0px 0px 0px var(--color-faded-black);
}