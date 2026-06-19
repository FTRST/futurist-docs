# WindowTitle

This section covers the **WindowTitle** component — a section header with a themed bottom border.

---

## Purpose

WindowTitle renders an `<h4>` heading with a bottom border colored from the current theme. It is used for section headers within window content — not for interactive buttons.

---

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `value` | string | — | The heading text |
| `style` | object | — | Additional CSS styles |
| `styleSettings` | object | context → defaults | Override theme for this title |

---

## Usage

```jsx
import { WindowContent, WindowTitle } from 'futurist-components';

<WindowContent>
  <WindowTitle value="Settings" />
  <p>Your settings content here.</p>
</WindowContent>
```

---

## Theme Properties

| Key | Fallback | Effect |
|-----|----------|--------|
| `titleBar.textColor` | `#cdd6f4` | Heading text color |
| `window.borderColor` | `#89b4fa` | Bottom border color |
| `spacing.padding` | `.5em` | Heading padding (default from theme, overridden by `.75em` in WindowContent) |