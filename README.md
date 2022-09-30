# XMenu

<p align="center">
	<img src="https://user-images.githubusercontent.com/63266536/114306062-ffb67000-9ab0-11eb-9a10-be30eadc68b4.gif", title="demo"/>
</p>

> Check out the `testing` branch for a faster version of `xmenu` with a
> different syntax that is not based on tabs.

XMenu is a menu utility for X.
XMenu receives a menu specification in stdin, shows a menu for the user
to select one of the options, and outputs the option selected to stdout.
XMenu can be controlled both via mouse and via keyboard.

In order to generate a menu of applications based on .desktop entries,
as specified by XDG, checkout [xdg-xmenu](https://github.com/OliverLew/xdg-xmenu)
by [OliverLew](https://github.com/OliverLew).

Check out my other project, [xclickroot](https://github.com/phillbush/xclickroot) for an application that can
spawn xmenu by right clicking on the root window (i.e. on the desktop).


## Features

XMenu comes with the following features:

* XMenu reads something in and prints something out, the UNIX way.
* Submenus (some menu entries can spawn another menu).
* Separators (menu entries can be separated by a line).
* Icons (menu entries can be preceded by an icon image).
* X resources support (you don't need to recompile xmenu for configuring it).
* Multi-head (xmenu supports multiple monitors by using Xinerama).
* Type-to-select (you can select an item by typing part of its name).


## Files

The files are:

* `./README`:     This file.
* `./Makefile`:   The makefile.
* `./config.h`:   The hardcoded default configuration for XMenu.
* `./xmenu.1`:    The manual file (man page) for XMenu.
* `./xmenu.c`:    The source code of XMenu.
* `./xmenu.sh`:   A sample script illustrating how to use XMenu.
* `./icons/`:     Icons for the sample script


## Installation

First, edit `./config.mk` to match your local setup.

In order to build XMenu you need the `Imlib2`, `Xlib`, `Xinerama` and `Xft` header files.
The default configuration for XMenu is specified in the file `config.h`,
you can edit it, but most configuration can be changed at runtime via
X resources.  Enter the following command to build XMenu.  This command
creates the binary file `./xmenu`.

	make

By default, XMenu is installed into the `/usr/local` prefix.  Enter the
following command to install XMenu (if necessary as root).  This command
installs the binary file `./xmenu` into the `${PREFIX}/bin/` directory, and
the manual file `./xmenu.1` into `${MANPREFIX}/man1/` directory.

	make install


## Running XMenu

XMenu receives as input a menu specification where each line is a menu
entry.  Each line can be indented with tabs to represent nested menus.
Each line is made out of a label and a command separated by any number
of tabs.  Lines without labels are menu separators.

See the script `./xmenu.sh` for an example of how to use XMenu to draw a
simple menu with submenus and separators.  The file `./demo.gif` shows how
the menu generated by that script looks like.

Read the [manual](https://github.com/phillbush/xmenu/wiki) for more information on running XMenu.


## Acknowledgements

* [thingmenu](https://github.com/singpolyma/thingmenu) for being the base
  for xmenu's code.  However, xmenu evolved enough that it no longer resembles
  thingmenu at all.
* [dmenu](https://tools.suckless.org/dmenu/) for inspiring the stdin-to-stdout
  interface, and being base for drawing routines and input method code.
