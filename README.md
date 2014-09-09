Odroid U2/3 - Arch Linux - Mali/xorg-armsoc
===========================================
This is  fork of gripped's repo odroid-u2-pkgbuilds, i made this to try and update the PKGBUILD's and keep them moving with Arch, the orignal README will be left in the repo for reference, I will only be working on the libs/drivers/etc i need/use but will leave the rest there incase anyone wants to update them !

Install/Build Instructions
==========================
There are 2 ways to install/build these packages, either install the provided 'pkg.tar.xz' file with pacman (Method 1) or build the package with the 'PKGBUILD' and then install the resulting 'pkg.tar.xz' file with pacman (Method 2). The packages i recommend you install are :

```
linux-odroidu-r4p0
mali-odroid-r4p0
mesa-libgl-noegl
mesa-noegl
xf86-video-armsoc-dsd
xf86-video-fbturbo-git
xorg-server-dsd
```

Method 1
--------
Change directory to where you want to clone the repo :

```
$ cd git
```

Then clone the repo :

```
$ git clone https://github.com/hreikin/odroid-u2-pkgbuilds
```

Then change directory into the file you wish to install, for example mesa-noegl :

```
$ cd mesa-noegl
```

Then install the available 'pkg.tar.xz' files with pacman :

```
$ sudo pacman -U mesa-noegl-10.2.7-1-armv7h.pkg.tar.xz
$ sudo pacman -U mesa-libgl-noegl-10.2.7-1-armv7h.pkg.tar.xz
```

Once you have all the files installed you need to edit your '/etc/xorg.conf' mine has :

```
# X.Org X server configuration file for xfree86-video-mali

Section "Device"

  Identifier "Mali-Fbdev"

  Driver   "armsoc"

  Option   "fbdev"           "/dev/fb1"

  Option  "DriverName"      "exynos"

EndSection



Section "Screen"

  Identifier   "Mali-Screen"

  Device       "Mali-Fbdev"

  DefaultDepth 24 

EndSection



Section "DRI"

  Mode 0666

EndSection
```

Method 2
--------
Change directory to where you want to clone the repo :

```
$ cd git
```

Then clone the repo :

```
$ git clone https://github.com/hreikin/odroid-u2-pkgbuilds
```

Then change directory into the file you wish to install, for example mesa-noegl :

```
$ cd mesa-noegl
```

Then take a look at the 'PKGBUILD' to check everything is ok with nano before running 'makepkg -s' :

```
$ nano PKGBUILD
$ makepkg -s
```

Once 'makepkg' finishes it will create a 'pkg.tar.xz' file (maybe more than 1!) which can be installed with pacman like so :

```
$ sudo pacman -U mesa-noegl-10.2.7-1-armv7h.pkg.tar.xz
$ sudo pacman -U mesa-libgl-noegl-10.2.7-1-armv7h.pkg.tar.xz
```
Once you have all the files installed you need to edit your '/etc/xorg.conf' mine has :

```
# X.Org X server configuration file for xfree86-video-mali

Section "Device"

  Identifier "Mali-Fbdev"

  Driver   "armsoc"

  Option   "fbdev"           "/dev/fb1"

  Option  "DriverName"      "exynos"

EndSection



Section "Screen"

  Identifier   "Mali-Screen"

  Device       "Mali-Fbdev"

  DefaultDepth 24 

EndSection



Section "DRI"

  Mode 0666

EndSection
```
