# Wedding Site Skill
## Inspired by cordially.io — editorial, image-light, typography-forward

---

## WHEN TO USE THIS SKILL
Use this skill whenever building a single-page wedding website in HTML/CSS/JS. It encodes the design language, typography system, section vocabulary, and copy conventions extracted from Cordially.io's demo — the gold standard for modern editorial wedding sites.

---

## CORE DESIGN PHILOSOPHY

Cordially builds beautiful wedding sites **without relying heavily on photos**. The design earns its elegance through:

- **Typography as the hero** — big, expressive, well-spaced type does the emotional work that photos usually do
- **Generous whitespace** — sections breathe; nothing is cramped
- **Lowercase editorial voice** — section labels and nav links are lowercase (`our story`, `june 18, 2027`) giving it an intimate, non-corporate feel
- **Restrained color** — near-monochrome palette (cream, warm off-white, dark charcoal, single muted accent). No gradients. No color overload.
- **Full-width thinking** — sections often span full viewport width with centered max-width content containers (~720px–900px)
- **Story-first structure** — the site reads like a narrative, not a flyer

---

## TYPOGRAPHY SYSTEM

### Font Stack (Google Fonts — always load via `<link>` in `<head>`)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Jost:wght@300;400;500&display=swap" rel="stylesheet">
```

| Role | Font | Weight | Style |
|------|------|--------|-------|
| Hero names / display | `Cormorant Garamond` | 300–400 | Normal or italic |
| Chapter headings | `Cormorant Garamond` | 400 | Italic |
| Body / story text | `Cormorant Garamond` | 300 | Normal |
| Nav links, labels, badges | `Jost` | 300–400 | Uppercase or lowercase |
| Section eyebrow labels | `Jost` | 300 | Uppercase, wide letter-spacing (~0.2em) |
| Countdown, dates | `Jost` | 300 | Normal |
| Buttons | `Jost` | 400 | Normal, slight letter-spacing |

**Why this stack:** Cormorant Garamond is a free Google Font that closely matches the refined editorial serif seen on Cordially. Jost provides the clean sans-serif contrast for UI elements. Together they replicate Cordially's warm-classical aesthetic.

### Type Scale

```css
:root {
  --text-hero: clamp(3.5rem, 10vw, 8rem);      /* Couple names */
  --text-display: clamp(2rem, 5vw, 3.5rem);     /* Section titles */
  --text-chapter: clamp(1.4rem, 3vw, 2rem);     /* Chapter / card headings */
  --text-body: clamp(1rem, 1.5vw, 1.15rem);     /* Story / paragraph text */
  --text-label: 0.75rem;                         /* Eyebrow labels, nav */
  --text-button: 0.85rem;                        /* CTA buttons */

  --leading-tight: 1.1;
  --leading-body: 1.8;
  --leading-display: 1.2;

  --tracking-wide: 0.15em;                       /* Labels */
  --tracking-hero: -0.02em;                      /* Large display text */
}
```

---

## COLOR PALETTE

```css
:root {
  /* Base */
  --color-bg: #FAF8F5;           /* Warm off-white — main background */
  --color-bg-alt: #F2EDE6;       /* Slightly warmer — alternate section bg */
  --color-surface: #FFFFFF;      /* Cards, overlays */

  /* Text */
  --color-text-primary: #1C1A18;  /* Near-black — headings */
  --color-text-body: #3D3A36;     /* Dark warm grey — body copy */
  --color-text-muted: #9A9189;    /* Muted — labels, captions */

  /* Accent — pick ONE per wedding, based on couple's palette */
  --color-accent: #B5936A;        /* Default: warm gold/champagne */
  /* Other options: */
  /* --color-accent: #8FA68E;  Sage green */
  /* --color-accent: #C4A0A0;  Dusty rose */
  /* --color-accent: #7A8FA6;  Slate blue */

  /* Borders */
  --color-border: #E2DDD6;        /* Subtle dividers */
}
```

---

## LAYOUT SYSTEM

```css
:root {
  --container-max: 860px;
  --container-wide: 1100px;
  --section-padding-y: clamp(5rem, 10vw, 9rem);
  --section-padding-x: clamp(1.5rem, 5vw, 3rem);
  --gap-sm: 1rem;
  --gap-md: 2rem;
  --gap-lg: 4rem;
}

