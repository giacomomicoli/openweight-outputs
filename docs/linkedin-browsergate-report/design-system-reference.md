# Apple Design System Reference

A comprehensive reference document for the Apple-inspired minimalistic design system used in the BrowserGate report webpage.

## Table of Contents
1. [Color System](#color-system)
2. [Typography](#typography)
3. [Layout & Spacing](#layout--spacing)
4. [Components](#components)
5. [Effects & Shadows](#effects--shadows)
6. [Responsive Breakpoints](#responsive-breakpoints)
7. [CSS Variables](#css-variables)
8. [Usage Examples](#usage-examples)

---

## Color System

### Primary Colors

| Name | Hex | CSS Variable | Usage |
|------|-----|------------|-------|
| Apple Blue | `#0071e3` | `--apple-blue` | Links, accents, active states |
| Apple Blue Hover | `#0077ed` | `--apple-blue-hover` | Link hover states |
| Dark Text | `#1d1d1f` | `--dark-text` | Primary text, headings |
| Secondary Text | `#86868b` | `--secondary-text` | Captions, metadata, labels |
| Light Background | `#f5f5f7` | `--light-bg` | Section backgrounds, cards |
| White | `#ffffff` | `--white` | Main background |
| Border | `#d2d2d7` | `--border` | Dividers, card borders |
| Warning Red | `#ff3b30` | `--warning` | Alerts, errors |
| Success Green | `#34c759` | `--success` | Success states, checkmarks |

### Gradient Presets

**Hero Title Gradient:**
```css
background: linear-gradient(135deg, #1d1d1f 0%, #434344 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
```

**Hero Section Background:**
```css
background: linear-gradient(180deg, var(--light-bg) 0%, var(--white) 100%);
```

**Warning Banner Background:**
```css
background: linear-gradient(135deg, #fff5f5 0%, #ffe5e5 100%);
border: 1px solid #ffcfcf;
```

---

## Typography

### Font Stack

**Primary Font Stack:**
```css
font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Inter', 'Segoe UI', Roboto, sans-serif;
```

**Web Fonts Loaded:**
- Inter (300, 400, 500, 600, 700)
- SF Pro Display (300, 400, 600, 700) - fallback only

### Type Scale

| Element | Size | Weight | Line Height | Letter Spacing | Usage |
|---------|------|--------|-------------|----------------|-------|
| Hero Title | 80px | 700 | 1.05 | -0.003em | Section 1 headlines |
| Section Title | 56px | 700 | 1.07 | -0.005em | Major section headings |
| Subsection Title | 32px | 700 | - | - | Inner section headings |
| Hero Subtitle | 28px | 400 | - | - | Hero descriptions |
| Quote Text | 28px | 400 | 1.5 | - | Blockquotes |
| Card Title | 24px | 600 | - | -0.021em | Card headers |
| Section Intro | 21px | 400 | 1.5 | - | Under section titles |
| Timeline Title | 21px | 600 | - | - | Timeline events |
| Body | 17px | 400 | 1.47059 | -0.022em | Paragraphs, default |
| Card Text | 17px | 400 | 1.5 | - | Card content |
| Caption | 15px | - | - | - | Secondary info |
| Label | 14px | 600 | - | 0.08em uppercase | Section labels |
| Nav | 14px | 600 | - | - | Navigation items |
| Badge | 12px | 600 | - | 0.05em uppercase | Tags, status |

---

## Layout & Spacing

### Container

**Standard Container:**
```css
max-width: 980px;
margin: 0 auto;
padding: 0 22px;
```

**Navigation Container:**
```css
max-width: 1024px;
height: 48px;
```

### Section Spacing

| Spacing | Value | Usage |
|---------|-------|-------|
| Section Padding | 160px | Major section vertical padding |
| Section Padding (Mobile) | 100px | Reduced on smaller screens |
| Grid Gap | 24px | Between grid items |
| Card Padding | 40px | Internal card spacing |
| Timeline Gap | 32px | Space between dot and content |

### Key Spacing Variables

```css
--section-spacing: 160px;
```

---

## Components

### Navigation Bar

```css
nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(251, 251, 253, 0.8);
  backdrop-filter: saturate(180%) blur(20px);
  z-index: 1000;
  border-bottom: 1px solid rgba(0,0,0,0.05);
  height: 48px;
}
```

**Features:**
- Fixed position at top
- Frosted glass effect (backdrop-filter)
- Semi-transparent background

### Cards

**Card Base:**
```css
.card {
  background: var(--white);
  border-radius: 20px;
  padding: 40px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.08);
  border: 1px solid var(--border);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.12);
}
```

**Card Variants:**
- `.card` - Standard card
- `.card-full` - Full-width card (grid-column: 1 / -1)

**Card Parts:**
- `.card-icon` - Circular icon container (56x56px)
- `.card-title` - Card heading
- `.card-text` - Card body text
- `.card-highlight` - Large stat number (48px)
- `.card-sub` - Subtitle/label below highlight

### Quote Block

```css
.quote-block {
  background: var(--light-bg);
  border-radius: 20px;
  padding: 48px;
  margin: 60px 0;
  position: relative;
}

.quote-block::before {
  content: '"';
  font-size: 128px;
  font-weight: 700;
  color: var(--border);
  position: absolute;
  top: -20px;
  left: 24px;
  font-family: Georgia, serif;
}

.quote-text {
  font-size: 28px;
  font-weight: 400;
  line-height: 1.5;
  padding-left: 16px;
}

.quote-source {
  font-size: 17px;
  color: var(--secondary-text);
  margin-top: 24px;
  padding-left: 16px;
}
```

### Timeline

```css
.timeline {
  position: relative;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 20px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--border);
}

.timeline-item {
  display: flex;
  gap: 32px;
  padding: 32px 0;
  position: relative;
}

.timeline-dot {
  width: 12px;
  height: 12px;
  background: var(--apple-blue);
  border-radius: 50%;
  margin-top: 6px;
}

.timeline-date {
  font-size: 14px;
  font-weight: 600;
  color: var(--apple-blue);
  margin-bottom: 8px;
}

.timeline-title {
  font-size: 21px;
  font-weight: 600;
  margin-bottom: 8px;
}

.timeline-text {
  font-size: 17px;
  color: var(--secondary-text);
  line-height: 1.5;
}
```

### Stat Counter

**Stat Item:**
```css
.stat-item {
  text-align: center;
  padding: 32px 24px;
  background: var(--light-bg);
  border-radius: 20px;
}

.stat-value {
  font-size: 48px;
  font-weight: 700;
  color: var(--dark-text);
  margin-bottom: 8px;
  line-height: 1;
}

.stat-label {
  font-size: 14px;
  color: var(--secondary-text);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-weight: 500;
}
```

**Stat Row Layout:**
```css
.stats-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}
```

### Warning Banner

```css
.warning-banner {
  background: linear-gradient(135deg, #fff5f5 0%, #ffe5e5 100%);
  border: 1px solid #ffcfcf;
  border-radius: 16px;
  padding: 24px 32px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.warning-icon {
  width: 32px;
  height: 32px;
  background: var(--warning);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: 700;
}
```

### Badges

**Badge (Tag):**
```css
.hero-badge {
  display: inline-block;
  background: var(--dark-text);
  color: var(--white);
  padding: 8px 16px;
  border-radius: 98px;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
```

**Section Label:**
```css
.section-label {
  font-size: 14px;
  font-weight: 600;
  color: var(--apple-blue);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 16px;
}
```

### Status Pills

```css
.status-pill {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 14px;
  background: var(--white);
  border: 1px solid var(--border);
  border-radius: 98px;
  font-size: 13px;
  font-weight: 500;
}

.status-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
}

.status-dot.active { background: var(--success); box-shadow: 0 0 8px var(--success); }
.status-dot.pending { background: #ff9500; }
.status-dot.closed { background: var(--secondary-text); }
```

---

## Effects & Shadows

### Shadows

| Name | Value | Usage |
|------|-------|-------|
| Card Shadow | `0 4px 24px rgba(0,0,0,0.08)` | Default card state |
| Card Hover | `0 12px 40px rgba(0,0,0,0.12)` | Card hover state |
| Nav Shadow | `rgba(0,0,0,0.05)` | Navigation bottom border |

### Frosted Glass

```css
backdrop-filter: saturate(180%) blur(20px);
background: rgba(251, 251, 253, 0.8);
```

### Transitions

```css
transition: transform 0.3s ease, box-shadow 0.3s ease;
```

---

## Responsive Breakpoints

### Breakpoint System

| Breakpoint | Target | Changes |
|------------|--------|---------|
| Default | Desktop (>900px) | Full layout |
| max-width: 900px | Tablet | Reduced spacing, 2-col grids |
| max-width: 600px | Mobile | Single column, smaller type |

### Responsive Adjustments

**Tablet (max-width: 900px):**
```css
.hero-title { font-size: 48px; }
.hero-subtitle { font-size: 21px; }
.section-title { font-size: 40px; }
.grid { grid-template-columns: 1fr; }
.stats-row { grid-template-columns: repeat(2, 1fr); }
.section { padding: 100px 0; }
.quote-text { font-size: 21px; }
```

**Mobile (max-width: 600px):**
```css
.stats-row { grid-template-columns: 1fr; }
.hero-title { font-size: 36px; }
.section-title { font-size: 32px; }
```

---

## CSS Variables

### Complete Variable Set

```css
:root {
  /* Colors */
  --apple-blue: #0071e3;
  --apple-blue-hover: #0077ed;
  --dark-text: #1d1d1f;
  --secondary-text: #86868b;
  --light-bg: #f5f5f7;
  --white: #ffffff;
  --border: #d2d2d7;
  --warning: #ff3b30;
  --success: #34c759;
  
  /* Shadows */
  --card-shadow: 0 4px 24px rgba(0,0,0,0.08);
  
  /* Spacing */
  --section-spacing: 160px;
}
```

---

## Usage Examples

### Basic Section Structure

```html
<section class="section">
  <div class="container">
    <div class="section-header">
      <p class="section-label">01 — Label</p>
      <h2 class="section-title">Section Title</h2>
      <p class="section-intro">Introduction paragraph...</p>
    </div>
    
    <!-- Content goes here -->
  </div>
</section>
```

### Two Column Grid Cards

```html
<div class="grid">
  <div class="card">
    <div class="card-icon">🔍</div>
    <h3 class="card-title">Card Title</h3>
    <p class="card-text">Card description...</p>
  </div>
  <div class="card">
    <div class="card-icon">📊</div>
    <h3 class="card-title">Card Title</h3>
    <p class="card-text">Card description...</p>
  </div>
</div>
```

### Statistics Row

```html
<div class="stats-row">
  <div class="stat-item">
    <div class="stat-value">6,222</div>
    <div class="stat-label">Extensions Scanned</div>
  </div>
  <div class="stat-item">
    <div class="stat-value">48</div>
    <div class="stat-label">Data Points</div>
  </div>
</div>
```

### Quote Block

```html
<div class="quote-block">
  <p class="quote-text">The quote text goes here...</p>
  <p class="quote-source">— Attribution</p>
</div>
```

### Timeline Item

```html
<div class="timeline">
  <div class="timeline-item">
    <div class="timeline-dot"></div>
    <div class="timeline-content">
      <div class="timeline-date">April 2026</div>
      <div class="timeline-title">Event Title</div>
      <div class="timeline-text">Description...</div>
    </div>
  </div>
</div>
```

---

## Design Principles

1. **Clarity First**: Typography is highly legible with generous line-heights and contrast
2. **Generous Whitespace**: Section padding of 160px creates breathing room
3. **Subtle Depth**: Shadows are soft, borders are light gray
4. **Focus Hierarchy**: Section labels in blue guide the eye, main titles are bold
5. **Responsive Respect**: Major breakpoints at 900px and 600px
6. **Smooth Interactions**: Subtle hover transforms on cards
7. **Apple Aesthetic**: Frosted glass nav, rounded corners (20px), pill-shaped badges
8. **Data Visualization**: Stats displayed prominently with large numbers
9. **Readability**: 17px body text, 1.47059 line-height for comfortable reading

---

## External Dependencies

### Google Fonts
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=SF+Pro+Display:wght@300;400;600;700&display=swap" rel="stylesheet">
```

### Font Weights Used
- Inter: 300, 400, 500, 600, 700
- SF Pro Display: 300, 400, 600, 700 (system fallback)

---

## Browser Support

- Modern browsers with `backdrop-filter` support (Safari, Chrome, Edge)
- `-webkit-` prefixes for gradients where needed
- `-webkit-font-smoothing: antialiased` for crisp text on macOS

---

*Reference compiled April 23, 2026*
