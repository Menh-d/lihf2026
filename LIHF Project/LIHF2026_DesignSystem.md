# LIHF 2026 — Design System & UX/UI Plan
> Reference document for visual design and interaction architecture

---

## 🎨 Brand Identity & Color System

### Primary Palette
```
Gold (Primary)     #F5C400   ████
Bright Yellow      #FFD700   ████  (hover states, highlights)
Pure Black         #000000   ████  (hero bg)
Deep Black         #0A0A0A   ████  (main bg)
Dark Surface       #111111   ████  (section bg)
Card Surface       #1A1A1A   ████  (cards, panels)
Border Grey        #2A2A2A   ████  (dividers)
Text White         #FFFFFF   ████
Text Muted         #AAAAAA   ████
Text Dim           #666666   ████
```

### Usage Rules
- **Gold** → Headlines, CTA buttons, stats, icon accents, borders on key cards
- **Black/Dark** → All backgrounds (never white background)
- **White** → Body text, subheadings
- **Muted grey** → Supporting text, labels
- **Gold gradient** → `linear-gradient(135deg, #F5C400, #FF8C00)` for hero elements

---

## 🔤 Typography System

### Font Stack
```
Display (Hero)   → "Bebas Neue" — bold, condensed, impactful
Heading          → "Space Grotesk" Bold (700)
Subheading       → "Space Grotesk" SemiBold (600)
Body             → "Space Grotesk" Regular (400)
Label / Tag      → "Oswald" SemiBold, ALL CAPS
Accent Number    → "Bebas Neue" — for large stat numbers
```

### Size Scale
```
Hero Title       → 96–120px / clamp(64px, 10vw, 120px)
Section Title    → 48–64px
Card Title       → 24–32px
Body Text        → 16–18px
Label/Tag        → 11–13px, letter-spacing: 0.15em
Stat Number      → 72–96px (Bebas Neue)
```

### Rules
- ALL CAPS on section labels and tags
- Letter-spacing: `0.1–0.2em` on labels
- Never mix more than 2 fonts per section
- Gold color reserved for key emphasis words only

---

## 📐 Layout System

### Grid
```
Max Content Width  → 1280px
Gutter (desktop)   → 80px horizontal padding
Gutter (mobile)    → 24px
Column Grid        → 12-column CSS Grid
Section Padding    → 120px top/bottom (desktop), 64px (mobile)
Card Gap           → 24px
```

### Breakpoints
```
Mobile    → < 768px
Tablet    → 768px–1024px
Desktop   → > 1024px
Wide      → > 1440px
```

---

## 🖼️ Visual Style Language

### 3D & Depth Effects

#### Floating Elements
- LIHF Logo: slowly rotates on Y-axis (CSS 3D transform, 8s loop)
- Golden particles: canvas or CSS floating dots background
- Stat cards: hover → `rotateX(5deg) rotateY(8deg) translateZ(20px)` (3D tilt)
- Sponsor tier cards: perspective tilt on mouse move (vanilla JS)

#### Glassmorphism Cards
```css
/* Glass Card Style */
background: rgba(255, 255, 255, 0.03);
backdrop-filter: blur(12px);
border: 1px solid rgba(245, 196, 0, 0.25);
border-radius: 16px;
box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5),
            inset 0 1px 0 rgba(245, 196, 0, 0.1);
```

#### Glow & Neon Effects
```css
/* Gold Glow — used on key CTAs and hero elements */
box-shadow: 0 0 20px rgba(245, 196, 0, 0.4),
            0 0 60px rgba(245, 196, 0, 0.15);
text-shadow: 0 0 30px rgba(245, 196, 0, 0.6);
```

#### Texture Overlays
- Subtle grain texture (noise SVG filter, opacity: 0.03) on hero bg
- Diagonal line pattern on section dividers
- Hexagon or graffiti-inspired subtle background texture

---

## 🎬 Animation & Motion Plan

### Principles
- Smooth, purposeful — not excessive
- Easing: `cubic-bezier(0.16, 1, 0.3, 1)` (spring-like)
- Duration: 0.4–0.8s for transitions, 2–8s for ambient loops
- Motion hierarchy: Hero → Section entry → Cards → Details

### Animation Inventory

| Element | Animation | Trigger | Duration |
|---|---|---|---|
| Hero text | Slide up + fade in, stagger letters | Page load | 1.2s |
| Stat numbers | Count up from 0 | Scroll into view | 2s |
| Section titles | Clip-reveal (left to right) | Scroll | 0.7s |
| Cards | Fade up + scale from 0.95 | Scroll | 0.5s stagger |
| LIHF Logo (hero) | Slow Y-axis rotation | Always | 8s loop |
| Particles | Float upward, random direction | Always | Ambient |
| CTA button | Pulse gold glow | Hover | 0.3s |
| Nav links | Gold underline slide in | Hover | 0.2s |
| Sponsor tiers | 3D tilt on mouse move | Mouse hover | Real-time |
| Progress bars | Fill from 0% | Scroll into view | 1s |
| Chart (donut) | Draw arc | Scroll | 1.5s |