.container {
  max-width: var(--container-max);
  margin: 0 auto;
  padding: 0 var(--section-padding-x);
}
```

---

## SECTION VOCABULARY

### 1. Hero
- Full viewport height (`100svh`)
- Centered content: eyebrow label → couple names → date → scripture/quote → scroll cue
- Eyebrow label: `Jost 300, 0.75rem, letter-spacing: 0.2em, uppercase, color: muted`
- Couple names: `Cormorant Garamond 300, var(--text-hero), letter-spacing: -0.02em`
- No hero image → use solid `var(--color-bg)`. Never use a gradient as photo substitute.
- Scroll cue: small Jost text + thin animated chevron or line

### 2. Our Story
- Eyebrow sentence: lowercase, e.g. `"thank god for meetings after church..."`
- Structured as chapters if long; single narrative if short
- Chapter label: `Jost 300, uppercase, 0.2em tracking, muted color`
- Chapter heading: `Cormorant Garamond italic, var(--text-chapter)`
- Body: `Cormorant Garamond 300, var(--text-body), line-height: 1.8`
- Image-light: use thin decorative `<hr>` dividers or large italic pull-quotes between chapters

### 3. Schedule
- Eyebrow: `"so please join us..."`
- Date large in Cormorant (~3rem), centered
- Countdown timer: Jost 300, beneath date
- Venue: name in Cormorant, address + map link in Jost 300 small (text link, not button)
- Event cards: thin top border in accent color

### 4. Tidbits / Details
- Eyebrow: `"a few things to know..."`
- Card grid: 2–3 col desktop, 1 col mobile
- Each card: `2px solid var(--color-accent)` top border, title in Cormorant italic, text in Jost 300

### 5. Gifts
- Tone: `"your presence is the greatest gift"` opening line
- Payment details in subtly bordered `<div>` — `border: 1px solid var(--color-border); padding: 1.5rem`
- Account numbers get inline clipboard copy button (SVG icon)

### 6. FAQ / Q&A
- Eyebrow: `"questions and answers"`
- Accordion: question in Jost 400, answer in Cormorant Garamond 300
- Thin border separators, no section background color

### 7. Faith / Gospel (optional)
- Soft, non-intrusive section
- Opening line in italic Cormorant
- Full prayer text inside an expandable accordion

### 8. Footer
- Large italic Cormorant closing quote
- Couple names + date below in small Jost muted
- No heavy footer bar — whitespace and text only

---

## COPY CONVENTIONS

| Element | Convention | Example |
|---------|-----------|---------|
| Section eyebrows | Lowercase full sentence | `"you're invited to celebrate..."` |
| Nav links | Lowercase | `our story`, `schedule`, `gifts` |
| Dates | Written out | `june 4, 2026` not `Jun 4th` |
| CTA buttons | Sentence case | `Share your photos` |
| Section intros | One warm sentence | `"The people and practical details..."` |

---

## IMAGE-LIGHT STRATEGIES

1. **Large italic pull-quotes** — Cormorant italic ~2.5rem, centered, generous padding
2. **Thin decorative rules** — `border-top: 1px solid var(--color-border); width: 60px; margin: 2rem auto`
3. **Oversized initials/date** — ~15vw Cormorant, `opacity: 0.06`, as background typographic element
4. **SVG botanical dividers** — simple leaf/branch inline SVGs between sections, no external images
5. **Section bg alternation** — alternate `--color-bg` and `--color-bg-alt` for rhythm without images

---

## ANIMATIONS & INTERACTIONS

```css
/* Fade-up on scroll via IntersectionObserver */
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

- Nav: hide on scroll down, show on scroll up (`transform: translateY(-100%)`)
- Accordion: `max-height` transition, no JS libraries
- Countdown: `setInterval` every second, Jost font, no border boxes

---

## NAV PATTERN

```html
<nav class="site-nav">
  <div class="nav-brand">D & K</div>
  <ul class="nav-links">
    <li><a href="#story">our story</a></li>
    <li><a href="#schedule">schedule</a></li>
    <li><a href="#gifts">gifts</a></li>
    <li><a href="#faq">faq</a></li>
  </ul>
  <button class="nav-hamburger" aria-label="Menu">&#9776;</button>
</nav>
```

```css
.site-nav {
  position: fixed; top: 0; width: 100%; z-index: 100;
  padding: 1.25rem var(--section-padding-x);
  display: flex; align-items: center; justify-content: space-between;
  background: rgba(250, 248, 245, 0.92);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid var(--color-border);
  transition: transform 0.3s ease;
  font-family: 'Jost', sans-serif;
  font-size: 0.75rem;
  letter-spacing: 0.15em;
}
.site-nav.hidden { transform: translateY(-100%); }
```

---

## CHECKLIST BEFORE OUTPUT

- [ ] Google Fonts `<link>` in `<head>` (Cormorant Garamond + Jost)
- [ ] All CSS custom properties in `:root`
- [ ] Nav links lowercase, hide-on-scroll behavior
- [ ] Mobile hamburger menu
- [ ] Section eyebrow labels styled correctly
- [ ] No `font-weight: 700` anywhere — this is a light-weight design
- [ ] Countdown timer wired up
- [ ] Account numbers have copy-to-clipboard
- [ ] Scroll-reveal `.reveal` class + IntersectionObserver
- [ ] Image placeholders use warm CSS backgrounds, not grey boxes
- [ ] Footer has closing quote in large italic Cormorant
