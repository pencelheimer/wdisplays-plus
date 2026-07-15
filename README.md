# wdisplays-plus

[![License: GPL 3.0 or later][license-img]][license-spdx]

wdisplays-plus is a graphical application for configuring displays in Wayland
compositors. It should work in any compositor that implements the
[wlr-output-management-unstable-v1](https://wayland.app/protocols/wlr-output-management-unstable-v1)
protocol.

### Supported Compositors

Check the protocol support
[here](https://wayland.app/protocols/wlr-output-management-unstable-v1#compositor-support).

Tested on:
- [Sway]
- [Wayfire]
- [River](https://codeberg.org/river/river)
- [Hyprland](https://hyprland.org)
- [Niri](https://github.com/niri-wm/niri)

![Screenshot](wdisplays.png)

# Building

Build requirements are:

- meson
- GTK+3
- epoxy
- wayland-client

```sh
meson build
ninja -C build
sudo ninja -C build install
```

# Recent Changes & Fixes

This version includes several recent enhancements and fixes merged from the
community:

- **GSettings / Preferences**: Automatically load and save application
  preferences found in the hamburger menu via gsettings (credit to **Lauren
  Lagarde**). Added runtime schema verification and fallback to prevent crashes
  if the schema isn't installed.
- **Kanshi Integration Improvements**: Kanshi configuration export support was added by the community (credit to **Jason André Charles Gantner** and **Shaochang Tan**). Further enhancements and fixes were made by **pencelheimer**, including updating the output naming scheme to use a "make model serial_number" triplet (to comply with recent Wayland protocol updates) and fixing linker errors.
- **UI Enhancements**: Allow applying pending changes quickly using
  `Ctrl+Return` (credit to **Manuel Herrmann**).
- **Bug Fixes**: Handled overlay crashes when the overlay surface is destroyed
  before its role and handled NULL heads during resize/draw (credit to
  **save196**).
- **Compilation & Modernization**: Fixed C23 compilation issues and updated
  licensing headers (credit to **Viorel Munteanu** and **Jason André Charles
  Gantner**).

# Usage

Displays can be moved around the virtual screen space by clicking and dragging
them in the preview on the left panel. By default, they will snap to one
another. Hold Shift while dragging to disable snapping. You can click and drag
with the middle mouse button to pan. Zoom in and out either with the buttons on
the top left, or by holding Ctrl and scrolling the mouse wheel. Fine tune your
adjustments in the right panel, then click apply (or press `Ctrl+Return`).

Settings applied here are for the current session. To make display settings
persistent (e.g. in Sway), use an external tool like [kanshi]. When you apply
a new change, wdisplays-plus can automatically update `$HOME/.config/kanshi/config`
for the current monitor combination.

[kanshi]: https://github.com/emersion/kanshi
[way-displays]: https://github.com/alex-courtis/way-displays
[Sway]: https://swaywm.org
[Wayfire]: https://wayfire.org
[ARandR]: https://christian.amsuess.com/tools/arandr/
[tinywl-output-management]: https://git.sr.ht/~jf/tinywl-output-management/commit/87a45d89ae0e7975e2a59f84e960380dd2f5ac08

[license-img]:  https://img.shields.io/badge/License-GPL%203.0%20or%20later-blue.svg?logo=gnu
[license-spdx]: https://spdx.org/licenses/GPL-3.0-or-later.html
