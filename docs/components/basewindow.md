# BaseWindow

This section covers the **BaseWindow** component — the draggable, resizable window shell for your application.

---

## Purpose

BaseWindow is the outer shell of any windowed application. It wraps your content with drag (via react-draggable), resize (via re-resizable), maximize/minimize, close, and z-index stacking — all themed through the `styleSettings` system.

BaseWindow uses **TitleBar** (for the window controls) and **WindowContent** (for the themed content area) internally.

---

## Usage

BaseWindow expects the following props:

| Prop | Type | Required | Description |
|------|------|----------|-------------|
| `id` | string | yes | Unique identifier for this window (must match a window in `device.windows[]`) |
| `device` | object | yes | Device state from `useDeviceDetail()` |
| `manipulateWindows` | function | yes | State setter from `useSetAtom(windowManipulatorAtom)` |
| `children` | ReactNode | no | Content to render inside the window |
| `styleSettings` | object | no | Override theme for this specific window |

### Core Example

```jsx
import { useSetAtom } from 'jotai';
import { BaseWindow, useDeviceDetail, windowManipulatorAtom } from 'futurist-components';

function App() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  return (
    <BaseWindow
      id="my-app"
      device={device}
      manipulateWindows={manipulateWindows}
    />
  );
}
```

### With Children

```jsx
<BaseWindow id="my-app" device={device} manipulateWindows={manipulateWindows}>
  <p>Your application content goes here.</p>
</BaseWindow>
```

### With styleSettings Override

```jsx
<BaseWindow
  id="special"
  device={device}
  manipulateWindows={manipulateWindows}
  styleSettings={{
    window: { backgroundColor: '#313244', borderColor: '#cba6f7' }
  }}
>
  <p>This window has a different background and border.</p>
</BaseWindow>
```

---

## Window Lifecycle

1. **Create a window** — add a window object to `device.windows[]` via `openWindow()` or direct atom dispatch
2. **BaseWindow renders** — positioned by its index (cascading from {30,30} by 25px)
3. **Drag** — via react-draggable with `bounds="parent"` (constrained to the desktop area)
4. **Resize** — via re-resizable, minimum size from `styleSettings.dimensions` (default 200×150)
5. **Maximize** — fills viewport; stores previous dimensions for later restore
6. **Minimize** — restores previous dimensions and position
7. **Close** — removes window from `device.windows[]`
8. **Z-index** — clicking brings target to front (99999), others re-index by array order

---

## Window Object Shape

Each entry in `device.windows[]` should have:

```js
{
  id: string,           // unique identifier
  title: string,        // window title shown in TitleBar
  width: number|string, // initial width (px or CSS)
  height: number|string,// initial height (px or CSS)
  zIndex: number,       // stacking order
  top: number,          // optional: initial y position (px)
  left: number,         // optional: initial x position (px)
  maximize: boolean,    // whether the window is maximized
  prevWidth: number,    // previous width before maximize
  prevHeight: number,   // previous height before maximize
  prevTop: number,      // previous y before maximize
  prevLeft: number,     // previous x before maximize
}
```

---

## Theme Properties Used

| Theme Key | Fallback | Effect |
|-----------|----------|--------|
| `window.borderColor` | `#89b4fa` | Window border + button accent |
| `window.backgroundColor` | `#1e1e2e` | Content area (behind WindowContent) |
| `borders.width` | `1px` | Window border width |
| `borders.style` | `solid` | Window border style |
| `dimensions.minWidth` | 200 | Minimum resize width |
| `dimensions.minHeight` | 150 | Minimum resize height |
| `button.primaryBg` | `#45475a` | Maximize/minimize button background |
| `button.primaryText` | `#cdd6f4` | Close button background |
| `titleBar.backgroundColor` | `#181825` | Title bar area |
| `titleBar.textColor` | `#cdd6f4` | Title text