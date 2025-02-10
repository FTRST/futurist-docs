***
## Before Getting Started
***
This guide provides the raw, copy / paste commands to get an environment set up and looking like [futurist.io](https://futurist.io).

For better understanding on the project, please (at least) read:

* [Framework Summary](framework/architecture) - To understand the roles of each of the parts being set up.
* [Application Walkthrough](framework/app_walkthrough) - For an in-depth walkthrough of an Application, how it works, etc.


***
## Prerequisites
***
No specific OS is required, but be sure to have a typical setup for React projects:

* ```Node.js 18+```, which you can download here.
* Slight familiarity with a package manager, such as **npm** or **yarn**.
* Ability to copy code someone else wrote for you.
* An internet connection (to download necessary packages, etc)

***
## Basic Setup
***
The architecture for Futurist is split into three parts: Core, Sidebar, and Applications.

**Core** is the only required package required.

In addition to the desktop interface, it includes a sampling setup of all extensions, such as:

* The device state
* A start Application

Clone the GitHub repo:

```git clone https://github.com/ftrst/futurist-core.git && cd futurist-core```

Now, install the packages. To do so, use one of the following:

Using **npm**

```npm install```

Or using **yarn**

```yarn add```

To run the project, simply use:

```npm start```

Or using yarn:

```yarn dev```

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

The one included by default within the [futurist-core](framework/core.md) looks like this:
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
Applications refer to the [deviceDetail](framework/standard_states) state for functionality and bounds updating.

However, some Applications also require their own state in order to function.

There are two standards in place to know if an Application requires its own state:

* Check the Readme: Any requirements for states should be included within the project Readme. 
* Check the States folder: Even if not directly notated, Applications should contain the required states via the ```States``` folder.

The ```quantum-coin-flip``` example does not require a separate state.