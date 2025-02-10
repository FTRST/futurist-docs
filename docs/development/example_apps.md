# Example Apps
This page includes examples of purpose-built applications.

Each is open source for anyone to review and modify.
***
## Before Reviewing
***

Each example includes:

* The GitHub repo link
* Summary of the Application
* The Application ID for setup

The GitHub repo for each Application includes more specific information.

!!! note "Questions / Problems / Contributions"

    If any problems arise using them, or you'd like to contribute, [make a pull request](https://github.com/ftrst/futurist-react)!


***
## Quantum Coin Flip
***

* GitHub link is here: [Quantum Coin Flip](https://github.com/ftrst/futurist-qcf)
* Application ID: ```qcf```

***
### Application Summary
***

This Application uses [TabContainer](../components/tabcontainer.md) screens.

It fetches data from an external endpoint and re-renders the content within the window after receiving it.

A full walkthrough of this Application, including an explanation of how it works and all components, [can be found here](../framework/app_walkthrough.md).
***
## NetXplorer
***

* GitHub link is here: [NetXplorer](https://github.com/ftrst/futurist-nxp)
* Application ID: ```nxp```

***
### Application Summary
***

This Application relies on an external web service that asynchronously fetches, renders, and returns HTML content.

The 

***
## Brain Connect
***

* GitHub link is here: [BrainConnect](https://github.com/ftrst/futurist-nxp)
* Application ID: ```bcp```

***
### Application Summary
***

This Application focuses on Web APIs to interact with real-world hardware, specifically EEG headsets.

It enables a bluetooth connection to the headset and starts the data stream to the browser.

A custom state is used to store the data stream, which can be referenced by other Applications.

***
## Manage Sessions
***

* GitHub link is here: [ManageSessions](https://github.com/ftrst/futurist-nxp)
* Application ID: ```mxs```

***
### Application Summary
***

This Application makes use of the custom state from ```BrainConnect```.

With the constant stream of data, *Manage Sessions* creates slices of this data over a set of time.

These slices are called Sessions. They can be exported or imported.

***
## Session Review
***

* GitHub link is here: [SessionReview](https://github.com/ftrst/futurist-nxp)
* Application ID: ```srw```

***
### Application Summary
***

This Application makes use of the custom ```BrainConnect``` state.

It charts the live view of incoming data streamed from the connected headset.

Similarly, if Sessions are available, they can be reviewed.
