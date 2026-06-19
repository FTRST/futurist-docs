# Development Quick Start

This section covers how to set up **futurist-components** for local development and contribution.

---

## Clone and Install

```bash
git clone https://github.com/xtrem3/futurist-components
cd futurist-components
yarn
```

---

## Available Commands

| Command | Description |
|---------|-------------|
| `yarn dev` | Start Vite dev server with HMR on port 5173 |
| `yarn build` | Production build for npm distribution |
| `yarn test` | Run tests with Vitest |
| `yarn lint` | Lint with ESLint |
| `yarn preview` | Preview production build |

---

## Project Structure

```
src/
├── components/        # 35+ component directories
│   ├── index.jsx     # Barrel export for all components
│   ├── BaseWindow/   # Window system
│   ├── Button/       # Form controls
│   ├── ThemeProvider/ # Theme infrastructure
│   ├── DevPlayground/ # Dev sandbox
│   └── ...
├── states/           # Jotai atoms (index.js exports all)
│   ├── deviceDetail.js
│   ├── deviceDetailState.js
│   └── themeState.js
├── hooks/            # Shared hooks (useStyleSettings)
├── utils/            # Utility functions
│   ├── windowControls.js
│   └── componentControls.js
├── contexts/         # React contexts (StyleSettingsContext)
└── index.jsx         # Main entry — re-exports everything
```

---

## Key Conventions

### Imports

All components use named imports from the same package:

```js
import { Button, BaseWindow, WindowContent } from 'futurist-components';
```

### Styling

- styled-components v6 with transient `$` props
- Theme values via `$s` (resolved styleSettings)
- Fallbacks default to Modern theme colors

### Adding a New Component

1. Create `src/components/MyComponent/MyComponent.jsx`
2. Use `React.forwardRef` and `useStyleSettings`
3. Add to `src/components/index.jsx`
4. Test via DevPlayground or ComponentShowcase