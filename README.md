<p align="center">
<img src="https://nabile.duckdns.org/Arc-39/images/Logo.svg" alt="logo">
</p>

# Arc-39

Arc-39 is a Miku-styled theme for the Linux desktop.

This theme is based on [Arc Theme](https://github.com/arc-design/arc-theme).

### Screenshots

![](https://nabile.duckdns.org/Arc-39/images/gtk3-widget-factory-page-1.png)

![](https://nabile.duckdns.org/Arc-39/images/gtk3-widget-factory-page-2.png)

## Building

First, [ensure that you have the required packages installed, and review the autogen.sh options available](README.arc-theme.md#manual-installation).

I build the theme using the following commands:

- `./autogen.sh --prefix=$HOME/.local --with-gtk3=3.22 --disable-light --disable-darker --disable-cinnamon --disable-metacity --disable-unity --disable-xfwm --disable-plank --disable-openbox`
- `make install`

At this time, I have only themed the dark variant of GTK 3.20, GTK 2, and GNOME Shell 3.22.

This should be compatible with GTK 2, GTK 3.20+, and GNOME Shell 3.18 through 3.24.

### Notes

- Since GTK 2 only looks at `~/.themes` for user theme files, you'll want to do either of these things:

    - `ln -s ~/.local/share/themes ~/.themes` to symlink the XDG themes folder to the user's folder.
    - Rebuild with `./autogen.sh --prefix=$HOME/.themes` to move the theme's destination to where GTK 2 will check for files.

- The generated makefiles don't seem to watch for `.scss` changes to update the `.css` files when rebuilding.

    In order to quickly prototype stylesheet edits, remove all `.css` files from the `common` directory, then `make install`.

- Unlike `gtk-3.0`'s `assets.svg` from which resources are automatically generated from, `gnome-shell`'s are individual `.svg` files contained within the `*-assets` folders.

    To make your life easier, identify common hexadecimal colour codes to modify, and use sed to globally replace the values instead of editing the elements one by one (i.e.: `find common/gnome-shell/3.22 -type f -print0 | xargs -0 sed -i -e 's/#AAAAAA/#BBBBBB/g'`).

## Design

The design is straightforward:

- Background elements (including some of the text) had their red channel zeroed out. This produces a turquoise palette.
- Foreground elements and text are tinted green, like leek.
- Selected elements are tinted pink.

## Credits

Credits go to the authors of the excellent [Arc Theme](https://github.com/arc-design/arc-theme).
