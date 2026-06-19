# Quick Start

This guide walks you through setting up a project with **futurist-components**.

---

## Prerequisites

- Node.js 18+
- A package manager (yarn recommended, but npm works too)
- A React project (Vite, Create React App, Next.js, etc.)

---

## Installation

```bash
yarn add futurist-components
```

Or with npm:

```bash
npm install futurist-components
```

---

## Minimal Setup

Wrap your app with `ThemeProvider`, then use components:

```jsx
import { ThemeProvider, BaseWindow } from 'futurist-components';
import { useDeviceDetail, useSetAtom, windowManipulatorAtom } from 'futurist-components';

function App() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  return (
    <ThemeProvider>
      <BaseWindow
        id="my-app"
        device={device}
        manipulateWindows={manipulateWindows}
      >
        <h1>Hello, world!</h1>
      </BaseWindow>
    </ThemeProvider>
  );
}

export default App;
```

> **Note:** `useDeviceDetail()` listens to the window `resize` event. Call it once at the top of your app and pass `device` down.

---

## Next Steps

- [Component Overview](../components/overview.md) — browse all available components
- [ThemeProvider](../components/themeprovider.md) — theming and presets
- [Architecture](../framework/architecture.md) — learn how the system works
- [Example Apps](../development/example_apps.md) — see complete working examples