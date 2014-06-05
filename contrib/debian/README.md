
Debian
====================
This directory contains files used to package horuscoind/horuscoin-qt
for Debian-based Linux systems. If you compile horuscoind/horuscoin-qt yourself, there are some useful files here.

## horuscoin: URI support ##


horuscoin-qt.desktop  (Gnome / Open Desktop)
To install:

	sudo desktop-file-install horuscoin-qt.desktop
	sudo update-desktop-database

If you build yourself, you will either need to modify the paths in
the .desktop file or copy or symlink your horuscoin-qt binary to `/usr/bin`
and the `../../share/pixmaps/horuscoin128.png` to `/usr/share/pixmaps`

horuscoin-qt.protocol (KDE)

