# 4d-plugin-full-screen
Control full screen status of a window on Mac

### References

[Implementing the Full-Screen Experience](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/FullScreenApp/FullScreenApp.html#//apple_ref/doc/uid/TP40010543-CH6-SW4)

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
window|Integer|Window reference
fullscreen|Integer|``1`` if full screen

```
SET WINDOW FULL SCREEN (window;fullscreen)
```

Parameter|Type|Description
------------|------|----
window|Integer|Window reference
fullscreen|Integer|``1`` to enter full screen; ``0`` does nothing
