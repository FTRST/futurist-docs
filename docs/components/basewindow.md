# BaseWindow
This section covers the **BaseWindow** component, its use, and capabilities.

***
## Purpose
***
BaseWindow is the outer shell or core of an Application.

It wraps the functionality of moving, resizing, and closing the Application.

***
## Usage
***

BaseWindow expects the following to be passed as parameters:

* **id**: The id for the Application.
* **device**: A function of the device state.
* **manipulateWindows**: An atom from the device state to manage window control.

Reference **Core Example** below for barebone usage.

This will create an Application that adheres to bounds and can be closed, moved, and resized.

To add content within it, BaseWindow expects to be wrapped around other components.

Reference **Children Example** below for extended usage.

***
## Core Example
***
```
import { useAtom, useSetAtom } from 'jotai';
import { useDeviceDetail } from './states/deviceDetail';
import { windowManipulatorAtom } from './states/deviceDetailState';

import BaseWindow from 'futurist-components';

function App() {
    const device = useDeviceDetail();
    const manipulateWindows = useSetAtom(windowManipulatorAtom);
    
    return (
        <>
            <BaseWindow device={device} manipulateWindows={manipulateWindows} />
        </>
    )
}
```

***
## Children Example
***
```
import { useAtom, useSetAtom } from 'jotai';
import { useDeviceDetail } from './states/deviceDetail';
import { windowManipulatorAtom } from './states/deviceDetailState';

import BaseWindow from 'futurist-components';

function App() {
    const device = useDeviceDetail();
    const manipulateWindows = useSetAtom(windowManipulatorAtom);
    
    return (
        <>
            <BaseWindow device={device} manipulateWindows={manipulateWindows}>
                <span>Here is a basic text</span>
            </BaseWindow>
        </>
    )
}
```

***
## Advanced Usage
***
BaseWindow optionally accepts raw CSS as a parameter to override styling.

The parameter name is aptly titled **style**. An example is below:

***
## Custom Style Example
***
```
import { useAtom, useSetAtom } from 'jotai';
import { useDeviceDetail } from './states/deviceDetail';
import { windowManipulatorAtom } from './states/deviceDetailState';

import BaseWindow from 'futurist-components';

function App() {
    const device = useDeviceDetail();
    const manipulateWindows = useSetAtom(windowManipulatorAtom);
    
    // Custom Styling
    const cStyle = 'background-color:blue;color;white';
    
    return (
        <>
            <BaseWindow 
                device={device} 
                manipulateWindows={manipulateWindows}
                style={`css${cstyle}`}
            >
                <span>Here is a basic text</span>
            </BaseWindow>
        </>
    )
}
```