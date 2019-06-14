# Dillie-O's HammerSpoon Windows Management
(Extendend with much gratitude from [Miro's windows manager](https://github.com/miromannino/miro-windows-manager)

Hammerspoon provides an amazing foundation in which to make work more productive. Having enjoyed Spectacle, but needed just a little bit more, I stumbled upon Hammerspoon, and Miro's Window Manager, which I tweaked and extended a bit further to suit my ongoing needs.

## Features
Once installed, this script provided the following window management commands:

### Movement
* Move window to the left/right half of the screen (sized incrementally)
* Move window to the top/bottom half of the screen (sized incrementally)
* Move window to the corners of the screen (sized incrementally)
* Move window to the adjacent monitor (north/south/east/west)

### Sizing
* Adjust window to fit entire width of the screen
* Adjust window to fit entire height of the screen
* Adjust window to fit full screen (sized incrementally)
* Adjust window to fit in the center of the screen (full height, sized incrementally)

### Incremental Sizing
Most of the actions above include incremental sizing. This means that pressing the same action multiple times will yield a different size result. For example, moving the window to the left side of the screen will do it by half the first time, by a third the second time, and by 2/3rds the third time. This allows you to quick dock/size based on your needs.

## Installation (skip to step 4 if you already have Hammerspoon installed)

1. Install [Hammerspoon](https://www.hammerspoon.org)
2. Launch Hammerspoon, open preferences, and make sure Hammerspoon launches at login and you have enabled accessibility for the app (the icon will be green next to the button).
3. Extract the zip file into the `~/.hammerspoon/Spoons` folder. Note: The spoon file itself (MirADillieOWinspoon.spoon) is a module (folder) that consists of an `init.lua` file and a `docs.json` file. You need to navigate into this folder or open the .spoon file in a tool like Visual Studio Code if you want to make any edits.
4. In the Hammerspoon menu, select "Open Config" and add the following code that will configure the hotkeys and spoon to load. Note: This is code exists in your `~/.hammerspoon/init.lua` file.

```
local hyper = {"alt", "cmd"}
local hyperPlus = {"ctrl", "alt", "cmd"}

hs.loadSpoon("MiroWindowsManager")

hs.window.animationDuration = 0.3
spoon.MiroWindowsManager:bindHotkeys({
  up = {hyper, "up"},
  right = {hyper, "right"},
  down = {hyper, "down"},
  left = {hyper, "left"},
  fullscreen = {hyper, "f"},
  centerscreen = {hyper, "c"},
  monitoreast = {hyperPlus, "right"},
  monitorwest = {hyperPlus, "left"}
})
```
5. Save the config file and select the "Reload Config" option.
6. Enjoy your newfound window management power!


## Shortcuts

In the snippet above configure Miro'w Windows Manager in the following way:

### Hyper key

The hyper key is defined as `alt` + `cmd`. This means that each shortcut will start by pressing these two keys. If you consider this too verbose for your personal keyboard interactions, you can also change it, for example replacing it with an unused key (e.g. caps lock key) with [Karabiner](https://pqrs.org/osx/karabiner/) and [Seil](https://pqrs.org/osx/karabiner/seil.html.en) to act as hyper key.

### HyperPlus key

The hyper plus key is defined as `ctrl` + `alt` + `cmd`. This means that each shortcut will start by pressing these three keys. There were some actions that the arrows worked best for that were already taken, so you add another activator to the combination and life is good. You can always modify the `init.lua` file in your main Hammerspoon config if you want to map out the keystrokes differently

### Move in halves

 - `hyper` + `up`: move to the top half of the screen
 - `hyper` + `right`: move to the right half of the screen
 - `hyper` + `down`: move to the bottom half of the screen
 - `hyper` + `left`: move to the left half of the screen

By repeating these shortcuts the window is resized to be one third or two thirds and again in one half. 

### Move to corners

 - `hyper` + `up` + `right`: move the window to the top-right corner
 - `hyper` + `down` + `right`: move the window to the bottom-right corner
 - `hyper` + `up` + `left`: move the window to the top-left corner
 - `hyper` + `down` + `left`: move the window to the bottom-left corner

 When the window is in the corner, it will have one half of screen height and one half of screen width. 
 The arrows can be used to expand the height/width to be one third, two thirds or again one half. 
 For example if the window is in the top-right corner, pressing `hyper` + `up` the window height will be resized to be one third, while pressing `hyper` + `right` the window width will be resized to be one third; in this case `hyper` + `left` and `hyper` + `down` will move the window to the top-left and bottom-right corners, respectively.

### Expand to fit the entire height or width

These are useful in case the window is in one of the corners.

 - `hyper` + `up` + `down`: expand the height to fit the entire screen height
 - `hyper` + `right` + `left`: expand the width to fit the entire screen width

### Expand to fullscreen

 - `hyper` + `f`: expand to be full screen

Note that in case the window is resized to be a half of the screen, you can also use `hyper` + `up` + `down` (or `hyper` + `right` + `left`) to resize the window full screen.

As the other shortcuts, `hyper` + `f` can be pressed multiple times to obtain a centered window of three fourth and one half of height and width. This behaviour can be customized.

### Center screen

 - `hyper` + `c`: centers the window on the screen. This also sets the window height to the max value of the window. This is handy for things like web browsers on large displays where you don't want it taking up the entire width of the display, but also need it front and center for work.

Note that in case the window is resized to be a half of the screen, you can also use `hyper` + `up` + `down` (or `hyper` + `right` + `left`) to resize the window full screen.

As the other shortcuts, `hyper` + `c` can be pressed multiple times to obtain a centered window of one third, two thirds, and one half of width. This behaviour can be customized.

## Animations

The snippet above configures the animation to last `0.3s` with `hs.window.animationDuration = 0.3`. To remove the animations completely change this value to `0`.


## License (MIT)

Copyright (c) 2019 Sean Patterson

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
