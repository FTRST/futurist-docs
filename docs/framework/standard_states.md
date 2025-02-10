# Standard States
This article walks through the standard States, what they are, and how they're used.

***
## State References
***
States in many projects are referenced values.

Futurist has a few different States.

How States differ 

Data from applications or the window itself can be referenced across them using shared states.

A specific example is the ```deviceDetail``` state, which contains the current height and width of the window.

```Core``` contains an event listener to update on changes in window dimensions.

This updates the ```deviceDetail``` state with the newest resolution, which then updates the bounds for subsequent applications.


It's important to note that states, as well as their location, are **expected**.

This means releases of Core, Sidebar, or Applications should note what are the required fields for them to function.


***
## Standard States
***
Here's some state standards..

***
### DeviceDetail
***
```deviceDetail``` is a state included within the [futurist-core](core.md).

It creates an object that looks like this:

```
{
    width: __window_width__,
    height: __window_height__,
    windows: []
}
```

The ```width``` and ```height``` are the current dimensions of the usable desktop area.

These are referenced as the bounds when dragging Application windows, so it doesn't escape the usable space.

The ```windows``` array of window objects.

***
#### Window Object
***
[futurist-core](core.md) shows the desktop interface, including the [Shortcuts](../components/shortcut.md).

When a Shortcut is opened, a window object is added to the ```windows``` array.

This