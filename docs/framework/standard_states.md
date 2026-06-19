# Standard States

States in futurist-components are managed by **Jotai** — a primitive, flexible state management library for React.

---

## deviceDetailAtom

The core state atom for device/window management:

```js
{
  width: 1366,        // current viewport width
  height: 768,        // current viewport height
  type: 'desktop',    // 'desktop' | 'mobile' (derived from width)
  appWidth: 1366,     // usable width (adjusts for sidebar if present)
  deskSpace: {
    width: 1366,
    height: 768
  },
  windows: []         // array of window objects
}
```

### Hook

```js
import { useDeviceDetail } from 'futurist-components';

const device = useDeviceDetail();
// Returns the current device state, updated on window resize
```

### Window Object

Each entry in `device.windows[]`:

```js
{
  id: 'my-app',          // unique identifier
  title: 'My App',       // window title
  width: 400,            // current width
  height: 300,           // current height
  zIndex: 1,             // stacking order
  top: 30,               // y position
  left: 30,              // x position
  maximize: false,        // whether maximized
  prevWidth: null,       // previous width (before maximize)
  prevHeight: null,      // previous height (before maximize)
  prevTop: null,         // previous y (before maximize)
  prevLeft: null,        // previous x (before maximize)
}
```

---

## windowManipulatorAtom

A single writable atom that dispatches actions to manage windows:

### Actions

| Type | Description |
|------|-------------|
| `add` | Adds a new window to the windows array |
| `remove` | Removes a window by id |
| `update` | Merges properties on a window by id |
| `reindex` | Brings a window to front (zIndex 99999) |

### Usage

```js
import { useSetAtom, windowManipulatorAtom } from 'futurist-components';

const manipulateWindows = useSetAtom(windowManipulatorAtom);

// Add a window
manipulateWindows({
  type: 'add',
  window: {
    id: 'calculator',
    title: 'Calculator',
    width: 300,
    height: 400,
  }
});

// Close a window
manipulateWindows({ type: 'remove', window: { id: 'calculator' } });
```

---

## otherAtom

(Standard states doc TBD)

---

## Importing State

All state atoms and hooks are available from the top-level import:

```js
import {
  useDeviceDetail,
  deviceDetailAtom,
  windowManipulatorAtom,
  getWindowAtom,
} from 'futurist-components';
```