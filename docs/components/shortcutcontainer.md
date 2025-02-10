# ShortcutContainer
This section covers the **ShortcutContainer** component, its use, and capabilities.

***
## Purpose
***
ShortcutContainer accepts an array of objects.

The objects include the same data required to create [Shortcuts](shortcut.md).

***
## Code Example
***

Below, you can see the shortcuts array and how to use the ShortcutContainer:

```
import { useAtom, useSetAtom } from "jotai";
import { useDeviceDetail } from "./states/deviceDetail";
import { windowManipulatorAtom } from "./states/deviceDetailState";

import ShortcutContainer from "futurist-components";

function App() {
  const device = useDeviceDetail();
  const manipulateWindows = useSetAtom(windowManipulatorAtom);

  const shortcuts = [
    {
      icon: "./icons/qcf.png",
      title: "Quantum Coin Flip",
      id: "qcf",
      windowData: {
        id: "qcf",
        title: "Quantum Coin Flip",
        width: "300px",
        height: "300px",
      },
    },
    {
      icon: "./icons/web-shortcut.png",
      title: "NetXplorer",
      id: "nxp",
      windowData: {
        id: "nxp",
        title: "NetXplorer",
        width: "300px",
        height: "300px",
      },
    },
    {
      icon: "./icons/web-shortcut.png",
      title: "HConnector",
      id: "scf",
      windowData: {
        id: "scf",
        title: "HConnector",
        width: "300px",
        height: "300px",
      },
    },
  ];

  return (
    <>
      <ShortcutContainer
        device={device}
        shortcuts={shortcuts}
        manipulateWindows={manipulateWindows}
      />
    </>
  );
}
```

## Usage
BaseWindow expects the following to be passed as parameters:
