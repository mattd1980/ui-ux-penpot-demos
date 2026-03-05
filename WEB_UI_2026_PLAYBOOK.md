# Web UI Playbook (2026)

Use this as the default standard for modern web UI decisions.

## Core Principles
- Clarity over cleverness.
- Fast perceived performance beats ornamental complexity.
- Accessibility is baseline quality, not a feature.
- Fewer decisions per screen = better conversion.
- Design systems over one-off components.

## 2026 Web UI Best Practices

### 1) Speed + Responsiveness
- Target sub-100ms interaction feedback where possible.
- Use optimistic UI for reversible actions.
- Skeletons over spinners for content loading.
- Avoid layout shift (stable placeholders, reserved media space).

### 2) AI-Aware UX Patterns
- Distinguish AI-generated content from user/system content clearly.
- Show confidence/uncertainty cues for AI outputs when relevant.
- Always provide edit/undo paths for AI actions.
- Keep human override obvious and frictionless.

### 3) Accessibility (WCAG 2.2+ mindset)
- Keyboard-first navigation and visible focus states.
- Sufficient contrast in all states (hover, disabled, focus, error).
- Touch targets comfortably large on mobile.
- Semantic labels and meaningful error guidance.

### 4) Mobile-First Reality
- Thumb-zone aware primary actions.
- Reduced visual density on small screens.
- Sticky contextual actions for long forms and commerce flows.
- Avoid modal-over-modal patterns on mobile.

### 5) Forms + Conversion UX
- Progressive disclosure for complex forms.
- Inline validation with plain language fixes.
- Preserve user input on error and reconnect.
- Minimize required fields and explain why data is needed.

### 6) Design System Discipline
- Use tokens for spacing, color, typography, radius, elevation.
- Define component states explicitly: empty/loading/error/success/disabled.
- Keep motion purposeful and brief; respect reduced-motion preferences.

### 7) Trust + Safety UX
- Show clear permission boundaries and data usage context.
- Add confirmation for destructive actions and recovery paths.
- Prefer transparent system status over silent failures.

### 8) Measurement Standards
Every major UI recommendation should include:
- Primary metric (e.g., activation, completion rate, CTR, task success)
- Leading indicator (e.g., time to complete, drop-off at step N)
- Validation plan (A/B test or before/after instrumentation)

### 9) Dark Mode & Theme Flexibility
- Design in both light and dark from the start (not as an afterthought).
- Use semantic color tokens (not hard-coded hex values).
- Test contrast in both modes, especially for charts and data viz.
- Respect system preference but allow manual override.
- Avoid pure black (#000) - use dark grays for better readability.

### 10) Privacy-First Patterns (2026)
- No cookie banners if you're not tracking (just don't track!).
- Explain data usage in-context, not buried in a policy link.
- Local-first wherever possible (IndexedDB, localStorage, OPFS).
- When you do collect data, show what you have and let users delete it.
- Prefer privacy-preserving analytics (no PII in event payloads).

### 11) Component Composition
- Favor composable primitives over monolithic components.
- Use compound components for complex UI (Tabs.Root, Tabs.List, Tabs.Content).
- Separate layout from content (Container, Stack, Grid vs Button, Card).
- Slot-based APIs for flexibility (e.g., `<Button leftIcon={...} />`).
- Avoid prop explosion - use composition over configuration.

### 12) Error Recovery & Resilience
- **Never lose user work** - auto-save drafts, preserve form state on error.
- Show recovery options, not just error messages ("Try again" / "Save offline").
- Network-aware UI (show offline state, queue actions for later).
- Graceful degradation (if feature X fails, keep Y and Z working).
- Clear error hierarchy: info → warning → error → critical.

### 13) AI Interaction Patterns (2026)
- **Streaming responses**: Show partial results as they arrive (not all-or-nothing).
- **Regeneration**: Always allow "try again" or "refine" for AI outputs.
- **Attribution**: When AI uses external data, cite sources clearly.
- **Confidence indicators**: Show when the AI is uncertain (e.g., "I'm not sure, but...").
- **Human-in-the-loop**: For high-stakes actions, require confirmation.
- **Editing AI output**: Make it easy to tweak AI-generated content inline.

### 14) Information Architecture
- **Progressive disclosure**: Show only what's needed now, reveal more on demand.
- **Clear hierarchy**: Use visual weight, spacing, and typography to guide attention.
- **Search + browse**: Offer both (people think differently).
- **Breadcrumbs for depth**: When navigating hierarchies, show where you are.
- **Empty states**: Make them actionable (not just "no data yet").

### 15) Data Visualization (2026)
- **Accessible charts**: Use patterns/textures, not just color.
- **Interactive legends**: Click to toggle series on/off.
- **Responsive scales**: Adapt to container size, not fixed dimensions.
- **Context tooltips**: Show exact values and comparisons on hover.
- **Export options**: Let users download data (CSV, PNG, SVG).

## Default Output Template for Reviews
1. Problem and user impact
2. Recommended UI change
3. Why this aligns with 2026 standards
4. Accessibility + edge states
5. Engineering handoff notes
6. Metric + validation plan
