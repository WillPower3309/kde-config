# kde-config
Optimal configuration files for the KDE Desktop Environment

![](/thumbnail.png)

## Tiling
+ Install `kwin-tiling` though the KWin Scripts section of the System Settings
+ Run the following commend to get access to changing the tiling settings in the KWin Scripts settings area:

```
mkdir -p ~/.local/share/kservices5/
ln -s ~/.local/share/kwin/scripts/k ~/.local/share/kwin/scripts/kwin-script-tiling/metadata.desktop ~/.local/share/kservices5/kwin-script-tiling.desktop
```

+ Enable Tiling Extension and access its settings
  + Check "Remove window borders on tiled windows"
  + Set the placement method to "Open new tiles at the end"
  + Set desired gaps under the "Gaps" tab. Personally, I have all fields set to 12, and both "Gaps between windows" fields set to 6
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
  + [Window Buttons](https://github.com/psifidotos/applet-window-buttons)
  
### Global Menu
+ In order to have the global menu work with GTK apps, install `appmenu-gtk-module`
+ In order to have the global menu work with electron apps, install `libdbusmenu-glib`

## Application Theming

### Colors ###
The top panel is set to change it's color based off of the titlebar color of the application thats maximized (even if the titlebars aren't displayed like in our case). This means we need a color scheme for each application we're using, and this is accomplished by having window rules set a color scheme for each applciation that doesnt look right with the top panel matching the default qt theme titlebar color.
1. Install all the color schemes located in `color-schemes` via kde's system settings. Alternatively, copy / symlink them to the `~/.kde4/share/apps/color-schemes` folder
2. In system settings, under Window Management -> Window Rules, import all of the rules located in the `window-rules` folder

### Firefox ###
1. Copy the `firefox-css/chrome` folder into your Firefox profile directory. To find your profile directory, go to about:support. Alternatively, you can symlink your chrome folder instead of copying
2. In about:config Set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true` (default is false).
3. In about:config Set `full-screen-api.ignore-widgets` to `true`
4. Restart Firefox

Theme used from [dpcdpc11's Simplify Silver Peach](https://www.deviantart.com/dpcdpc11/art/Simplify-Silver-Peach-for-Firefox-userChrome-css-837727434)

### Emacs
+ Install [doom emacs](https://github.com/hlissner/doom-emacs)

```
git clone --depth 1 https://github.com/hlissner/doom-emacs ~/.emacs.d
~/.emacs.d/bin/doom install
```

### Neovim

1. Ensure the nvim folder from the repo has been copied into the ~/.config directory
2. Install VimPlug with

```
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

3. Open neovim and run :PlugInstall
4. Exit and reopen neovim

### Spotify
1. Install `spicetify-cli`
2. Chown spotify directory: `sudo chown $USER -R /opt/spotify`
3. Run `spicetify` once to generate config
4. `spicetify backup apply enable-devtool` to enable devtools
5. Move the `spicetify/Dribbblish` folder into the `~/.config/spicetify/Themes` folder
6. Move the `spicetify/dribbblish.js` file into the `~/.config/spicetify/Extensions` folder
7. Run:

```
spicetify config extensions dribbblish.js
spicetify config current_theme Dribbblish color_scheme base
spicetify config inject_css 1 replace_colors 1 
spicetify apply
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
