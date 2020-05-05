# kde-config
Optimal configuration files for the KDE Desktop Environment

## Tiling
+ Install `Krohnkite` though the KWin Scripts section of the System Settings
+ Run the following commend to get access to changing Krohnkite's settings in the KWin Scripts settings:

```
mkdir -p ~/.local/share/kservices5/
ln -s ~/.local/share/kwin/scripts/krohnkite/metadata.desktop ~/.local/share/kservices5/krohnkite.desktop
```

+ Enable Krohnkite and access its settings
  + In `Layout` deselect every layout except `Tile Layout`
  + Add a desired gap in `Geometry` (I like 15 for normal DPI displays)
  + In `Behaviour` select `Directional` in the `Directional Keys Behaviours` area
  + In `Options` select `Remove borders of tiled windows`
  + Apply changes
+ In `System Settings`, under `Window Behaviour`, change the `Window activation policy` to `Focus follows mouse` and set `Delay focus` to `0ms`

## Shortcuts
Designed to emulate popular tiling window managers
+ Ensure there are 10 virtual desktops in kde

## Latte Layout
Beautiful macOS esque layout with a "get out of my way when I don't need you" design philosophy
**Widgets (in order):**
+ Left:
  + Application Dashboard
  + [Virtual Desktop Bar](https://github.com/wsdfhjxc/virtual-desktop-bar)
  + Application Title
  + Global Menu
+ Middle:
  + Digital Clock
+ Right: 
  + System Tray
  + Window Buttons
  
### Global Menu
+ In order to have the global menu work with GTK apps, install `appmenu-gtk-module`
+ In order to have the global menu work with electron apps, install `libdbusmenu-glib`

## Emacs
+ Install [doom emacs](https://github.com/hlissner/doom-emacs)

```
git clone --depth 1 https://github.com/hlissner/doom-emacs ~/.emacs.d
~/.emacs.d/bin/doom install
```

## Video Wallpaper
+ Install `Smart video wallpaper` from `Configure Desktop`
+ Install `gst-libav`, and restart your computer
+ Change the `Wallpaper Type` dropdown menu to `Smart video wallpaper`
+ Select the video in this repo
    + Video is from [this youtube video](https://www.youtube.com/watch?v=NAEVf9M-pLE)

+ To get the menu bar back (for the KDE global menu):
  + Navigate to `.emacs.d`
  + remove the line `(add-to-list 'default-frame-alist '(menu-bar-lines . 0))` from `core-el.el`

## Shell
1. install `zsh`
2. Install `powerlevel10k`
```
pacman -S zsh-theme-powerlevel10k
```
3. Install `oh-my-zsh` with the below command
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
4. Install Plugins
  + Syntax highlighting (copy and paste the below command to install)
    ```
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```
  + Autosuggestions (copy and paste the below command to install)
    ```
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```
5. Copy the `.zshrc` file in this repo to your home directory
6. Fini! Reopen the terminal to view the fruit of your labor

## GRUB Auto Boot
To auto boot linux change the `/etc/default/grub` boot loader configuration to:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_DISTRIBUTOR="Arch"
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet acpi=copy_dsdt splash"
GRUB_CMDLINE_LINUX=""
```
