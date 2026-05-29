# Lecture Pages — Design Reference
> ליטל אפרים | חוסן והשראה — Lital Efraim personal brand site

---

## 1. Brand Identity

| Attribute | Value |
|---|---|
| Brand name | ליטל אפרים |
| Page title | חוסן והשראה |
| Language | Hebrew primary, English secondary |
| Directionality | RTL (`dir="rtl"`, `lang="he"`) |
| Themes | Dark (default) + Light |
| Tone | Intimate, resilient, professional |

---

## 2. Color Tokens

### Dark Theme (lectures.html)

| Token | Hex | Role |
|---|---|---|
| `--base` | `#0F172A` | Page background |
| `--surface` | `#131E35` | Card / elevated surface |
| `--surface-2` | `#131E35` | Hero gradient end |
| `--wine` | `#9B2A40` | Primary brand color |
| `--wine-vivid` | `#C03858` | Hover / emphasis |
| `--wine-rose` | `#E05878` | Headlines, active states |
| `--wine-deep` | `#701828` | Deep shadow / border |
| `--beige` | `#C8A87A` | Secondary accent |
| `--beige-light` | `#DFC4A0` | CTA buttons, highlights |
| `--beige-pale` | `#EFD8B5` | Subtle text, audience labels |
| `--white` | `#F1F5F9` | Body text on dark |
| `--gray` | `#94A3B8` | Secondary text |
| `--gray-dim` | `#475569` | Muted text, dividers |

### Light Theme (lectures-light.html)

| Token | Hex | Role |
|---|---|---|
| `--base` | `#FAF7F2` | Page background (warm off-white) |
| `--surface` | `#F0E9DF` | Card / elevated surface |
| `--surface-2` | `#FCEEF0` | Hero blush tint |
| `--wine` | `#6B1929` | Primary brand color (deeper) |
| `--wine-vivid` | `#8B2A3A` | Hover / emphasis |
| `--wine-rose` | `#A03050` | Headlines, active states |
| `--wine-deep` | `#400C18` | Deep shadow |
| `--beige` | `#9B7345` | Secondary accent |
| `--beige-light` | `#C8A87A` | CTA buttons, highlights |
| `--beige-pale` | `#EFD8B5` | Audience labels |
| `--white` | `#FFFFFF` | Pure white |
| `--text` | `#0F172A` | Primary body text |
| `--gray` | `#374151` | Secondary text |
| `--gray-dim` | `#6B7280` | Muted text |

---

## 3. Typography

| Use | Font | Weight | Notes |
|---|---|---|---|
| Hebrew body | Heebo | 300, 400, 500, 700, 900 | Default font |
| Hebrew headings | Alef | 400, 700 | Applied to h1, quote, contact h2 via `.lang-he` |
| English body | Inter | 300, 400, 500, 600, 700, 900 | Active when `.lang-en` |
| Nav links | Heebo / Inter | 500 | 0.875rem, letter-spacing 0.04em |
| Eyebrow labels | Heebo / Inter | 700 | 0.68rem, 0.28em tracking, uppercase |
| H1 | Alef | 900 | `clamp(2.5rem, 5.5vw, 4rem)`, color: `--wine-rose` |
| Lead paragraph | Heebo | 400 | 1.08rem, line-height 1.85 |
| Intro paragraph | Alef | 400 | 0.92rem, line-height 1.95, color: `--gray-dim` |
| Card title | Heebo | 700 | 1.2rem, line-height 1.4 |
| Card description | Heebo | 400 | 0.875rem, line-height 1.85 |
| Quote text | Alef | 300 | `clamp(1.3rem, 2.8vw, 2rem)`, line-height 1.6 |

---

## 4. Layout Grid

- Max content width: `1100px`, centered with `margin: 0 auto`
- Page horizontal padding: `2rem`
- Main padding-top: `5rem`
- Lectures grid: `repeat(auto-fill, minmax(330px, 1fr))`, gap `1.75rem`
- Hero inner: two-column `1fr auto` grid, gap `3rem`, aligned center

---

## 5. Component Specs

### Navigation Bar

- Fixed, full-width, `z-index: 1000`
- Background: `rgba(15,23,42,0.92)` + `backdrop-filter: blur(20px) saturate(1.4)`
- Border-bottom: `1px solid rgba(155,42,64,0.22)`
- Padding: `0.75rem 2.5rem`
- Logo height: `52px`
- Active link: `--wine-rose` color, bottom underline scales to full width
- Language toggle: pill buttons (`HE` / `EN`), active state filled with `--wine`
- Mobile: hamburger at `768px` breakpoint, fullscreen overlay menu

---

### Page Hero Banner

- Min-height: `62vh`, padding `8rem 2rem 4rem`
- Background: `linear-gradient(160deg, var(--base) 0%, var(--surface-2) 100%)`
- Animated grid overlay: wine-tinted lines, `52px × 52px`, `gridPulse` animation (14s)
- Radial glow: wine at 30% 55%, `glowPulse` animation (8s)
- Watermark logo: `190px`, opacity `0.14`, desaturated, subtle hover to `0.20`
- Structure: eyebrow label → H1 → lead text → intro paragraph

---

### Lecture Card (`.lec-card`)

