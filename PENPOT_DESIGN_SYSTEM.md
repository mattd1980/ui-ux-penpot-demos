# Penpot Design System Foundation

Practical implementation guide for building UI components in Penpot that align with the 2026 playbook.

## Design Tokens

### Spacing Scale (8px base)
```
xs:   4px   (tight spacing, chip padding)
sm:   8px   (button padding, list gaps)
md:   16px  (card padding, section gaps)
lg:   24px  (page padding, major sections)
xl:   32px  (hero sections)
2xl:  48px  (page gutters)
3xl:  64px  (major layout breaks)
```

### Typography Scale
```
xs:   12px  (metadata, captions, badges)
sm:   14px  (body text, descriptions)
base: 16px  (primary body text)
lg:   18px  (large body, intro text)
xl:   20px  (subheadings, card titles)
2xl:  24px  (section headings)
3xl:  30px  (page titles)
4xl:  36px  (hero headings)
```

**Font weights:**
- Regular: 400 (body text)
- Medium: 500 (labels, buttons)
- Semibold: 600 (headings, emphasis)
- Bold: 700 (hero text, strong emphasis)

**Line heights:**
- Tight: 1.2 (headings)
- Normal: 1.5 (body text)
- Relaxed: 1.75 (long-form content)

### Color System

**Neutrals (light mode):**
```
gray-50:  #F9FAFB  (subtle backgrounds)
gray-100: #F3F4F6  (hover states, dividers)
gray-200: #E5E7EB  (borders)
gray-300: #D1D5DB  (disabled text)
gray-400: #9CA3AF  (secondary text)
gray-500: #6B7280  (body text)
gray-600: #4B5563  (headings)
gray-700: #374151  (strong emphasis)
gray-800: #1F2937  (titles)
gray-900: #111827  (primary text)
```

**Neutrals (dark mode):**
```
gray-900: #18181B  (background)
gray-800: #27272A  (card backgrounds)
gray-700: #3F3F46  (borders)
gray-600: #52525B  (dividers)
gray-500: #71717A  (secondary text)
gray-400: #A1A1AA  (body text)
gray-300: #D4D4D8  (headings)
gray-200: #E4E4E7  (emphasis)
gray-100: #F4F4F5  (strong emphasis)
```

**Brand colors:**
```
primary:   #3B82F6  (actions, links)
secondary: #8B5CF6  (accents)
success:   #10B981  (positive states)
warning:   #F59E0B  (caution states)
error:     #EF4444  (errors, destructive)
info:      #06B6D4  (informational)
```

**Semantic colors:**
```
bg-primary:      #FFFFFF (light) / #18181B (dark)
bg-secondary:    #F9FAFB (light) / #27272A (dark)
text-primary:    #111827 (light) / #F4F4F5 (dark)
text-secondary:  #6B7280 (light) / #A1A1AA (dark)
border-default:  #E5E7EB (light) / #3F3F46 (dark)
```

### Border Radius
```
sm:   2px   (small elements, badges)
md:   4px   (buttons, inputs)
lg:   8px   (cards, modals)
xl:   12px  (large cards)
2xl:  16px  (hero sections)
full: 9999px (pills, avatars)
```

### Shadows
```
sm:  0 1px 2px rgba(0,0,0,0.05)
md:  0 2px 8px rgba(0,0,0,0.08)
lg:  0 8px 24px rgba(0,0,0,0.12)
xl:  0 16px 48px rgba(0,0,0,0.16)
```

## Component State Matrix

Every interactive component needs these states defined:

### Button States
```
Default:  primary bg, white text
Hover:    darker primary (-10% lightness)
Focus:    outline ring (2px, primary color)
Active:   even darker (-15% lightness)
Disabled: gray-300 bg, gray-400 text, cursor not-allowed
Loading:  spinner + disabled appearance
```

### Input States
```
Default:  border-default, bg-white
Hover:    border-gray-400
Focus:    border-primary, 2px ring
Error:    border-error, error text below
Disabled: bg-gray-100, text-gray-400
Filled:   slightly darker border
```

