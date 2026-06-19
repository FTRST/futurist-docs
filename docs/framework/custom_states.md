# Custom States

Applications built with futurist-components can create their own Jotai atoms for application-specific state.

---

## When to Use Custom States

- Your application needs data that persists across re-renders
- Multiple components within your app need to share state
- You want to access the device state (`deviceDetailAtom`) alongside your own data

---

## Example: Quantum Coin Flip

The Quantum Coin Flip app uses a custom `selectedValue` state via `useState` (local to the component). For more complex apps, Jotai atoms are preferred:

```js
import { atom, useAtom } from 'jotai';

const flipResultAtom = atom(null);

function CoinFlipApp() {
  const [result, setResult] = useAtom(flipResultAtom);
  // ...
}
```

---

## Accessing Standard State

Custom state can reference the standard device state:

```js
import { atom, useAtomValue } from 'jotai';
import { deviceDetailAtom } from 'futurist-components';

const myAppAtom = atom((get) => {
  const device = get(deviceDetailAtom);
  // Derive from device state
  return {
    isMobile: device.type === 'mobile',
    windowCount: device.windows.length,
  };
});
```

---

## Sharing State Between Applications

Jotai atoms defined at the top level of an app or module scope can be imported by multiple components, making them a convenient way to share state between different parts of your dashboard.

For apps that need shared state (like BrainConnect streaming EEG data to ManageSessions), define atoms in a shared module:

```js
// states/sharedData.js
import { atom } from 'jotai';

export const brainwaveStreamAtom = atom([]);
export const sessionsAtom = atom([]);
```