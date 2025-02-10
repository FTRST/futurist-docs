# Adding Applications

***
## Adding Applications
***
To add in another Application, such as the ones from the [Examples](development/example_apps), there's a few easy steps required.

***
### 1) Install the Package
***
Applications are installed like any other npm package:

```npm install <application_name>```

For example, to install ```Quantum Coin Flip```:

```npm install quantum-coin-flip```

***
### 2) Import the Application
***

***
### 3) Update the Shortcut Container
***
Once the Application is installed, manually update the ```shortcuts``` array.

This is then packed into the [ShortcutContainer](components/shortcutcontainer.md) to display [Shorcuts](components/shortcut.md), or icons.

The one included by default within the [futurist-core](arch/core.md) looks like this:
```
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
];
```

To update this with ```quantum-coin-flip```, the final version would look like:

```
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
];
```
***
### 4) Create the Application State (optional)
***
Applications refer to the [deviceDetail](arch/using_states) state for functionality and bounds updating.

However, some Applications also require their own state in order to function.

There are two standards in place to know if an Application requires its own state:

* Check the Readme: Any requirements for states should be included within the project Readme. 
* Check the States folder: Even if not directly notated, Applications should contain the required states via the ```States``` folder.

The ```quantum-coin-flip``` example does not require a separate state.