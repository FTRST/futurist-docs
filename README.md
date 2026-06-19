# Futurist Docs

Documentation for [**futurist-components**](https://github.com/xtrem3/futurist-components) — a React UI kit for building desktop-like experiences in the browser.

> **Note:** This documentation (and futurist-components as a whole) is still in beta. Some items may not be up-to-date.

---

## About the Library

futurist-components provides draggable/resizable windows, a theme-driven component system with 4 built-in presets, form controls, charts, and desktop patterns like shortcuts and tab containers — all styled via a unified `styleSettings` object.

Key features:
- **Theme-driven** — all visual properties resolve from `styleSettings` (prop → context → defaults)
- **Window system** — drag, resize, maximize, minimize, z-index stacking via Jotai atoms
- **Works out of the box** — Modern theme (Catppuccin Mocha-inspired) is the default
- **No-nonsense** — named exports, single import, no configuration required

---

## Contents

- [Getting Started](docs/index.md) — introduction and quick start
- [Component Overview](docs/components/overview.md) — full component index
- [Architecture](docs/framework/architecture.md) — theming, state, window system
- [Theme Provider](docs/components/themeprovider.md) — ThemeProvider, useTheme, presets
- [Application Walkthrough](docs/framework/app_walkthrough.md) — building with components
- [Setup Guide](docs/setup_guide/quick_start.md) — install and configure
- [Example Applications](docs/development/example_apps.md) — reference implementations

---

## Quick Install

```bash
yarn add futurist-components
```

## Local Development

```bash
git clone https://github.com/xtrem3/futurist-components
cd futurist-components
yarn        # install
yarn dev    # dev server on port 5173
yarn build  # production build
yarn test   # run tests
yarn lint   # lint
```

---

## Contributing

Want to improve these docs? [Make a pull request](https://github.com/xtrem3/futurist-docs).
Interested in extending the component library itself? See the [GitHub repo](https://github.com/xtrem3/futurist-components).