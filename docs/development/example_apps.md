# Example Applications

This page includes examples of purpose-built applications using futurist-components.

Each is open source for anyone to review and modify.

---

## Before Starting

Each example includes:

- The GitHub repo link
- Summary of the application
- The application ID for setup

---

## Local Development

To run the component library itself locally:

```bash
git clone https://github.com/xtrem3/futurist-components
cd futurist-components
yarn        # install
yarn dev    # Vite dev server (HMR, port 5173)
yarn build  # production build
yarn test   # run tests
yarn lint   # lint
```

### DevPlayground

futurist-components includes a **DevPlayground** for iterating on theming and window behavior. Mount it in any route:

```jsx
import { DevPlayground } from 'futurist-components';

function PlaygroundPage() {
  return <DevPlayground />;
}
```

Features:
- 4 theme presets (Modern, Retro, Light, Warm)
- Theme copy/import via JSON
- Window spawning with different content types
- Debug panel showing all windows (id, size, z-index)
- ComponentShowcase button for full component demo

### ComponentShowcase

A scrollable demo of every component with live chart data:

```jsx
import { ComponentShowcase } from 'futurist-components';

<ComponentShowcase />
```