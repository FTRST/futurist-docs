# Button

This section covers the **Button** component, its use, style variants, and theming.

---

## Purpose

Button is an actionable interaction for users, just like a standard HTML `<button>`, but themed via the `styleSettings` system with three built-in visual variants.

---

## Usage

```jsx
import { Button } from 'futurist-components';

function App() {
  let count = 0;
  function increaseCount(value) {
    count += value;
  }
  return (
    <>
      <Button label="Click me" action={() => increaseCount(1)} variant="primary" />
      <span>Count: {count}</span>
    </>
  );
}
```

---

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | string | — | Text displayed on the button |
| `action` | function | — | `onClick` handler |
| `variant` | `'default'` \| `'primary'` \| `'ghost'` | `'default'` | Visual style variant |
| `disabled` | boolean | `false` | Disables the button (0.4 opacity, no cursor) |
| `type` | string | — | HTML `type` attribute (e.g. `'submit'`) |
| `style` | object | — | Additional CSS styles |
| `styleSettings` | object | context → defaults | Override theme for this button |

---

## Variants

| Variant | Text Color | Background | Border |
|---------|-----------|------------|--------|
| `default` | `button.primaryText` | `button.primaryBg` | `window.borderColor` |
| `primary` | `button.primaryBg` | `button.primaryText` | `button.primaryText` |
| `ghost` | `titleBar.textColor` | transparent | transparent (shows bg on hover) |

```jsx
<Button label="Default" action={handleClick} />
<Button label="Primary" action={handleClick} variant="primary" />
<Button label="Ghost" action={handleClick} variant="ghost" />
```

---

## Theming

Button reads these keys from `styleSettings`:

| Key | Fallback | Used For |
|-----|----------|----------|
| `button.primaryText` | `#cdd6f4` | Default text, primary background |
| `button.primaryBg` | `#45475a` | Default background, primary text |
| `window.borderColor` | `#89b4fa` | Default variant border |
| `titleBar.textColor` | `#cdd6f4` | Ghost variant text |

Override per-instance:

```jsx
<Button
  label="Custom"
  action={handleClick}
  styleSettings={{
    button: { primaryBg: '#a6e3a1', primaryText: '#1e1e2e' }
  }}
/>
```