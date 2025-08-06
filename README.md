![deprecated](https://img.shields.io/badge/-deprecated-inactive)

use [miyako/4d-plugin-menu](https://github.com/miyako/4d-plugin-menu)

# 4d-plugin-full-screen
Invoke full screen mode on Mac

### References

[Implementing the Full-Screen Experience](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/FullScreenApp/FullScreenApp.html#//apple_ref/doc/uid/TP40010543-CH6-SW4)

full screen mode (other than 32-bit carbon/QuickTime full screen mode) was introduced in 4D v14 and Mac OS X 10.7.

it seems the only way to invoke this mode by code is to simulate a click on the full screen button.

`[window toggleFullScreen:nil]` or `[[window standardWindowButton:NSWindowZoomButton]performClick:nil]` does not work.

as such, the plugin can only enter full screen, not return from it.

also, low-level automation of mouse events require accesibility permisson by the user.

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
