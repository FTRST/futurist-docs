# TitleBar
This section covers the **TitleBar** component, its use, and capabilities.

***
## Purpose
***
TitleBar does not need to used directly.

It is used within [BaseWindow](basewindow.md) and includes the window label, as well as the close / maximize / minimize buttons.

***
## Usage
***
TitleBar expects the following to be passed as parameters:

* Title: The window label.
* expandAction: Handles the expansion to max window dimensions.
* closeAction: Handles the closing of the window.
* minimizeAction: Handles the collapse to previous dimensions before expanding.

***
## Code Example
***

Again, this code is typically handled automatically by passing the appropriate values into [BaseWindow](basewindow.md).

Below is how it would look if used directly:
```
<TitleBar
  ref={titleBarRef}
  title={windowDetails.title}
  expandAction={() =>
    resizeWindow(manipulateWindows, id, {
      width: device.width,
      height: device.height,
      maximize: true,
      prevWidth: windowDetails.width,
      prevHeight: windowDetails.height,
    })
  }
  closeAction={() => closeWindow(manipulateWindows, id)}
  minimizeAction={() =>
    resizeWindow(manipulateWindows, id, {
      width: windowDetails.preveWidth,
      height: windowDetails.prevHeight,
      maximize: false,
    })
  }
  maximize={windowDetails.maximize}
/>;
```