# Input

This section covers the **Input** component — a styled text input field with theme support.

---

## Purpose

Input is a themed replacement for the standard HTML `<input>`. It inherits text color, background, and border from the current theme, with focus highlighting and placeholder styling.

---

## Usage

```jsx
import { Input } from 'futurist-components';

function App() {
  const [value, setValue] = React.useState('');

  return (
    <Input
      value={value}
      action={(e) => setValue(e.target.value)}
      placeholder="Type something..."
    />
  );
}
```

---

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `value` | string | — | Current input value |
| `action` | function | — | `onChange` handler (receives the event) |
| `placeholder` | string | — | Placeholder text (0.4 opacity styled) |
| `type` | string | `'text'` | HTML input type (e.g. `'password'`, `'email'`) |
| `name` | string | — | HTML `name` attribute |
| `variant` | string | `'default'` | Reserved for future use |
| `style` | object | — | Additional CSS styles |
| `styleSettings` | object | context → defaults | Override theme for this input |

---

## Theming

Input reads these keys from `styleSettings`:

| Key | Fallback | Effect |
|-----|----------|--------|
| `titleBar.textColor` | `#cdd6f4` | Text + focus border color |
| `button.primaryBg` | `#45475a` | Input background |
| `window.borderColor` | `#89b4fa` | Default border color |

On focus, the border transitions to `titleBar.textColor`. Placeholder text has 0.4 opacity.

```jsx
<Input
  value={value}
  action={handleChange}
  styleSettings={{
    window: { borderColor: '#cba6f7' },
    titleBar: { textColor: '#cba6f7' }
  }}
/>
```