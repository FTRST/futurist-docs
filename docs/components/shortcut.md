# Shortcut

This section covers the **Shortcut** component — the desktop icon that launches applications.

---

## Purpose

Shortcut is the icon shown on the desktop. On click or tap, it opens the connected application. On mobile, it uses drag-to-click detection (fires click only if drag ≤ 10px within 300ms). On desktop, it is draggable via react-draggable.

---

## Props

| Prop | Type | Required | Description |
|------|------|----------|-------------|
| `width` | string/number | yes | Starting width of the window when opened |
| `icon` | string | yes | URL to the icon image |
| `name` | string | yes | Display name shown below the icon |
| `action` | function | yes | Function to open the window (called on click/tap) |

---

## Usage

Shortcuts are typically rendered through **ShortcutContainer**, not used directly:

```jsx
import { ShortcutContainer } from 'futurist-components';

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

<ShortcutContainer
  device={device}
  shortcuts={shortcuts}
  manipulateWindows={manipulateWindows}
/>
```

See [ShortcutContainer](shortcutcontainer.md) for details on the shortcuts array shape.