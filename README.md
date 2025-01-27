# sway-launcher-desktop [![Build Status](https://travis-ci.org/Biont/sway-launcher-desktop.svg?branch=master)](https://travis-ci.org/Biont/sway-launcher-desktop)

![screenshot_2019-10-25-213740](https://user-images.githubusercontent.com/4208996/67599848-3a1f3680-f771-11e9-9715-da6e943ae14e.png)

This is a launcher menu made for the Sway window manager made with bash and the amazing [fzf](https://github.com/junegunn/fzf).

## Features
- Lists and executes available binaries
- Lists and executes .desktop files (entries as well as actions)
- Shows a preview window containing `whatis` info of binaries and the `Comment=` section of .desktop files
- History support which will highlight recently used entries. (Inspried by [this nice script which inspired me to create my own](https://gitlab.com/FlyingWombat/my-scripts/blob/master/sway-launcher))
- Colored output and glyphs for the different entry types
- Entries are lazily piped into fzf eliminating any lag during startup

## Installation

Make sure you have `fzf` installed and download this repository

Configure it in Sway like this:
```
for_window [class="URxvt" instance="launcher"] floating enable, border pixel 10, sticky enable
set $menu exec urxvt -geometry 55x18 -name launcher -e env TERMINAL_COMMAND="urxvt -e" /path/to/repo/sway-launcher-desktop.sh
bindsym $mod+d exec $menu
```

### Setup a Terminal command
Some of your desktop entries will probably be TUI programs that expect to be launched in a new terminal window. Those entries have the `Terminal=true` flag set and you need to tell the launcher which terminal emulator to use. Pass the `TERMINAL_COMMAND` environment variable with your terminal startup command to the script to use your preferred terminal emulator. The script will default to `termite -e`
