# river

river is a dynamic wayland compositor that takes inspiration from
[dwm](https://dwm.suckless.org) and
[bspwm](https://github.com/baskerville/bspwm).

*Note: river is currently early in development and not yet ready for
the average end user*

## Design goals

- Simplicity and minimalism, river should not overstep the bounds of a
window manger.
- Dynamic window management based on a stack of views and tags like dwm.
- Scriptable configuration and control through a socket and separate
binary, `riverctl`, like bspwm.

## Building

To compile river first ensure that you have the following dependencies
installed:

- [zig](https://github.com/ziglang/zig) master (will depend on 0.6.0
after that is released)
- wayland
- wayland-protocols
- [wlroots](https://github.com/swaywm/wlroots) 0.10.1
- xkbcommon

Then simply run `zig build`.

River can either be run nested in an X11/wayland session or directly
from a tty using KMS/DRM.

## Development

Check out the [roadmap](https://github.com/ifreund/river/issues/1)
if you'd like to see what has been done and what is left to do.

If you are interested in the development of river, please join our
matrix channel:
[#river](https://matrix.to/#/!BQgAgeafraCtMiVbSX:matrix.org?via=matrix.org).

I can often be found in the `#sway-devel` IRC channel with the
nick `ifreund` on irc.freenode.net as well, or reached by email at
[ifreund@ifreund.xyz](mailto:ifreund@ifreund.xyz).