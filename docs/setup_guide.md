# Setup Guide

This section covers how to install and configure **futurist-components** in your project.

---

## Before Starting

Get familiar with the project:

- [Architecture](../framework/architecture.md) — understand the theming system, state management, and window system
- [Component Overview](../components/overview.md) — see what's available
- [App Walkthrough](../framework/app_walkthrough.md) — walk through building an application

---

## Prerequisites

- Node.js 18+
- Familiarity with a package manager like **npm** or **yarn**
- A React project (created via Vite, CRA, Next.js, etc.)

---

## Install

```bash
yarn add futurist-components
```

Or with npm:

```bash
npm install futurist-components
```

---

## Basic Setup

1. Wrap your app with `<ThemeProvider>`
2. Use `useDeviceDetail()` to get device/window state
3. Use `useSetAtom(windowManipulatorAtom)` to control windows
4. Render `<BaseWindow>` components with your content

```jsx
import { ThemeProvider, useDeviceDetail, useSetAtom, windowManipulatorAtom } from 'futurist-components';
import { Desktop } from './Desktop';

function App() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  return (
    <ThemeProvider>
      <Desktop device={device} manipulateWindows={manipulateWindows} />
    </ThemeProvider>
  );
}
```

---

## Adding Windows

Windows are managed through the `device.windows[]` state. Use the utility functions:

```js
import { openWindow, closeWindow, bringToFront, resizeWindow } from 'futurist-components';

// Open a new window
openWindow(manipulateWindows, {
  id: 'calculator',
  title: 'Calculator',
  width: 400,
  height: 500,
});

// Close
closeWindow(manipulateWindows, 'calculator');

// Bring to front
bringToFront(manipulateWindows, 'calculator');

// Resize / maximize
resizeWindow(manipulateWindows, 'calculator', {
  width: window.innerWidth,
  height: window.innerHeight,
  maximize: true,
  prevWidth: 400,
  prevHeight: 500,
});
```

---

## Theming

Switch themes on the fly:

```jsx
import { useUpdateTheme, themes } from 'futurist-components';

function ThemeSwitcher() {
  const update = useUpdateTheme();
  return (
    <div>
      <button onClick={() => update(themes.modern)}>Modern</button>
      <button onClick={() => update(themes.light)}>Light</button>
      <button onClick={() => update(themes.retro)}>Retro</button>
      <button onClick={() => update(themes.warm)}>Warm</button>
    </div>
  );
}
```

## Full Project Example

For a complete working project, check the [Example Apps](../development/example_apps.md) section.