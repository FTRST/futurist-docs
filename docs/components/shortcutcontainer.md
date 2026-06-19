# ShortcutContainer

This section covers the **ShortcutContainer** component — renders an array of desktop shortcut icons.

---

## Purpose

ShortcutContainer accepts an array of shortcut objects and renders them as draggable/clickable icons on the desktop. Clicking a shortcut opens the associated window in the device state.

---

## Props

| Prop | Type | Required | Description |
|------|------|----------|-------------|
| `device` | object | yes | Device state from `useDeviceDetail()` |
| `shortcuts` | array | yes | Array of shortcut objects (see shape below) |
| `manipulateWindows` | function | yes | State setter from `useSetAtom(windowManipulatorAtom)` |

---

## Shortcut Object Shape

Each entry in the `shortcuts` array:

```js
{
  icon: string,       // URL to shortcut icon image
  title: string,      // Display name (passed as `name` to Shortcut component)
  id: string,         // Unique identifier for this shortcut
  windowData: {       // Data passed to BaseWindow when opened
    id: string,       // Window id (matches the shortcut id)
    title: string,    // Window title
    width: string,    // Starting width (e.g. '300px')
    height: string,   // Starting height (e.g. '300px')
  }
}
```

---

## Usage

```jsx
import { useSetAtom } from 'jotai';
import { ShortcutContainer, useDeviceDetail, windowManipulatorAtom } from 'futurist-components';

function Desktop() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  const shortcuts = [
    {
      icon: 'https://futurist.io/icons/folder.png',
      title: 'My App',
      id: 'my-app',
      windowData: {
        id: 'my-app',
        title: 'My App',
        width: '400px',
        height: '300px',
      },
    },
  ];

  return (
    <ShortcutContainer
      device={device}
      shortcuts={shortcuts}
      manipulateWindows={manipulateWindows}
    />
  );
}
```

---

## Behavior

- Each shortcut is rendered via the **Shortcut** component
- Clicking/tapping a shortcut opens the window by adding its `windowData` to `device.windows[]`
- Only one instance of a window can be open — clicking again does not create a duplicate
- Shortcuts are draggable on desktop, with drag-to-click detection on mobile