---
name: ui-dev
description: Build UI components with accessibility, responsiveness, and design system consistency. Use when building components, layouts, forms, or any visual feature — especially when a Figma design or design system is involved.
---

# UI Development

Component-first UI development: accessible, responsive, design-system-aligned.

## How It Works

1. Understand the design spec (Figma link, description, or design tokens)
2. Identify the component hierarchy and reusable parts
3. Build from the inside out: atoms → molecules → layouts
4. Verify accessibility (keyboard nav, ARIA, contrast)
5. Test responsiveness across breakpoints
6. Validate against design if Figma is available

## Usage

```
"Build a responsive nav bar from this Figma design [URL]"
"Create a reusable Button component with primary/secondary/danger variants"
"/ui-dev add a modal with keyboard trap and focus management"
"Build a data table with sorting and pagination"
```

## Component Checklist

Before marking a component complete:

```
Functionality
- [ ] All states implemented (default, hover, focus, active, disabled, loading, error)
- [ ] Props typed with sensible defaults
- [ ] Edge cases handled (empty state, long text, overflow)

Accessibility
- [ ] Keyboard navigable (Tab, Enter, Escape, arrow keys where applicable)
- [ ] ARIA roles and labels correct
- [ ] Focus visible — never remove outline without a custom replacement
- [ ] Color contrast meets WCAG AA (4.5:1 text, 3:1 UI)
- [ ] Screen reader tested (at minimum, logical reading order)

Responsiveness
- [ ] Mobile (≥320px), tablet (≥768px), desktop (≥1280px)
- [ ] No horizontal scroll on mobile
- [ ] Touch targets ≥ 44×44px

Design Fidelity
- [ ] Spacing matches design tokens / Figma
- [ ] Typography: font, size, weight, line-height correct
- [ ] Colors from design system only (no hardcoded hex unless documented)
```

## Component Structure

```
components/
  Button/
    Button.tsx       # Component
    Button.test.tsx  # Unit tests
    index.ts         # Re-export
```

## Responsive Breakpoints

| Name    | Min width | Common use |
|---------|-----------|------------|
| mobile  | 320px     | base styles |
| tablet  | 768px     | md: |
| desktop | 1280px    | lg: |

## Rules

ALWAYS:
- Use semantic HTML (button for actions, a for navigation, etc.)
- Add `aria-label` when visible label is absent
- Use design tokens / CSS variables — never magic numbers
- Handle all interactive states in CSS
- Test with keyboard only before marking done

NEVER:
- Use `div` or `span` for interactive elements
- Remove `outline` without replacement
- Hardcode colors outside the design system
- Ship without mobile testing
- Nest interactive elements (e.g., button inside button)

## Troubleshooting

**Component doesn't match Figma:** Check spacing scale (usually 4px or 8px base), then typography, then color — in that order.

**Focus not visible:** Add `:focus-visible` with a high-contrast outline — don't use `:focus` alone (triggers on click too).

**Layout breaks on mobile:** Start from mobile styles and use `min-width` media queries (mobile-first).
