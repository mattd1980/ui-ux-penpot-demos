# MEMORY.md - Long-Term Memory

## Core Operating Principles

### UI/UX Standards (2026)
- **ALWAYS consult `WEB_UI_2026_PLAYBOOK.md` before giving UI/UX advice**
- Default to modern patterns: optimistic UI, skeleton screens, clear AI affordances
- Accessibility is baseline, not optional
- Every recommendation needs a success metric
- Design systems > one-off components

**Playbook enhanced 2026-03-05** with:
- Dark mode as first-class consideration (semantic tokens, test both modes)
- Privacy-first patterns (local-first, in-context data explanations, no tracking bloat)
- Component composition (primitives over monoliths, compound components)
- Error recovery (never lose user work, offline support, clear error hierarchy)
- AI interaction patterns (streaming, regeneration, attribution, confidence indicators)
- Information architecture (progressive disclosure, actionable empty states)
- Data visualization (accessible charts, responsive, exportable)

### Key Lessons Learned

#### 2026-03-05: Text Wrapping Mistake
- Created Penpot card component with text that didn't wrap (756px wide text in 320px card)
- **Lesson**: Always set width constraints on text elements when creating designs programmatically
- **Fix**: Constrain text to container width minus padding (288px for 320px card with 16px padding)
- **Takeaway**: Test with realistic content lengths before calling something "done"

### Tools & Capabilities
- **Penpot MCP**: 81 tools for creating/reading/updating designs
- **Figma MCP**: Access to Figma files/components/styles (via `mcp-figma`)
- Function call syntax works: `mcporter call 'penpot.tool(arg: "value")'`
- CLI arg passing can be tricky - use function syntax when flag style fails

### Design System Foundation (2026-03-05)
Created `PENPOT_DESIGN_SYSTEM.md` with:
- **Design tokens**: spacing (8px base), typography scale, color system (light+dark), border radius, shadows
- **Component state matrix**: button/input/card states (default/hover/focus/active/disabled/loading/error/empty)
- **Wireframe checklist**: width constraints, padding tokens, all states, responsive, accessible
- **Implementation notes**: text width calculations, spacing formulas, color palette structure
- **Component library structure**: foundations → components → patterns
- **Validation checklist**: 10-point QA before delivery

This bridges the gap between UX principles (playbook) and actual Penpot implementation.

### Content Mogul Context
- Product URL: https://mogul.heliacode.com
- Working on design components for content creation platform
- Matt (user) expects high-quality UX work with attention to detail

### Things to Remember
- In group chats: contribute value, don't just acknowledge
- Write decisions to files - "mental notes" don't persist
- Call out bad UX directly and propose better alternatives
- Measure everything - no recommendations without success metrics
