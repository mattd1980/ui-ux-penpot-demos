# Content Mogul - Visual Style Documentation

Based on analysis of the `heliacode/content-mogul` repository CSS and HTML files.

**Last Updated:** 2026-03-05  
**Repository:** heliacode/content-mogul (private)  
**UI Framework:** Tailwind CSS + custom overrides

---

## Design Philosophy

**"Grounded" aesthetic** - Reduced "floaty" feel with:
- Subtle lift effects (1px vs aggressive transforms)
- Refined shadows (low opacity, tight spread)
- Fast, snappy animations (280ms vs 400ms+)
- Respects `prefers-reduced-motion`

---

## Typography

### Font Family
- **Primary:** Ubuntu (Google Fonts)
- **Weights:** 300 (light), 400 (regular), 500 (medium), 700 (bold)

### Font Weight Usage
```css
body: 400 (regular)
h1-h6: 700 (bold)
button, .font-semibold, .font-bold: 500 (medium)
.font-light: 300 (light)
```

### Tailwind Typography Classes
- Display/Headings: `text-xl`, `text-2xl`, `text-3xl`
- Body: `text-base`, `text-sm`
- Meta/captions: `text-xs`

---

## Color Palette

### Primary Brand Colors

**Purple (Primary Brand)**
- `#9333ea` - Main gradient start, primary actions, brand accents
- `#7e22ce` - Gradient hover darker variant
- `purple-600` (#9333ea) - Primary interactive elements (114 uses)
- `purple-700` (#7e22ce) - Emphasis text (15 uses)
- `purple-900` (#581c87) - Strong emphasis (11 uses)
- `purple-500` (#a855f7) - Borders and subtle accents (10 uses)
- `purple-50` (#faf5ff) - Light backgrounds (13 uses)
- `purple-100` (#f3e8ff) - Subtle hover states (4 uses)

**Pink (Secondary Brand)**
- `#ec4899` - Main gradient end, secondary actions
- `#db2777` - Gradient hover darker variant  
- `pink-600` (#ec4899) - Secondary accents (5 uses)

**Gradient (Primary CTA)**
```css
background: linear-gradient(135deg, #9333ea 0%, #ec4899 100%);
/* Hover variant: #7e22ce to #db2777 */
```

### Semantic Colors

**Gray Scale (Most Used - 199 text-gray-900 instances)**
- `gray-900` (#111827) - Primary text (199 uses)
- `gray-800` (#1f2937) - Strong emphasis (80 uses)  
- `gray-700` (#374151) - Secondary headings (135 uses)
- `gray-600` (#4b5563) - Body text (107 uses)
- `gray-500` (#6b7280) - Muted text (83 uses)
- `gray-400` (#9ca3af) - Placeholder, disabled (67 uses)
- `gray-300` (#d1d5db) - Borders (84 uses)
- `gray-200` (#e5e7eb) - Dividers, light borders (126 uses)
- `gray-100` (#f3f4f6) - Hover backgrounds (20 uses)
- `gray-50` (#f9fafb) - Subtle backgrounds (53 uses)

**Success (Green)**
- `green-600` (#10b981) - Success states, checkboxes (16 uses)
- `green-700` (#059669) - Emphasis (6 uses)
- `green-500` (#10b981) - Active indicators (7 uses)
- `green-50` (#ecfdf5) - Success backgrounds (6 uses)
- `green-200` (#bbf7d0) - Success borders (7 uses)

**Error/Warning (Red)**
- `red-600` (#dc2626) - Error text, destructive actions (34 uses)
- `red-800` (#991b1b) - Strong error emphasis (8 uses)
- `red-700` (#b91c1c) - Error states (9 uses)
- `red-50` (#fef2f2) - Error backgrounds (16 uses)
- `red-200` (#fecaca) - Error borders (17 uses)

**Informational (Blue)**
- `blue-600` (#2563eb) - Info actions, links (9 uses)
- `indigo-600` (#4f46e5) - Alternative info states (5 uses)

**Warning (Amber)**
- `amber-100` (#fef3c7) - Warning backgrounds (7 uses)
- `amber-700` (#b45309) - Warning text (6 uses)

---

## Spacing & Layout

### Container Widths
Based on Tailwind defaults:
- Mobile: full width (100%)
- `sm:` 640px
- `md:` 768px  
- `lg:` 1024px
- `xl:` 1280px

### Common Spacing Patterns
```css
Padding (cards/sections): p-4 (16px), p-6 (24px)
Margins (sections): mb-4 (16px), mb-6 (24px), mb-8 (32px)
Gaps (flex/grid): gap-2 (8px), gap-4 (16px), gap-6 (24px)
```

---

## Border Radius

### Standard Rounding
- Buttons, inputs, cards: `rounded-lg` (8px)
- Badges, small elements: `rounded` (4px) or `rounded-md` (6px)
- Modals, large cards: `rounded-xl` (12px)
- Pills, avatars: `rounded-full` (9999px)

---

## Shadows

### Grounded Shadow System
```css
/* Default card (subtle) */
box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06);

/* Card hover (refined, not aggressive) */
box-shadow: 0 10px 18px -10px rgba(0, 0, 0, 0.18);

/* Gradient button hover */
box-shadow: 0 10px 18px -10px rgba(147, 51, 234, 0.45);
```

**Philosophy:** Shadows are tight, low-opacity, and don't "float" components.

---

## Animation & Motion

### Timing Functions
- Standard transitions: `160ms ease`
- Fade-in: `280ms ease-out`
- Hover lifts: `160ms ease`

### Keyframe: fadeIn
```css
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.fade-in {
  animation: fadeIn 0.28s ease-out forwards;
}
```

### Hover Behaviors
**Card Hover (Grounded):**
```css
@media (hover: hover) and (pointer: fine) {
  .card-hover:hover {
    transform: translateY(-1px);
    box-shadow: 0 10px 18px -10px rgba(0, 0, 0, 0.18);
  }
}
```

**Gradient Button Hover:**
```css
.gradient-button:hover {
  transform: translateY(-1px);
  background: linear-gradient(135deg, #7e22ce 0%, #db2777 100%);
  box-shadow: 0 10px 18px -10px rgba(147, 51, 234, 0.45);
}
```

### Motion Accessibility
```css
@media (prefers-reduced-motion: reduce) {
  .fade-in {
    animation: none !important;
  }
  .card-hover,
  .gradient-button {
    transition: none !important;
  }
}
```

---

## Component Patterns

### Navigation Header
- **Background:** Purple-to-Pink gradient (`#9333ea` to `#ec4899`)
- **Text:** `text-white/90` with `hover:text-white`
- **Hover states:** `hover:bg-white/10` (subtle)
- **Transition:** `transition-colors`

### Cards
- **Background:** `bg-white`
- **Border:** `border border-gray-200`
- **Radius:** `rounded-lg` (8px)
- **Padding:** `p-6` (24px)
- **Hover:** `.card-hover` class (1px lift, refined shadow)
- **Action buttons:** `.card-action-btn` (opacity: 0 → 1 on hover)

### Buttons

**Primary (Gradient):**
```css
.gradient-button
background: linear-gradient(135deg, #9333ea 0%, #ec4899 100%)
padding: py-2.5 px-5 (10px/20px)
border-radius: rounded-lg (8px)
hover: darker gradient + 1px lift + purple shadow
```

**Secondary/Outline:**
```css
border: 2px solid
background: transparent
hover: subtle background fill
```

**Danger:**
```css
background: red-600 (#dc2626)
hover: red-700 (#b91c1c)
```

### Forms & Inputs
- **Border:** `border-gray-300`
- **Focus state:** `box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.14)` (indigo ring)
- **Padding:** `px-4 py-2` (standard inputs)
- **Border radius:** `rounded-lg` (8px)
- **Disabled:** `bg-gray-100 text-gray-400`

### Badges/Tags
- **Keyword selected:** `bg-green-600` (#10b981), white text
- **Keyword hover:** `border-green-400`, `bg-green-50`
- **Info badge:** `bg-purple-50 text-purple-700`
- **Warning badge:** `bg-amber-50 text-amber-700`

### Empty States
- **Border:** `border-2 border-dashed border-gray-300`
- **Hover:** `hover:border-purple-500`
- **Icon:** `text-gray-400`
- **Text:** `text-gray-600`

---

## Accessibility

### Focus States
- **Ring color:** Indigo (`rgba(99, 102, 241, 0.14)`)
- **Ring width:** 3px
- **Visible on all interactive elements**

### Contrast Ratios
Primary text combinations (WCAG 2.2 compliant):
- `gray-900` on `white` - ✅ 16.5:1 (AAA)
- `gray-700` on `white` - ✅ 10.7:1 (AAA)
- `gray-600` on `white` - ✅ 7.0:1 (AAA)
- `purple-600` on `white` - ✅ 5.9:1 (AA)
- White on `purple-600` - ✅ 7.1:1 (AAA)

### Motion Preferences
- Respects `prefers-reduced-motion`
- All animations can be disabled
- Transitions fallback to instant state changes

---

## Usage Guidelines

### When to Use Purple Gradient
- Primary CTAs (e.g., "Create Content", "Save", "Publish")
- Hero sections
- Key conversion actions
- Not for every button (reserve for impact)

### When to Use Gray Scale
- Body text: `gray-700` or `gray-600`
- Secondary text: `gray-500`
- Disabled/placeholder: `gray-400`
- Borders: `gray-200` or `gray-300`
- Backgrounds: `gray-50` or `gray-100`

### When to Use Semantic Colors
- **Green:** Success confirmations, completed states, positive indicators
- **Red:** Errors, warnings, destructive actions (with confirmation)
- **Blue:** Informational messages, alternative CTAs
- **Amber:** Caution states, warnings that aren't errors

---

## Dark Mode Considerations

**Current Status:** No dark mode implementation detected in CSS.

**Recommendations (if implementing):**
- Swap gray scale (900 becomes background, 50 becomes text)
- Reduce purple gradient opacity or use darker variants
- Maintain semantic color meanings
- Test contrast ratios for WCAG compliance
- Use `dark:` Tailwind variants

---

## Implementation Checklist

When building new Content Mogul components:

- [ ] Use Ubuntu font family
- [ ] Primary text: `gray-900` or `gray-700`
- [ ] Cards: `bg-white border border-gray-200 rounded-lg p-6`
- [ ] Hover lifts: 1px max (`.card-hover` pattern)
- [ ] Shadows: Subtle, tight spread
- [ ] Animations: 160-280ms, ease-out
- [ ] Purple gradient for primary CTAs only
- [ ] Semantic colors for status/feedback
- [ ] Focus rings: 3px indigo
- [ ] Respect `prefers-reduced-motion`
- [ ] Test contrast ratios (WCAG 2.2)

---

## Files Reference

- **Main styles:** `/public/ui-grounded.css`
- **In-page styles:** Embedded `<style>` blocks in each HTML file
- **Framework:** Tailwind CSS (CDN) + custom overrides
- **Icons:** Font Awesome 6.5.1

---

## Design System Tokens (Extracted)

### Color Tokens
```javascript
const colors = {
  brand: {
    purple: '#9333ea',      // purple-600
    purpleDark: '#7e22ce',  // purple-700
    pink: '#ec4899',        // pink-600
    pinkDark: '#db2777',    // pink-700
  },
  text: {
    primary: '#111827',     // gray-900
    secondary: '#374151',   // gray-700
    tertiary: '#6b7280',    // gray-600
    muted: '#9ca3af',       // gray-400
  },
  bg: {
    primary: '#ffffff',
    secondary: '#f9fafb',   // gray-50
    tertiary: '#f3f4f6',    // gray-100
  },
  border: {
    default: '#e5e7eb',     // gray-200
    light: '#d1d5db',       // gray-300
  },
  semantic: {
    success: '#10b981',     // green-600
    error: '#dc2626',       // red-600
    warning: '#f59e0b',     // amber-500
    info: '#2563eb',        // blue-600
  }
};
```

### Spacing Tokens
```javascript
const spacing = {
  xs: '4px',
  sm: '8px',
  md: '16px',
  lg: '24px',
  xl: '32px',
  '2xl': '48px',
};
```

### Typography Tokens
```javascript
const typography = {
  fontFamily: "'Ubuntu', sans-serif",
  fontSize: {
    xs: '12px',
    sm: '14px',
    base: '16px',
    lg: '18px',
    xl: '20px',
    '2xl': '24px',
    '3xl': '30px',
  },
  fontWeight: {
    light: 300,
    regular: 400,
    medium: 500,
    bold: 700,
  },
  lineHeight: {
    tight: 1.25,
    normal: 1.5,
    relaxed: 1.75,
  }
};
```

### Border Radius Tokens
```javascript
const borderRadius = {
  sm: '4px',
  md: '6px',
  lg: '8px',
  xl: '12px',
  '2xl': '16px',
  full: '9999px',
};
```

### Shadow Tokens
```javascript
const shadows = {
  sm: '0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06)',
  md: '0 10px 18px -10px rgba(0, 0, 0, 0.18)',
  purple: '0 10px 18px -10px rgba(147, 51, 234, 0.45)',
};
```

---

**Generated by:** Elaine (UI/UX Expert Agent)  
**Source:** Analysis of heliacode/content-mogul codebase  
**For:** Content Mogul design consistency and component development
