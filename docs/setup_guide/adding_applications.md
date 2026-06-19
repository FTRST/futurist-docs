# Adding Applications

This guide covers adding new applications to a dashboard built with futurist-components.

---

## 1) Define the Shortcut

Add an entry to your `shortcuts` array:

```js
const shortcuts = [
  {
    icon: './icons/my-app.png',   // URL to shortcut icon
    title: 'My App',              // Display name
    id: 'my-app',                 // Unique identifier
    windowData: {
      id: 'my-app',
      title: 'My App',
      width: '400px',
      height: '300px',
    },
  },
];
```

---

## 2) Create the Application Component

```jsx
import { BaseWindow, Button, WindowContent, WindowTitle } from 'futurist-components';

function MyApp({ device, manipulateWindows }) {
  return (
    <BaseWindow
      id="my-app"
      device={device}
      manipulateWindows={manipulateWindows}
    >
      <WindowContent>
        <WindowTitle value="My App" />
        <p>Application content goes here.</p>
        <Button label="Action" action={() => alert('Hello!')} variant="primary" />
      </WindowContent>
    </BaseWindow>
  );
}
```

---

## 3) Render the Application

In your main app component, render the application alongside the ShortcutContainer:

```jsx
function Desktop() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  return (
    <>
      <ShortcutContainer device={device} shortcuts={shortcuts} manipulateWindows={manipulateWindows} />
      <MyApp device={device} manipulateWindows={manipulateWindows} />
    </>
  );
}
```

The BaseWindow will only render when a matching window exists in `device.windows[]` — clicking the shortcut adds it.

---

## 4) Application-Specific State (Optional)

If your app needs its own state beyond the device state:

```jsx
import { atom, useAtom } from 'jotai';

const appStateAtom = atom({
  count: 0,
  settings: {},
});

function MyApp({ device, manipulateWindows }) {
  const [appState, setAppState] = useAtom(appStateAtom);
  // ...
}
```

---

## See Also

- [Example Apps](../development/example_apps.md) — reference implementations
- [App Walkthrough](../framework/app_walkthrough.md) — detailed walkthrough of an application