### Scroll Behavior
- Smooth scroll: `scroll-behavior: smooth`
- Snap scrolling: optional per section (test UX)
- Sticky navigation: appears after hero section
- Parallax depth on hero background (−0.3 factor)

---

## 🧩 Component Library

### 1. Navigation Bar
```
Position: Fixed top, transparent → blur/dark on scroll
Elements: LIHF Logo (small) | Nav links | "Become a Sponsor" CTA button (gold)
Mobile: Hamburger → full-screen overlay menu
```

### 2. Hero Section
```
Layout: Full viewport height (100vh)
Background: Video loop OR dark with animated gold particles canvas
Foreground:
  - LIHF Badge Logo (3D rotating, center or left-aligned)
  - "OFFICIAL SPONSORSHIP & PARTNERSHIP PROPOSAL" — label tag
  - "LAO INTERNATIONAL HIPHOP FESTIVAL 2026" — hero title (Bebas Neue)
  - Tagline: "One Culture • One Movement • One Region"
  - Event badge: 📅 Nov 13–15, 2026 | 📍 Lao-ITECC, Vientiane
  - CTA row: [View Proposal ↓] [Download Deck ⬇]
Scroll indicator: Animated chevron or bouncing dot
```

### 3. Stat Counter Card
```
Layout: Horizontal scroll row OR 3-column grid
Card content:
  - Large number (Bebas Neue, gold)
  - Unit label
  - Description text (muted)
  - Icon (optional)
Effect: Count-up animation on scroll, glass card style
```

### 4. Audience Pie / Segment Card
```
Layout: 3 cards side by side, or stacked on mobile
Each card:
  - Percentage (large, gold)
  - Segment name
  - Profile bullets
  - Progress bar or arc indicator
Highlight: 50% card is largest/featured
```

### 5. Event Pillar Cards (Program Section)
```
Layout: Horizontal card rail or 2-column grid
Card content:
  - Number badge (#1–#7, gold circle)
  - Event name (bold)
  - Prize pool badge (gold tag)
  - Format description
  - Format badge (International / National)
Hover: Gold border glow, slight lift translateY(−6px)
```

### 6. Sponsorship Tier Cards
```
Layout: 4 cards (Title, Gold, Silver, Bronze)
Featured: Title card is taller / has crown icon
Card content:
  - Tier icon + name
  - Investment amount (large, gold)
  - Availability badge
  - Benefit bullets (checkmarks in gold)
  - CTA: "Select This Tier"
Effect: 3D mouse-tracking tilt, gold border glow on Title
```

### 7. Timeline / Roadmap
```
Layout: Horizontal step-by-step (desktop), vertical (mobile)
Steps: 4 steps with icons, connecting line
Active state: Gold filled, glowing
Future state: Outline, muted
```

### 8. Budget Donut Chart
```
Type: CSS/Canvas animated donut chart
Colors: Each slice = distinct gold/grey shade
Hover: Show label + amount + percentage
Legend: Inline list with colored dots
```

### 9. Phase Campaign Cards (Digital Strategy)
```
Layout: 3-phase horizontal row
Phase cards: Numbered (01, 02, 03) with phase name
Sub-items: Bullet list of tactics
Connecting arrows between phases
Colors: Phase 1 dark, Phase 2 gold, Phase 3 mid
```

### 10. Download / CTA Section
```
Background: Full-width gold gradient or dark with gold accents
Heading: "Ready to Partner with Laos' Biggest HipHop Festival?"
Subtext: Contact + website info
Buttons:
  - Download Slide Deck (PDF) — uses html2canvas + jsPDF
  - Contact Us (mailto link)
  - Social media icon row
```

---

## 📱 Mobile UX Notes

- All stat numbers readable without zoom
- Cards: single column stack
- Sponsor tiers: horizontal scroll with snap
- Navigation: hamburger → fullscreen black overlay
- Touch-optimized tap targets: min 48px
- No hover-only content (duplicate on tap)
- Hero: reduce particle count for performance

---

## ♿ Accessibility Notes

- Color contrast: all text ≥ 4.5:1 ratio on dark bg
- Focus states: visible gold outline
- ARIA labels on icon-only buttons
- Animated elements: `prefers-reduced-motion` media query
- Alt text on all images
- Semantic HTML: `<nav>`, `<main>`, `<section>`, `<article>`

---

## 🔧 Technical Notes for AI Coder

### Recommended Libraries (CDN, no build step)
```html
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Space+Grotesk:wght@400;600;700&family=Oswald:wght@600&display=swap" rel="stylesheet">

<!-- GSAP (animations) -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<!-- html2canvas + jsPDF (download slide deck) -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<!-- Optional: Three.js (3D logo) -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

### File Structure
```
/LIHF2026/
├── index.html              ← Main web portfolio
├── slides.html             ← Printable slide deck version
├── assets/
│   ├── lihf-logo.png
│   ├── tshirt-mockup.jpg
│   └── bg-texture.png      ← optional grain texture
├── css/
│   └── styles.css          ← (or inline in HTML)
└── js/
    └── main.js             ← (or inline in HTML)
```

### Performance Targets
- First Contentful Paint: < 1.5s
- Interaction to Next Paint: < 200ms
- Total JS: < 200kb (excluding CDN)
- Images: WebP format, lazy loading
