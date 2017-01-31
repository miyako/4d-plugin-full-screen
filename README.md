# 4d-plugin-full-screen-window
Control full screen status of a window on Mac

###Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
||<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|||

###Version

<img src="https://cloud.githubusercontent.com/assets/1725068/18940649/21945000-8645-11e6-86ed-4a0f800e5a73.png" width="32" height="32" /> <img src="https://cloud.githubusercontent.com/assets/1725068/18940648/2192ddba-8645-11e6-864d-6d5692d55717.png" width="32" height="32" />
 
##Syntax

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

###Remarks

~~For 32 bits, requires v14 build number >= ``172426``. The ``EX_GET_HWND`` entry point has been updated in this build; in earlier versions of v14, ``PA_GetWindowPtr()`` did nothing; it was a simple type cast.~~

For 64 bits,  requires ``15R3`` or later. The ``EX_GET_HWND`` entry point has been updated to return a ``NSWindow*``.

Using the standard API ``toggleFullScreen:`` or ``performClick:`` has undesired effects in 4D.

As a workaround, the plugin simulates a click event on the zoom button to enter full screen.

It does use the standard API to exit, since the zoom button is hidden, there is a redraw issue on the unzoomed window.To force update the window, the plugin deactivates the application immediately before zoom. But the transition image is not good, and the window is grayed out.
