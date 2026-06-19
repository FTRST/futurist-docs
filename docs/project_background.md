# Project Background

This section covers the core ideas behind futurist-components and the desktop-like UI paradigm.

---

## Key Takeaways

- **Browser-native** — runs in any modern browser, cross-platform by default
- **Component-driven** — a library of ready-to-use components reduces boilerplate
- **Theme-driven** — one `styleSettings` object drives all visual properties
- **Works out of the box** — Modern theme is the default; no configuration needed

---

## Background

futurist-components started as a way to simplify building desktop-like interfaces in the browser. Desktop metaphors — draggable windows, clickable icons, movable/resizable panels — are universally understood interaction patterns, but implementing them from scratch requires solving the same problems repeatedly:

- Drag with bounds checking
- Resize with minimum/maximum constraints
- Z-index stacking when multiple windows overlap
- State management for window positions, sizes, and visibility
- Consistent theming across all visual elements

futurist-components packages all of this into a ready-to-use library. Rather than wiring up react-draggable, re-resizable, and Jotai atoms yourself, you import `BaseWindow` and get a fully functional window.

---

## Project Goals

- **Standardization** — consistent theming and behavior across all components
- **Reducing complexity** — one import, one theme object, minimal boilerplate
- **Clear defaults** — Modern theme looks good without any configuration
- **Extensibility** — override any style at the prop, component, or context level

---

## Related Links

- [futurist.io](https://futurist.io) — Home page
- [GitHub: futurist-components](https://github.com/xtrem3/futurist-components)
- [GitHub: futurist-docs](https://github.com/xtrem3/futurist-docs)