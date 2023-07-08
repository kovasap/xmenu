# XMenu

XMenu is a menu utility for X.
XMenu receives a menu specification in stdin, shows a menu for the user
to select one of the options, and outputs the option selected to stdout.
XMenu can be controlled both via mouse and via keyboard.

In order to generate a menu of applications based on .desktop entries,
as specified by XDG, checkout [xdg-xmenu](https://github.com/OliverLew/xdg-xmenu)
by [OliverLew](https://github.com/OliverLew).

Check out my other project, [xclickroot](https://github.com/phillbush/xclickroot) for an application that can
spawn xmenu by right clicking on the root window (i.e. on the desktop).

## Options
XMenu understand the following command-line options.

* `-N name`:      Specify a resource/instance name for XMenu.
* `-p position`:  Specify a position to place XMenu.
* `-t`:           Enable menus to be torn off.
* `-w`:           Initiate XMenu as a regular window.

## Environment
XMenu understands the following environment variable.

* `ICONPATH`: Colon-separated list of directories to search for images.

## Input
XMenu reads menu entries from standard input.
Each entry correspond to a line; and lines can be indented to represent
submenus.  Tab separates the label from the string to be output.  An
optional image can be inserted on the line to be rendered as the entry's
icon.

For example, the following input...

```
Applications
	IMG:./icons/web.png	Web Browser	firefox
	IMG:./icons/gimp.png	Image editor	gimp
Terminal (xterm)	xterm
Terminal (urxvt)	urxvt
Terminal (st)		st

Shutdown		poweroff
Reboot			reboot
```

...generates the following menu:

![demo](./demo.png)

## Customization
XMenu can be customized by setting the following X resources before
invoking XMenu.

* `XMenu.activeBackground`: Background color for selected entry.
* `XMenu.activeForeground`: Text color for selected enty.
* `XMenu.alignment`:        Text alignment.
* `XMenu.background`:       Background color.
* `XMenu.borderColor`:      Border color.
* `XMenu.borderWidth`:      Border size.
* `XMenu.faceName`:         Font for drawing text.
* `XMenu.faceSize`:         Font size.
* `XMenu.foreground`:       Text color.
* `XMenu.gap`:              Gap between windows.
* `XMenu.maxItems`:         Maximum number of items displayed on a menu.
* `XMenu.opacity`:          Background opacity (from 0.0 to 1.0).
* `XMenu.separatorColor`:   Separator color.
* `XMenu.shadowThickness`:  3D relief size.
* `XMenu.topShadowColor`, `XMenu.middleShadowColor`, `XMenu.bottomShadowColor`:
  Colors of the 3D relief.

## Installation
Run `make all` to build, and `make install` to install the binary and
the manual into `${PREFIX}` (`/usr/local`).

## Usage

* XMenu reads something in and prints something out, the UNIX way.
* Submenus (some menu entries can spawn another menu).
* Separators (menu entries can be separated by a line).
* Icons (menu entries can be preceded by an icon image).
* X resources support (you don't need to recompile xmenu for configuring it).
* Multi-head (xmenu supports multiple monitors by using Xinerama).

## License
The code and manual are under the MIT/X license.
See `./LICENSE` for more information.

## Epilogue
**Read the manual.**
