# TitleBar

This section covers the **TitleBar** component — the window title bar with maximize/minimize/close buttons.

---

## Purpose

TitleBar displays the window title, a maximize/minimize toggle button, and a close button. It is used internally by **BaseWindow** and is typically not used directly.

It serves as the drag handle (CSS class `.modal-title-bar`) for react-draggable.

---

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Window title text displayed in the bar |
| `expandAction` | function | — | Handler for maximize (expands to viewport size) |
| `closeAction` | function | — | Handler for close (removes window) |
| `minimizeAction` | function | — | Handler for minimize (restores previous size) |
| `maximize` | boolean | `false` | Whether the window is currently maximized |
| `style` | object | — | Additional CSS styles |
| `styleSettings` | object | context → defaults | Override theme for this title bar |

---

## Button Behavior

- **Maximize button** (`⛶`) — shown when `maximize` is `false`. Calls `expandAction`. Buttons styled with `button.primaryBg` and `titleBar.textColor`.
- **Minimize button** (`⤡`) — shown when `maximize` is `true`. Calls `minimizeAction`.
- **Close button** (`✕`) — always shown. Calls `closeAction`. Styled with the theme's accent color.

TitleBar is designed to work with the `resizeWindow` utility from `windowControls`:

```jsx
import { resizeWindow, closeWindow } from 'futurist-components';

// In your component:
<TitleBar
  ref={titleBarRef}
  title={windowDetails.title}
  expandAction={() =>
    resizeWindow(manipulateWindows, id, {
      width: device.width,
      height: device.height,
      maximize: true,
      prevWidth: windowDetails.width,
      prevHeight: windowDetails.height,
    })
  }
  closeAction={() => closeWindow(manipulateWindows, id)}
  minimizeAction={() =>
    resizeWindow(manipulateWindows, id, {
      width: windowDetails.prevWidth,
      height: windowDetails.prevHeight,
      maximize: false,
    })
  }
  maximize={windowDetails.maximize}
/>
```

---

## Theme Properties

| Key | Fallback | Effect |
|-----|----------|--------|
| `titleBar.backgroundColor` | `#181825` | Title bar background |
| `titleBar.textColor` | `#cdd6f4` | Title text + maximize/minimize button |
| `window.borderColor` | `#89b4fa` | Bottom border + close button background |
| `button.primaryBg` | `#45475a` | Maximize/minimize button background |
| `borders.style` | `solid` | Bottom border style |
| `borders.width` | `1px` | Bottom border width |

---

## Forwarded Refs

TitleBar uses `React.forwardRef`. BaseWindow measures `titleBarRef.current.offsetHeight` to calculate the content area height after subtracting the title bar height.