# 4d-plugin-full-screen-window
Control full screen status of a window on Mac

### References

https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/FullScreenApp/FullScreenApp.html#//apple_ref/doc/uid/TP40010543-CH6-SW4

full screen mode (other than 32-bit carbon/QuickTime full screen mode) was introduced in 4D v14 and Mac OS X 10.7.

it seems the only way to invoke this is to simulate a click on the full screen button.

`[window toggleFullScreen:nil]` or `[[window standardWindowButton:NSWindowZoomButton]performClick:nil]` does not work.

as such, the plugin can only enter full screen, not return from it.

also, low-level automatic of mouse events require accesibility permisson.

## Syntax

```
fullscreen:=Get window full screen (window)
```

Parameter|Type|Description
------------|------|----
window|INT32|Window reference
fullscreen|INT32|``1`` if full screen

```
SET WINDOW FULL SCREEN (window;fullscreen)
```

Parameter|Type|Description
------------|------|----
window|INT32|Window reference
fullscreen|INT32|``1`` to enter full screen; ``0`` to exit full screen

### Remarks

For 64 bits,  requires ``15R3`` or later. The ``EX_GET_HWND`` entry point has been updated to return a ``NSWindow*``.

Using the standard API ``toggleFullScreen:`` or ``performClick:`` has undesired effects in 4D.

As a workaround, the plugin simulates a click event on the zoom button to enter full screen.

It does use the standard API to exit, since the zoom button is hidden, there is a redraw issue on the unzoomed window.To force update the window, the plugin deactivates the application immediately before zoom. But the transition image is not good, and the window is grayed out.
