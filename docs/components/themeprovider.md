# ThemeProvider

This section covers the theming system — **ThemeProvider**, **useStyleSettings**, **useTheme**, **useUpdateTheme**, **useResetTheme**, and the built-in theme presets.

---

## Purpose

All visual properties of futurist-components are driven by a single `styleSettings` object. The **ThemeProvider** wraps your application tree and makes the current theme available to every component via React context. Components automatically pick up the theme — no prop drilling required.

---

## Quick Start

```jsx
import { ThemeProvider, BaseWindow } from 'futurist-components';

function App() {
  return (
    <ThemeProvider>
      <YourApp />
    </ThemeProvider>
  );
}
```

That's it. All components inside `<ThemeProvider>` will use the default Modern theme.

---

## Built-in Presets

Access via the `themes` object:

```js
import { themes } from 'futurist-components';

themes.modern   // Catppuccin Mocha-inspired dark (default)
themes.retro    // Green-on-black CRT aesthetic
themes.light    // Clean light theme
themes.warm     // Earthy brown/orange tones
```

### Theme Shape

Every preset follows this structure:

```js
{
  window:     { backgroundColor: '#1e1e2e', borderColor: '#89b4fa' },
  titleBar:   { backgroundColor: '#181825', textColor: '#cdd6f4' },
  dimensions: { minWidth: 200, minHeight: 150 },
  spacing:    { padding: '.75em', margin: '0' },
  borders:    { width: '1px', style: 'solid' },
  button:     { primaryText: '#cdd6f4', primaryBg: '#45475a' },
}
```

Each component reads with optional chaining, so any key can be omitted and the component will use its hardcoded Modern fallback.

---

## Changing the Theme

### Deep Merge (partial update)

Use `useUpdateTheme()` — merges the passed object into the current theme, keeping unchanged keys:

```jsx
import { useUpdateTheme, themes } from 'futurist-components';

function ThemeSwitcher() {
  const update = useUpdateTheme();

  return (
    <div>
      <button onClick={() => update(themes.retro)}>Retro</button>
      <button onClick={() => update(themes.light)}>Light</button>
      <button onClick={() => update(themes.warm)}>Warm</button>
      <button onClick={() => update(themes.modern)}>Modern</button>
    </div>
  );
}
```

### Full Replacement

Set the atom directly:

```jsx
import { useSetAtom, themeAtom } from 'futurist-components';

const setTheme = useSetAtom(themeAtom);
setTheme(themes.warm);
```

### Reset to Default

```jsx
import { useResetTheme } from 'futurist-components';

const reset = useResetTheme();
reset(); // clears localStorage + resets atom to MODERN_THEME
```

---

## Per-Component Override

Pass `styleSettings` directly to any component to override the context for just that instance:

```jsx
<Button
  label="Special"
  action={handleClick}
  styleSettings={{
    button: { primaryBg: '#a6e3a1', primaryText: '#1e1e2e' }
  }}
/>
```

The resolution priority is: **prop** → **context** → **hardcoded defaults**.

---

## Hooks

| Hook | Returns | Usage |
|------|---------|-------|
| `useTheme()` | Current resolved theme object | Read the current theme in custom components |
| `useUpdateTheme()` | `(partialTheme) => void` | Deep-merge partial updates into the current theme |
| `useResetTheme()` | `() => void` | Reset to MODERN_THEME, clear localStorage |
| `useStyleSettings(override)` | Resolved style settings | Low-level hook for custom components |

---

## Saving Themes

Themes persist across page reloads via localStorage under the `ftrst-theme` key:

```js
import { saveTheme, loadSavedTheme } from 'futurist-components';

// Save any theme
saveTheme(customTheme);

// Load saved theme (returns null if none saved)
const saved = loadSavedTheme();
```

ThemeProvider automatically loads a saved theme on mount.

---

## Nested ThemeProvider

Each `<ThemeProvider>` creates its own scope. Nest them to give isolated sections of your app different themes:

```jsx
<ThemeProvider>
  <WindowContent>This uses the outer theme</WindowContent>

  <ThemeProvider>
    <WindowContent>This uses its own scope</WindowContent>
  </ThemeProvider>
</ThemeProvider>
```

---

## styleSettings Shape Reference

```js
{
  window: {
    backgroundColor: string,   // content area background
    borderColor: string,       // window border + accent color
  },
  titleBar: {
    backgroundColor: string,   // title bar background
    textColor: string,         // title bar + input text color
  },
  dimensions: {
    minWidth: number,          // minimum window width (px)
    minHeight: number,         // minimum window height (px)
  },
  spacing: {
    padding: string,           // CSS padding (e.g. '.75em')
    margin: string,            // CSS margin (e.g. '0')
  },
  borders: {
    width: string,             // CSS border-width (e.g. '1px')
    style: string,             // CSS border-style (e.g. 'solid')
  },
  button: {
    primaryText: string,       // text color on default/ghost buttons
    primaryBg: string,         // background on default/primary buttons
  },
}
```

All fields are optional. Missing fields fall back to Modern-themed defaults.