- Padding: `2.25rem 2rem`, border-radius: `16px`
- Background: `rgba(255,255,255,0.02)`
- Border: `1px solid rgba(155,42,64,0.16)`
- Top accent line: wine gradient, appears on hover via opacity
- Hover state: `translateY(-5px)`, wine-tinted background `rgba(155,42,64,0.04)`, box-shadow with depth
- Internal structure:
  - `.lec-num` — number badge, 0.63rem, `--wine-vivid`, tracked uppercase
  - `.lec-title` — 1.2rem, 700 weight, `--white`
  - `.lec-desc` — 0.875rem, `--gray`, flex-grows to fill space
  - `.lec-audience` — 0.76rem, `--beige-pale`, separated by top border
  - `.lec-btns` — flex row of CTA buttons

---

### CTA Buttons

| Variant | Style |
|---|---|
| Default (`.lec-btn`) | Transparent, beige border `rgba(200,168,122,0.4)`, beige text |
| Default hover | `rgba(200,168,122,0.12)` fill, stronger border, `translateY(-1px)` |
| WhatsApp (`.lec-btn-wa`) | Gradient `#25D366 → #128C7E`, white text |
| WhatsApp hover | `#1ebe5d`, green glow shadow |
| Contact primary | Gradient `--beige-light → --beige`, `--base` text, pill `border-radius: 50px` |
| LinkedIn | `#0A66C2` fill, white text |

---

### Quote Band

- Padding: `4rem 2rem`, centered
- Background: subtle wine-beige gradient strip
- Top + bottom borders: `1px solid rgba(155,42,64,0.14)`
- Quote text: Alef 300, `clamp(1.3rem, 2.8vw, 2rem)`, `--beige-pale`
- Emphasis (`em`): `--wine-rose`, non-italic, 700 weight

---

### Contact Section

- Background: `linear-gradient(180deg, var(--surface-2) 0%, var(--base) 100%)`
- Padding: `6rem 2rem`, centered
- H2: gradient text clip `--wine-rose → --wine-vivid`, 900 weight
- Description: `--gray`, 1.05rem, line-height 1.8
- Buttons: flex row, centered, wrapping

---

### Footer

- Padding: `1.75rem 2rem`, centered
- Border-top: `1px solid rgba(155,42,64,0.14)`
- Color: `--gray-dim`, 0.8rem
- Brand emphasis in `em`: `--wine-vivid`

---

## 6. Motion & Animation

| Animation | Duration | Easing | Use |
|---|---|---|---|
| `gridPulse` | 14s | ease-in-out, infinite | Hero grid overlay drift |
| `glowPulse` | 8s | ease-in-out, infinite | Hero radial glow breathe |
| `.fade-up` | 0.65s | ease | Scroll-in for cards and sections |
| Card hover lift | 0.35s | ease | `translateY(-5px)` on `.lec-card` |
| Nav link underline | 0.3s | default | `scaleX(0 → 1)` on hover/active |
| CTA button hover | 0.3s | default | `translateY(-1px)` + glow shadow |

---

## 7. Scrollbar

- Width: `5px`
- Track: `--base`
- Thumb: `rgba(155,42,64,0.45)`, `border-radius: 3px`
- Thumb hover: `--wine-vivid`

---

## 8. Responsive Breakpoints

| Breakpoint | Behavior |
|---|---|
| `≤ 768px` | Nav collapses to hamburger; grid stacks to single column |
| Hero grid | Collapses to single column at mobile, logo may be hidden |

---

## 9. Internationalization

- Default language: Hebrew (`lang="he"`, `dir="rtl"`)
- English toggle available; shows "Coming Soon" state on lectures page
- `body.lang-he` applies Alef font to specific heading and body selectors
- `body.lang-en` switches to Inter across the board
- All structural CSS uses logical properties (`inset-inline`, `inset-inline-end`) for RTL/LTR compatibility

---

## 10. Theme Switching

- Preference stored in `localStorage` key `theme` (`'dark'` or absent for light)
- Each page pair redirects on load: `lectures.html` (dark) ↔ `lectures-light.html` (light)
- Toggle rendered as a small pill link in the nav area

---

## 11. Lecture Content Structure (per card)

Each lecture card holds:
1. Ordinal number (e.g., `01 —`)
2. Title (Hebrew)
3. Description (2–4 sentences)
4. Target audience line (`קהל יעד:`)
5. Action buttons — "פרטים נוספים" (details) + WhatsApp CTA

---

## 12. External Resources

| Resource | URL |
|---|---|
| Google Fonts | Heebo, Alef, Inter, Rubik via fonts.googleapis.com |
| WhatsApp CTA | `https://wa.me/972XXXXXXXXX` with pre-filled message |
| LinkedIn | `https://linkedin.com/in/litalefraim` |

---

*Confidence: 0.94*

**Key Caveats & Potential Biases:**
- WhatsApp number is masked above — use the actual number from the HTML files.
- The light theme applies slightly different wine shades (deeper/more saturated) vs. the dark theme — not interchangeable token-for-token.
- ❌ Rubik font is imported on the home page (`index.html`) but not visibly used in lectures pages; confirm if intentional or a candidate for removal.
