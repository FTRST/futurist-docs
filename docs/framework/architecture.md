# Architecture

This section covers the architecture of **futurist-components** — the component system, theming, state management, and window system.

---

## Overview

futurist-components is a React UI kit built with:

- **React 18** — functional components, hooks, forwardRef
- **styled-components v6** — CSS-in-JS with transient `$` props for DOM safety
- **Jotai 2** — atomic state management for theme, device dimensions, and window state
- **react-draggable** — window dragging
- **re-resizable** — window resizing
- **Vite** — library mode build

---

## Theming System

All visual properties are driven by a single `styleSettings` object with three-layer resolution:

```
prop → context (ThemeProvider) → hardcoded defaults
```

### ThemeProvider

Wraps your app tree and provides the current theme via `StyleSettingsContext`:

```jsx
<ThemeProvider>
  <App />
</ThemeProvider>
```

Components read theme values with optional chaining, so any key can be omitted:

```js
color: ${({ $s }) => $s?.titleBar?.textColor || '#cdd6f4'};
```

### Theme Shape

```js
{
  window:     { backgroundColor: '#1e1e2e', borderColor: '#89b4fa' },
  titleBar:   { backgroundColor: '#181825', textColor: '#cdd6f4' },
  dimensions: { minWidth: 200, minHeight: 150 },
  spacing:    { padding: '.75em', margin: '0' },
  borders:    { width: '1px', style: 'solid' },
  button:     { primaryText: '#cdd6f4', primaryBg: '#45475a' },
}
```

### Four Presets

```js
import { themes } from 'futurist-components';

themes.modern   // Catppuccin Mocha-inspired dark (default)
themes.retro    // Green-on-black CRT
themes.light    // Clean light
themes.warm     // Earthy brown/orange
```

See [ThemeProvider](../components/themeprovider.md) for full details.

---

## State Management (Jotai)

### Device State

`deviceDetailAtom` tracks the viewport and window list:

```js
{
  width: 1366,          // current viewport width
  height: 768,          // current viewport height
  type: 'desktop',      // 'desktop' | 'mobile'
  appWidth: 1366,       // usable width (adjusts for sidebar)
  deskSpace: { width: 1366, height: 768 },
  windows: []           // array of window objects
}
```

**`useDeviceDetail()`** — hook that listens to `window.resize` and returns device state.

### Window Manipulation

**`windowManipulatorAtom`** — single writable atom dispatching action objects:

| Type | Effect |
|------|--------|
| `add` | Pushes a new window to `device.windows[]` |
| `remove` | Filters out the window by id |
| `update` | Merges properties (resize, maximize state) |
| `reindex` | Brings window to front (zIndex: 99999) |

**Utility functions** wrapping the atom:

```js
import { openWindow, closeWindow, bringToFront, resizeWindow } from 'futurist-components';

openWindow(manipulateWindows, windowData);
closeWindow(manipulateWindows, id);
bringToFront(manipulateWindows, id);
resizeWindow(manipulateWindows, id, { width, height, maximize, prevWidth, prevHeight });
```

### Theme Atom

```js
import { themeAtom, updateThemeAtom, resetThemeAtom } from 'futurist-components';

// Read current theme
const theme = useAtomValue(themeAtom);

// Deep-merge partial update
const update = useSetAtom(updateThemeAtom);
update({ titleBar: { textColor: '#fab387' } });

// Full replace
useSetAtom(themeAtom)(themes.light);
```

---

## Window System

### BaseWindow

Each window instance is a `BaseWindow` component that:

1. Reads its dimensions from `device.windows[]` by `id`
2. Initializes position cascading from {30,30} by 25px per window
3. Provides drag via react-draggable (handle: `.modal-title-bar`, bounds: parent)
4. Provides resize via re-resizable (min from `styleSettings.dimensions`)
5. Manages maximize/minimize with saved/restored prev dimensions
6. Re-indexes z-index on click (target: 99999, others by array order)

### Component Tree

```
BaseWindow
├── styled.div (StyledWindow — border, background, absolute position)
│   ├── TitleBar (.modal-title-bar — drag handle)
│   │   ├── StyledMaximizeButton / StyledMinimizeButton
│   │   ├── StyledTitle (window title)
│   │   └── StyledCloseButton
│   └── re-resizable (content area)
│       └── WindowContent (inner wrapper — border, bg, padding)
│           └── {children}
```

---

## Styling Conventions

### Transient `$` Props

All style-driving props use the `$` prefix — required by styled-components v6 to prevent React DOM warnings:

```js
const StyledDiv = styled.div`
  color: ${({ $s }) => $s?.titleBar?.textColor || '#cdd6f4'};
  background: ${({ $s }) => $s?.window?.backgroundColor || '#1e1e2e'};
`;
```

Never pass `styleSettings`, `theme`, or raw style objects as non-transient props.

### Inline Styling

Prefer inline destructured template literals over `css` helper functions:

```js
// GOOD — inline
const Header = styled.h3`
  color: ${({ $s }) => $s?.titleBar?.textColor};
`;

// AVOID — unnecessary indirection
const headerStyle = (s) => css` color: ${s?.titleBar?.textColor}; `;
const Header = styled.h3` ${p => headerStyle(p.$s)} `;
```

### Defaults Must Be Modern

Every `||` fallback uses Catppuccin Mocha colors (`#cdd6f4`, `#1e1e2e`, `#89b4fa`, `#45475a`, `#181825`) — never retro green-on-black.