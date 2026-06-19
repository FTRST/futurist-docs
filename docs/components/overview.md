# Component Overview

futurist-components exports 35+ components plus theme infrastructure, state utilities, and hooks. All are importable as named exports from `'futurist-components'`.

---

## Window System

| Component | Description |
|-----------|-------------|
| **BaseWindow** | Draggable + resizable window shell. Accepts `id`, `device`, `manipulateWindows`. Uses TitleBar and WindowContent internally. |
| **TitleBar** | Window title bar with maximize/minimize/close buttons. Used internally by BaseWindow. |
| **WindowContent** | Single wrapper for window content — themed border, background, padding, text. Replaces the deprecated WindowInset/WindowSpacing/WindowInner three-layer pattern. |
| **WindowTitle** | `<h4>` section header with themed bottom border. |

---

## Theme Infrastructure

| Export | Description |
|--------|-------------|
| **ThemeProvider** | Wraps your app; provides theme context to all components. Named export. |
| **useTheme** | Alias for `useStyleSettings` — returns the current resolved theme. |
| **useUpdateTheme** | Returns a function for deep-merge partial theme updates. |
| **useResetTheme** | Resets theme to `MODERN_THEME` and clears saved theme from localStorage. |
| **themes** | Object with 4 presets: `themes.modern`, `themes.retro`, `themes.light`, `themes.warm`. |
| **themeAtom** | Jotai atom holding the current theme. Set directly for full replacement. |
| **updateThemeAtom** | Jotai writable atom — deep merges partial updates. |
| **defaultTheme** | Alias for `themes.modern`. |
| **useStyleSettings** | Low-level hook: resolves `styleSettings` from prop → context → null. |
| **StyleSettingsContext** | React context created by ThemeProvider. |

---

## Form Controls

| Component | Description |
|-----------|-------------|
| **Button** | 3 variants: `default`, `primary`, `ghost`. Props: `label`, `action`, `variant`, `disabled`, `type`. |
| **Input** | Text input with styled placeholder (0.4 opacity). Props: `value`, `action`, `placeholder`, `type`, `name`. |
| **Select** | Styled dropdown. Props: `value`, `action`, `options[]` (`{value, label}`), `placeholder`. |
| **Textarea** | Multi-line input, `resize: vertical`. Props: `value`, `action`, `placeholder`, `rows`. |
| **Checkbox** | Hidden native input + custom `<span>` visual with `✓` checkmark. Props: `checked`, `action`, `label`. |
| **Toggle** | Animated 2.2em track with 0.9em thumb. Props: `checked`, `action`, `label`. |
| **Radio** | Custom circle (1.25em), border from theme. Props: `checked`, `onChange`, `label`. |
| **Slider** | Custom thumb in accent color. Props: `value`, `onChange`, `min`, `max`, `step`, `label`, `showValue`. |

---

## Display & Feedback

| Component | Description |
|-----------|-------------|
| **Badge** | 5 variants: `default`, `info`, `success`, `warning`, `danger`. Props: `label`, `variant`. |
| **Alert** | 5 variants + optional close button. Props: `children`, `variant`, `onClose`. |
| **Spinner** | CSS keyframe rotating ring. Props: `size` (default 1.2em). |
| **Divider** | Themed `<hr>`, color from `window.borderColor` at 30% opacity. |
| **ProgressBar** | Smooth width transition. Props: `value`, `max`, `showLabel`. |
| **Toast** | Auto-dismiss after 3s. Wraps in ToastProvider. Global `window.ftrstToast`. |
| **Modal** | Fixed overlay with header + footer. Props: `isOpen`, `onClose`, `title`, `children`, `footer`. |
| **Card** | Header + body + footer sections. Props: `header`, `children`, `footer`. |

---

## Charts

| Component | Description |
|-----------|-------------|
| **AreaChart** | SVG-based area chart. Props: `data`, `title`. |
| **BarChart** | SVG-based bar chart. Props: `data`, `title`. |
| **LineChart** | SVG line chart. Props: `data`, `title`. |
| **HeatmapChart** | Grid-based colored cells. Props: `data`, `title`. |
| **Sparkline** | Inline SVG sparkline. Props: `data`, `width`, `height`. |

No PieChart — intentionally omitted.

---

## Desktop Patterns

| Component | Description |
|-----------|-------------|
| **Shortcut** | Desktop icon. Props: `width`, `icon`, `name`, `action`. |
| **ShortcutContainer** | Renders an array of Shortcuts. Props: `device`, `shortcuts[]`, `manipulateWindows`. |
| **Tab** | Individual tab button. Used inside TabContainer. |
| **TabContainer** | Tabbed container. Props: `tabComponents: {tabName: () => JSX}`. |
| **ComponentShowcase** | Scrollable demo of every component with live chart data. |
| **DevPlayground** | Dev sandbox: theme presets, window spawn, theme copy/paste, debug panel. |
| **Customizer** | Theme customization panel. |

---

## State Utilities

```js
import { useDeviceDetail, windowManipulatorAtom, deviceDetailAtom } from 'futurist-components';
```

| Export | Description |
|--------|-------------|
| **useDeviceDetail** | Hook listening to window.resize; returns `{ width, height, type, appWidth, deskSpace, windows[] }`. |
| **deviceDetailAtom** | Raw device detail atom. |
| **windowManipulatorAtom** | Single writable atom dispatching `{type, window}` actions. |
| **getWindowAtom(id)** | Derived atom for a specific window by id. |

---

## Utility Functions

```js
import { openWindow, closeWindow, bringToFront, resizeWindow } from 'futurist-components';
```

All accept `manipulateWindows` as first argument:

| Function | Usage |
|----------|-------|
| `openWindow(manipulateWindows, windowData)` | Opens a new window |
| `closeWindow(manipulateWindows, id)` | Closes window by id |
| `bringToFront(manipulateWindows, id)` | Brings window to front (z-index 99999) |
| `resizeWindow(manipulateWindows, id, newSize)` | Updates dimensions / maximize state |

```js
import { nestedInputChange, tabSelector } from 'futurist-components';
```

---

## Deprecated Components

| Component | Replacement |
|-----------|-------------|
| **WindowInset** | Use `WindowContent` |
| **WindowSpacing** | Use `WindowContent` |
| **WindowInner** | Use `WindowContent` |

These old three-layer wrappers are still exported for backwards compatibility but will be removed in a future version. `WindowContent` replaces all three in a single component.