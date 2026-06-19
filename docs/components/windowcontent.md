# WindowContent

This section covers the **WindowContent** component — a single wrapper providing themed border, background, padding, and text color for window content.

---

## Purpose

WindowContent is the replacement for the old three-layer pattern (WindowInset → WindowSpacing → WindowInner). It applies all visual styling from the current theme in one component.

**BaseWindow** uses WindowContent internally — you only need to use it directly when building content outside of BaseWindow or when nesting separate content sections.

---

## Usage

```jsx
import { WindowContent } from 'futurist-components';

function MySection() {
  return (
    <WindowContent>
      <p>This content gets the theme's border, background, and padding.</p>
    </WindowContent>
  );
}
```

### With style override

```jsx
<WindowContent
  styleSettings={{
    spacing: { padding: '1.5em' },
    borders: { width: '2px', style: 'dashed' }
  }}
>
  <p>Custom padding and border for this section.</p>
</WindowContent>
```

---

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `children` | ReactNode | — | Content to render inside the themed wrapper |
| `styleSettings` | object | context → defaults | Override theme for this instance |
| `style` | object | — | Additional CSS styles (applied on top of theme) |

---

## Theme Properties Used

| Theme Key | Fallback | Effect |
|-----------|----------|--------|
| `window.backgroundColor` | `#1e1e2e` | Content area background |
| `window.borderColor` | `#89b4fa` | Border color |
| `borders.width` | `1px` | Border width |
| `borders.style` | `solid` | Border style (solid, dashed, double, etc.) |
| `spacing.padding` | `.75em` | Inner padding |
| `titleBar.textColor` | `#cdd6f4` | Text color |

---

## Motivation for Single Wrapper

The old pattern required three nested components:

```jsx
{/* OLD — three layers */}
<WindowInset>
  <WindowSpacing>
    <WindowInner>
      <p>Content</p>
    </WindowInner>
  </WindowSpacing>
</WindowInset>

{/* NEW — single wrapper */}
<WindowContent>
  <p>Content</p>
</WindowContent>
```

WindowContent produces the same visual result with less nesting and fewer edge cases (no margin leaking, no double borders).