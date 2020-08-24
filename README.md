# river

river is a dynamic tiling wayland compositor that takes inspiration from
[dwm](https://dwm.suckless.org) and
[bspwm](https://github.com/baskerville/bspwm).

*Note: river is currently early in development. Expect breaking changes
and missing features. If you run into a bug don't hesitate to
[open an issue](https://github.com/ifreund/river/issues/new)*

## Design goals

- Simplicity and minimalism, river should not overstep the bounds of a
window manager.
- Window management based on a stack of views and tags.
- Dynamic layouts generated by external, user-written executables. (A default
`rivertile` layout generator is provided.)
- Scriptable configuration and control through a custom wayland protocol and
separate `riverctl` binary implementing it.

## Building

To compile river first ensure that you have the following dependencies
installed:

- [zig](https://github.com/ziglang/zig) 0.6.0
- wayland
- wayland-protocols
- [wlroots](https://github.com/swaywm/wlroots) 0.11.0
- xkbcommon
- libevdev
- pixman
- pkg-config
- scdoc (optional, but required for man page generation)

*Note: NixOS users should refer to the
[Building on NixOS wiki page](https://github.com/ifreund/river/wiki/Building-on-NixOS)*

Then run, for example,
```
zig build -Drelease-safe=true --prefix /usr/local install
```
to build and install the binaries and man pages to `/usr/local/bin` and
`/usr/local/share/man`. To enable experimental Xwayland support pass the
`-Dxwayland=true` option as well.

## Usage

River can either be run nested in an X11/wayland session or directly
from a tty using KMS/DRM.

River has no keybindings by default; mappings can be created using the `map`
command of `riverctl`. Generally, creating mappings and other configuration is
done with a shell script. River will execute any arbitrary shell command passed
with the `-c` flag during startup. For example:

```
river -c /path/to/config.sh
```

An example script with sane defaults is provided [here](contrib/config.sh) in
the contrib directory.

For a complete list of commands see the `riverctl(1)` man page.

Keyboard configuration is not yet implemented in river, but since river uses
libxkbcommon you may use the following environment variables to set defaults:

- `XKB_DEFAULT_RULES`
- `XKB_DEFAULT_MODEL`
- `XKB_DEFAULT_LAYOUT`
- `XKB_DEFAULT_VARIANT`
- `XKB_DEFAULT_OPTIONS`

Possible values for these variables can be found in the `xkeyboard-config(7)`
man page. For example, to use a dvorak layout one could start river with

```
XKB_DEFAULT_LAYOUT="us(dvorak)" river
```

## Development

Check out the [roadmap](https://github.com/ifreund/river/issues/1)
if you'd like to see what has been done and what is left to do.

If you are interested in the development of river, please join us at
[#river](https://webchat.freenode.net/#river) on freenode. You should also
read [CONTRIBUTING.md](CONTRIBUTING.md) if you intend to submit patches.

## Licensing

river is released under the GNU General Public License version 3, or (at your
option) any later version.

The protocols in the `protocol` directory are released under various licenses by
various parties. You should refer to the copyright block of each protocol for
the licensing information. The protocols prefixed with `river` and developed by
this project are released under the ISC license (as stated in their copyright
blocks).
