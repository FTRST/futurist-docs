# Adding Applications

***
## Adding Applications
***
To add in another Application, such as the ones from the [Examples](development/example_apps), there's a few easy steps required.

Please note: while the applications are open source and available on Github, **they are not published to npm**.

To retrieve them, you can build the applications from source or use our (soon to be released) package repo.

***
### 1) Install the Package
***
Applications are added ("installed") like any other npm package:

```npm install <application_name>```

For example, to add ```Quantum Coin Flip``` use the following:

```npm install ftrst-quantum-flip```

***
### 2) Import the Application
***
A manual configuration is required to add the application within the project.

To do this, you'll need to know the application id.

The README within the project should provide an identifier for the "app", as well as the main identifier for the app being added.

In the case of ```ftrst-quantum-flip``` the app id is ```qcf``` and the install is ```QuantumCoinFlip```.

So, to add this, you'll go to ```{your_directory}/src/components/Applications.js``` and add the line:

```import QuantumCoinFlip from 'ftrst-quantum-flip';```

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
      XCoord: 10,
      YCoord: 10,
    },
  },
];
```

To update this with ```ftrst-quantum-flip```, the final version would look like:

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
      xCoord: 10,
      yCoord: 10,
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

The ```ftrst-quantum-flip``` example does not require a separate state.