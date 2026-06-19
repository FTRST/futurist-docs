# Futurist Components (React)

[**futurist-components**](https://github.com/xtrem3/futurist-components) is a React UI kit that provides desktop-like windowing experiences in the browser — draggable, resizable windows, desktop shortcuts, theme-driven styling, and a full library of form controls, charts, and display components.

![Futurist desktop example](../images/futurist-desktop-example.png)

> **Note:** This documentation is still in development. Some items may not be fully up-to-date.

---

## What's Included

- **Window System** — draggable, resizable BaseWindow with TitleBar, maximize/minimize/close
- **Theme Provider** — context-based theming via `ThemeProvider` with 4 built-in presets
- **Form Controls** — Button, Input, Select, Textarea, Checkbox, Toggle, Radio, Slider
- **Display & Feedback** — Badge, Alert, Spinner, ProgressBar, Divider, Toast, Modal, Card
- **Charts** — AreaChart, BarChart, LineChart, HeatmapChart, Sparkline
- **Desktop Patterns** — ShortcutContainer, TabContainer, DevPlayground
- **State Management** — Jotai atoms for device dimensions, window manipulation, and theming

---

## Quick Start

```bash
yarn add futurist-components
```

Wrap your app with ThemeProvider, then use any component:

```jsx
import { ThemeProvider, BaseWindow, Button } from 'futurist-components';
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
        <Button label="Hello" action={() => alert('Hi!')} variant="primary" />
      </BaseWindow>
    </ThemeProvider>
  );
}
```

---

## Component Library

Browse the [Component Overview](components/overview.md) for a full list of exports.

---

## Theming

All components inherit style from the nearest `ThemeProvider`. Pass `styleSettings` on individual components to override locally. Read more about [Theming](components/themeprovider.md).

---

## Contributing

- [GitHub](https://github.com/xtrem3/futurist-components) — issues, PRs, discussions
- Check the [Development Quick Start](development/quick_start.md) for local setup