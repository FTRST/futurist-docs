# Basic Setup
This covers walks through our pre-built template to setup a basic environment.

Additionally, included are ways to customize it for your own experience.

***
## Prerequisites
***
No specific OS is required, but be sure to have a typical setup for React projects:

* ```Node.js 18+```, which you can download here.
* Familiarity with a package manager, such as **npm** or **yarn**.

***
## About the Template
***
Per the [Architecture](../framework/architecture.md), futurist is broken out into three main parts, [Core](https://github.com/ftrst/futurist-core), [Sidebar](https://github.com/ftrst/futurist-sidebar), and [Applications](../development/example_apps.md).

This template uses Core and Sidebar as dependencies, using the latest version available.

It's meant to be ready to use, out-of-the-box, but you can easily fork either of those repos and use it as a dependency instead of the default.

***
## What to Expect
***
This guide references [futurist-react](https://github.com/ftrst/futurist-react).

The expected outcome of getting this project setup is:

* The desktop experience seen on [futurist.io](https://futurist.io)
* A sample [device state](../framework/standard_states)
* A basic [Application](../framework/app_walkthrough.md)

Within our docs, there should be enough information to cover ways to create a bespoke experience.

However, if there are questions, please ask on the [template GitHub](https://github.com/ftrst/futurist-react)!

***
## Using the Template
***

Clone the GitHub repo:

```git clone https://github.com/ftrst/futurist-react.git && cd futurist-react```

Now, install the packages. To do so, use one of the following:

|             | npm         | yarn       |
|-------------|-------------|------------|
| to install: | npm install | yarn add   |
| to start:   | npm start   | yarn start |

Now, navigate to [http://localhost:3000](http://localhost:3000) if it didn't open automatically.

To add more Applications, check out our guide for [adding Applications](adding_applications.md).