# Custom States
This article walks through States, what they are, how to use them, standard ones, and where custom ones are used.

***
## State References
***
States in many projects are referenced values.

Futurist has a few different States.

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