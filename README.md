# kde-config
Optimal configuration files for the KDE Desktop Environment

## Shortcuts
Designed to emulate popular tiling window managers

## Latte Layout
Beautiful macOS esque layout with a "get out of my way when I don't need you" design philosophy

## Emacs
+ Install [doom emacs](https://github.com/hlissner/doom-emacs)

```
git clone --depth 1 https://github.com/hlissner/doom-emacs ~/.emacs.d
~/.emacs.d/bin/doom install
```

+ To get the menu bar back (for the KDE global menu):
  + Navigate to `.emacs.d`
  + remove the line `(add-to-list 'default-frame-alist '(menu-bar-lines . 0))` from `core-el.el`
