# Basic Setup

This covers setting up a project using **futurist-components** from scratch.

---

## Prerequisites

- Node.js 18+
- Familiarity with a package manager (npm or yarn)

---

## Create a New Project

```bash
# Using Vite (recommended)
npm create vite@latest my-desktop-app -- --template react
cd my-desktop-app
```

---

## Install futurist-components

```bash
yarn add futurist-components
# or
npm install futurist-components
```

---

## Set Up Your App

Create a minimal setup in `src/App.jsx`:

```jsx
import { ThemeProvider, useDeviceDetail, useSetAtom, windowManipulatorAtom } from 'futurist-components';

function App() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  const shortcuts = [
    {
      icon: 'src/icons/app-icon.png',
      title: 'My App',
      id: 'my-app',
      windowData: {
        id: 'my-app',
        title: 'My App',
        width: '500px',
        height: '400px',
      },
    },
  ];

  return (
    <ThemeProvider>
      <ShortcutContainer
        device={device}
        shortcuts={shortcuts}
        manipulateWindows={manipulateWindows}
      />
      <BaseWindow
        id="my-app"
        device={device}
        manipulateWindows={manipulateWindows}
      >
        <p>Your application content.</p>
      </BaseWindow>
    </ThemeProvider>
  );
}
```

Add the necessary imports:

```jsx
import { ShortcutContainer, BaseWindow } from 'futurist-components';
```

---

## Run the Dev Server

```bash
yarn dev
# or
npm run dev
```

Navigate to [http://localhost:5173](http://localhost:5173).

---

## Adding More Applications

See [Adding Applications](adding_applications.md) for details on integrating additional apps.