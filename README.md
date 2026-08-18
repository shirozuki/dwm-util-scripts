# dwm utility scripts

A small collection of POSIX shell scripts providing various desktop
functionalities, conveniently bound to keypresses in my
[custom dwm build](https://gitlab.dobrowolski.dev/dwm/dwm.git). `dwmctl` is
additionally integrated with [modbar](https://gitlab.dobrowolski.dev/dwm/modbar.git)
and its default [shell modules](https://gitlab.dobrowolski.dev/dwm/modbar-shell-modules.git).

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

## Usage
Copy the desired executables somewhere into your system `$PATH`.
