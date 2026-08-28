# dwm utility scripts

A small collection of POSIX shell scripts providing various desktop
functionalities, conveniently bound to keypresses in my
[custom dwm build](https://github.com/shirozuki/dwm.git). `dwmctl` is
additionally integrated with [modbar](https://github.com/shirozuki/modbar.git)
and its default [shell modules](https://github.com/shirozuki/modbar-shell-modules.git).

## Scripts
 - **dwmctl** — desktop control hub: display configuration, power management
   (lock/shutdown/reboot), wallpaper selection, keyboard setup, backlight and
   volume control.
 - **amilauncher** — pick and launch an FS-UAE Amiga emulator configuration via dmenu.
 - **btconn** — connect to a known Bluetooth device via dmenu.
 - **newswrap** — wrapper around newsboat that guards against concurrent runs.
 - **screenshot** — capture a selection, window or the whole screen with maim,
   copied to the clipboard.
 - **xclipemoji** — pick an emoji via dmenu and copy it to the clipboard.
 - **xclippass** — pick a `pass` entry via dmenu and copy a password, credit
   card field or OTP to the clipboard.

## Dependencies
`notify-send` (dunst) is used by every script, `dmenu` by all but newswrap
and screenshot, and `fd`/`awk`/`sed` wherever files are listed or parsed.
Per script: `fs-uae` (amilauncher), `bluetoothctl` (btconn), `newsboat` +
`pgrep` (newswrap), `maim` + `xdotool` + `xclip` (screenshot), `xclip`
(xclipemoji, xclippass), `pass` + `pass-otp` (xclippass), `xwallpaper` +
`slock` + `setxkbmap` + `xset` + `xbacklight` + `amixer` (dwmctl).

## Environment
| Variable | Used by | Description |
| --- | --- | --- |
| `XDG_DATA_HOME` | dwmctl, btconn, xclipemoji | Base for `display-conf/`, `bluetooth-devices/` (one file per device, holding its MAC address) and `emoji-list`. |
| `XDG_CONFIG_HOME` | all | Location of the dunst notification icons (`dunst/{critical,warning,info}.png`). |
| `MODBAR_PIPE_PATH` | dwmctl, btconn, newswrap | modbar FIFO used to trigger a module refresh. |
| `DWM_SETTINGS` | dwmctl | Shell file where `CURRENT_WALLPAPER` is persisted. |
| `WALLPAPER_DIRECTORY` | dwmctl | Root directory scanned for wallpapers. |
| `CURRENT_WALLPAPER` | dwmctl | Wallpaper restored by `-f setwp -c set`. |
| `KB_MAP` | dwmctl | Layout passed to `setxkbmap`. |
| `KB_AUTO_REPEAT_DELAY`, `KB_REPEAT_RATE` | dwmctl | Values passed to `xset r rate`. |
| `SCREENSHOT_DIRECTORY` | screenshot | Output directory, created if missing. |
| `PASSWORD_STORE_DIR` | xclippass | `pass` store to list entries from. |

Data files: `$XDG_DATA_HOME/display-conf/` holds executable display setup
scripts, `$XDG_DATA_HOME/emoji-list` one emoji per line, and
`~/FS-UAE/Configurations/` the `.fs-uae` files (path hardcoded).

## Usage
```
dwmctl -f <function> -c <command>
```
| Function | Commands |
| --- | --- |
| `displaysel` | — |
| `kbsetup` | — |
| `powermgr` | `lock`, `shutdown`, `restart` |
| `setwp` | `set`, `select` |
| `backlightctl` | `up`, `down` |
| `volumectl` | `up`, `down`, `toggle` |

```
screenshot <selection|window|all>
```
The remaining scripts take no arguments.

## Installation
Copy the desired executables somewhere into your system `$PATH`.