### Card States
```
Default:  white bg, subtle border
Hover:    shadow-md, slight scale (1.02)
Selected: border-primary, shadow-lg
Empty:    gray-100 bg, dashed border, centered message
Loading:  skeleton gradient animation
Error:    border-error, error message inside
```

## Wireframe Component Checklist

When building a component in Penpot, ensure:

- [ ] **Width constraints** on all text elements (prevent overflow)
- [ ] **Padding/spacing** uses tokens (4/8/16/24/32px)
- [ ] **All interactive states** are defined (hover/focus/active/disabled)
- [ ] **Empty states** are designed (what shows with no data?)
- [ ] **Error states** are designed (what shows when things break?)
- [ ] **Loading states** are designed (skeleton, not spinner)
- [ ] **Responsive breakpoints** considered (mobile/tablet/desktop)
- [ ] **Contrast ratios** meet WCAG 2.2 (4.5:1 for text)
- [ ] **Touch targets** are 44x44px minimum on mobile
- [ ] **Focus indicators** are visible (not removed)

## Penpot Implementation Notes

### Text Width Constraints
Always set explicit width on text elements:
```javascript
// Example for 320px card with 16px padding
textWidth = cardWidth - (padding * 2)  // 288px
```

### Creating Consistent Spacing
Use the spacing scale when positioning elements:
```javascript
// Stack elements with proper gaps
element1.y = 100
element2.y = element1.y + element1.height + 16  // md gap
element3.y = element2.y + element2.height + 16  // md gap
```

### Reusable Color Palette
Create a reference file with swatches for:
- All gray scale values
- Brand colors
- Semantic colors (light + dark mode)
- Component state colors

### Component Library Structure
```
/Design System
  /Foundations
    - Colors
    - Typography
    - Spacing
    - Shadows
  /Components
    /Buttons
      - Primary (all states)
      - Secondary (all states)
      - Destructive (all states)
    /Inputs
      - Text (all states)
      - Select (all states)
      - Checkbox (all states)
    /Cards
      - Basic (all states)
      - Content card (with variants)
      - Product card (with variants)
  /Patterns
    - Navigation
    - Forms
    - Modals
    - Empty states
```

## Quick Reference: Common Components

### Content Card (like we built)
- Container: white bg, gray-200 border, lg radius
- Image: 16:9 aspect ratio
- Badge: primary color, sm radius, xs text
- Title: xl text, semibold weight, gray-900 color
- Description: sm text, regular weight, gray-500 color, constrained width
- Meta: xs text, gray-400 color
- Padding: md (16px) all sides

### Button (Primary)
- Height: 40px (comfortable touch target)
- Padding: sm vertical (8px), md horizontal (16px)
- Text: sm size (14px), medium weight (500)
- Border radius: md (4px)
- All states defined (default/hover/focus/active/disabled)

### Input Field
- Height: 40px minimum
- Padding: sm (8px) vertical, md (16px) horizontal
- Border: 1px, border-default color
- Border radius: md (4px)
- Label: sm text, above input, gray-700 color
- Error message: xs text, error color, below input

### Modal
- Max width: 600px (desktop), 90vw (mobile)
- Padding: lg (24px)
- Border radius: xl (12px)
- Shadow: xl
- Overlay: rgba(0,0,0,0.5)
- Close button: top-right, 44x44px target

## Validation Checklist Before Delivery

- [ ] All text wraps properly (no overflow)
- [ ] Spacing is consistent (uses tokens)
- [ ] Colors use semantic names (not raw hex)
- [ ] Component has all required states
- [ ] Touch targets are 44x44px minimum
- [ ] Contrast ratios pass WCAG 2.2
- [ ] Design works in both light and dark mode
- [ ] Responsive behavior is defined
- [ ] Empty/loading/error states exist
- [ ] Documentation includes success metrics
