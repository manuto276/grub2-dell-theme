# Dell Theme for Grub2

A simple theme I made for my Dell XPS 15 running Ubuntu 23.10.

## Installation:

Usage:  `sudo ./install.sh [OPTIONS...]`

```
  -t, --theme     theme variant(s)          [dell]                              (default is dell)
  -i, --icon      icon variant(s)           [white]                             (default is white)
  -s, --screen    screen display variant(s) [1080p|2k|4k|ultrawide|ultrawide2k] (default is 1080p)
  -r, --remove    Remove theme              [dell]                              (must add theme name option, default is dell)

  -b, --boot      install theme into '/boot/grub' or '/boot/grub2'
  -g, --generate  do not install but generate theme into chosen directory       (must add your directory)

  -h, --help      Show this help
```

_If no options are used, a user interface `dialog` will show up instead_

### Examples:
 - Install Dell theme on 2k display device:

```sh
sudo ./install.sh -t dell -s 2k
```

 - Install Dell theme into /boot/grub/themes:

```sh
sudo ./install.sh -b -t dell
```

 - Uninstall Dell theme:

```sh
sudo ./install.sh -r -t dell
```

## Issues / tweaks:

### Correcting display resolution:

 - On the grub screen, press `c` to enter the command line
 - Enter `vbeinfo` or `videoinfo` to check available resolutions
 - Open `/etc/default/grub`, and edit `GRUB_GFXMODE=[height]x[width]x32` to match your resolution
 - Finally, run `grub-mkconfig -o /boot/grub/grub.cfg` to update your grub config

### Setting a custom background:

 - Make sure you have `imagemagick` installed, or at least something that provides `convert`
 - Find the resolution of your display, and make sure your background matches the resolution
   - 1920x1080 >> 1080p
   - 2560x1080 >> ultrawide
   - 2560x1440 >> 2k
   - 3440x1440 >> ultrawide2k
   - 3840x2160 >> 4k
 - Place your custom background inside the root of the project, and name it `background.jpg`
 - Run the installer like normal, but with -s `[YOUR_RESOLUTION]` and -t `[THEME]` and -i `[ICON]`
   - Make sure to replace `[YOUR_RESOLUTION]` with your resolution and `[THEME]` with the theme