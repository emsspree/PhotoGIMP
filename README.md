PhotoGIMP
=========

**Improvements for GIMP 2.10+,** 
the [GNU Image Manipulation Program](https://www.gimp.org/), to fit (former) Adobe&nbsp;Photoshop users’&nbsp;needs.

It patches [GIMP’s configuration and supporting data](https://www.gimp.org/tutorials/GIMPProfile/) to make it behave, look&nbsp;and&nbsp;feel more&nbsp;like&nbsp;Photoshop.

🛍 Features:
---------------

- Tool organization to mimic the position of those in&nbsp;Photoshop.
- Keyboard shortcuts similar to the ones in Photoshop, following Adobe’s&nbsp;documentation.
- New default settings to maximize space on the&nbsp;canvas.
- 20 additional Python filters, such as “Heal&nbsp;Selection”.
- 80+ additional brushes.
- 1800+ additional fonts included (see&nbsp;[fonts.txt](https://github.com/Diolinux/PhotoGIMP/blob/master/fonts.txt)).
- New splash screen.
- New icon and name from custom *.desktop* file. (preset for Flatpak; change the `Exec=`&nbsp;line for&nbsp;others)

___

🗳 Installation
---------------

PhotoGIMP was intended to be used with a Flatpak installation of GIMP, but since it contains “just files” you can use it on any platform supported by GIMP regardless of the installation method.



### Steps Prior PhotoGIMP Installation

1.  **Install GIMP first.** <a id="install-gimp" name="install-gimp"></a>This package does not include GIMP itself.

    > <details><summary>Install GIMP using your preferred method…</summary>
    >
    > + <img src="https://simpleicons.org/icons/gimp.svg" width="20px" alt="GIMP"><!---->
        Consult the [GIMP Downloads](https://www.gimp.org/downloads/) page for all install options.
    > + <img src="https://simpleicons.org/icons/freedesktopdotorg.svg" width="20px" alt="Unix-like systems in general"><!---->
        Install `gimp` with the installation routine provided by your system.
    > + <img src="https://simpleicons.org/icons/flathub.svg" width="20px" alt="Flathub"><!---->
        `flatpak install flathub org.gimp.GIMP` or [flathub.org](https://flathub.org/apps/details/org.gimp.GIMP).
    > + <img src="https://simpleicons.org/icons/snapcraft.svg" width="20px" alt="Snapcraft"><!---->
        `sudo snap install gimp` or [snapcraft.io](https://snapcraft.io/gimp)<br>
        You might want to use [Pedro Marinho’s Snap package of PhotoGIMP](https://github.com/pedroermarinho/photogimp) instead of this one.
    > + <img src="https://simpleicons.org/icons/freebsd.svg" width="20px" alt="FreeBSD"><!---->
        `pkg install gimp` or `cd /usr/ports/graphics/gimp/ && make install clean`
    > + <img src="https://simpleicons.org/icons/apple.svg" width="20px" alt="macOS"><!---->
        `brew install --cask gimp` or `sudo port install gimp`
    > + &#x2006;<img src="https://simpleicons.org/icons/windows.svg" width="17px" alt="Windows 7+"><!---->
        `choco install gimp`
    > </details>

1.  **Launch GIMP** immediately after installation is&nbsp;done.

1.  **Get the path of GIMP’s configuration directory.**<a id="get-gimp-dir" name="get-gimp-dir"></a>

    1. Open GIMP’s own console from&nbsp;the&nbsp;menu:<br>
    <kbd><samp>Filters</samp></kbd> › <kbd><samp>Python-fu</samp></kbd> › <kbd><samp>Console</samp></kbd><br>

    1. Enter `print gimp.directory` to show the path.

        > A Flatpak installation usually uses `"$HOME/.var/app/org.gimp.GIMP/config/GIMP/2.10"`.<br>
        > A Snap installation usually uses `"$HOME/snap/gimp/47/.config/GIMP/2.10"`.
        >
        > If you have installed GIMP as Flatpak or Snap, but GIMP does not show one of the paths above then you have probably installed a different GIMP version (e.g. via a package manager) before. This is not a problem in itself, but make sure that PhotoGIMP is then installed in this and not in the one provided by Flatpak or Snap. Easier for you is to quit GIMP, delete/rename the old folder and then look up the path on GIMP's console again.

        > It is also posible to define which directory GIMP shall use by setting an [environment variable](https://www.gimp.org/man/gimp.html#environment "GIMP ManPage").

    1. Copy the path shown by the console to the clipboard.
    If you don’t use a clipboard manager paste the path somewhere for later use – e.g. in a text editor or notes application.

1.  **Quit GIMP.**

1.  **Backup** your GIMP configuration directory if needed. Renaming is sufficient.

    ⚠️ **All existing files will be overwritten.** ⚠️<br>If you have not freshly installed GIMP but used it before, you may want to restore parts of your old configuration.

### Download and extract the ZIP file

> Not needed when you install the Snap (Linux) or Chocolatey (Windows 7+) package of PhotoGIMP.

1.  **Download** the [PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip](https://github.com/Diolinux/PhotoGIMP/releases/download/1.0/PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip) from the [Releases](https://github.com/Diolinux/PhotoGIMP/releases) page with a mouse click or with your shell:

        curl -L https://github.com/Diolinux/PhotoGIMP/releases/download/1.0/PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip -o ~/Downloads/PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip

    > Will download to `~/Downloads/PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip`.

1.  **Extract** the `PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip` archive with your shell (recommended) or any other way:

        unzip ~/Downloads/PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip -x '*/.ld.so/*' '*/cache/*' '*/current/*' '*/data/*' '*/gtk-?.0/*' '*/ibus/*' '*/user-dirs.dirs' '*Patch.txt' -d ~/  &&  \ls -A ~/Downloads/"PhotoGIMP by Diolinux v2020 for Flatpak"/.*

    > Extracts files to `"~/Downloads/PhotoGIMP by Diolinux v2020 for Flatpak"`.<br>
    > Files that are not required will not be extracted.

1.  **If you did not extract the archive using the shell command**, there are now some unnecessary files that you should delete now (not mandatory but easier).

    > Make your file manager **show hidden files** (whose names begin with a dot).

    + Delete `How to Install PhotoGIMP's Patch.txt` (you are currently reading an updated README)
    + Delete `.var/app/org.gimp.GIMP/.ld.so`
    + Delete `.var/app/org.gimp.GIMP/cache`
    + Delete `.var/app/org.gimp.GIMP/config/gtk-2.0`
    + Delete `.var/app/org.gimp.GIMP/config/gtk-3.0`
    + Delete `.var/app/org.gimp.GIMP/config/ibus`
    + Delete `.var/app/org.gimp.GIMP/config/user-dirs.dirs`
    + Delete `.var/app/org.gimp.GIMP/current`
    + Delete `.var/app/org.gimp.GIMP/data`

1.  **Result:** You should have these directories inside a `PhotoGIMP by Diolinux v2020 for Flatpak` directory.

    > Make your file manager **show hidden files** (whose names begin with a dot).

    + `.icons` (if you don’t want the custom icon you can delete this too.)
    + `.local` (if you don’t want the custom *.desktop* file you can delete this too.)
    + `.var` &nbsp;&#x2000; (this contains the essential PhotoGIMP configuration files.)



### Install PhotoGIMP


#### Windows 7+ with Chocolatey <img src="https://simpleicons.org/icons/windows.svg" width="17px" alt="Windows 7+"> + <img src="https://simpleicons.org/icons/chocolatey.svg" width="18px" alt="Windows 7+">

1.  Enter `choco install photogimp` in PowerShell.

The [Chocolatey package](https://community.chocolatey.org/packages/photogimp) is maintained by [André Augusto](https://github.com/AndreAugustoAAQ).


#### Linux Snap <img src="https://simpleicons.org/icons/snapcraft.svg" width="19px" alt="Snapcraft">

Snap users can install *this* package by using the method described in the [“All others” section](#all-others)<br>
or install *another* [Snap package](https://github.com/pedroermarinho/photogimp):

1.  Enter `sudo snap install photogimp` in a shell or use the [Snapcraft website](https://snapcraft.io/photogimp).

> This will install PhotoGIMP into `"$HOME/snap/gimp/47/.config/GIMP/2.10"`; [make sure GIMP really uses that directory](#get-gimp-dir).

That Snap package is maintained by [Pedro Marinho](https://github.com/pedroermarinho/photogimp).
<!--

#### <img src="https://simpleicons.org/icons/flathub.svg" width="20px" alt="Flathub"> Linux Flatpak

1.  Install the custom icon file: …

1.  Install the custom *.desktop* file: …

1.  Install the essential PhotoGIMP configuration files: see the [“All others” section](#all-others).-->


#### All Others <img src="https://simpleicons.org/icons/freedesktopdotorg.svg" width="19px" alt="Unix-like systems in general"> <img src="https://simpleicons.org/icons/flathub.svg" width="20px" alt="Flathub"> <img src="https://simpleicons.org/icons/linux.svg" width="19px" alt="FreeBSD"> <img src="https://simpleicons.org/icons/freebsd.svg" width="17px" alt="FreeBSD"><img src="https://simpleicons.org/icons/apple.svg" width="19px" alt="macOS">…

1.  **Copy essential config files:** copy the contents of the *2.10* directory, `.var/app/org.gimp.GIMP/config/2.10`, to your GIMP’s configuration directory <br>(the path shown by [GIMP’s console](#get-gimp-dir)), e.g. `$HOME/.config/GIMP/2.10`.

    Shell command 1: set a variable to your path (replace `…` with your path)

        GDIR=…
    
    Example: `GDIR="$HOME/.config/GIMP/2.10"` (no trailing slash!)

    Shell command 2: copy files

        cp -R ~/Downloads/"PhotoGIMP by Diolinux v2020 for Flatpak"/.var/app/org.gimp.GIMP/config/GIMP/2.10  "$GDIR"

1.  **Copy desktop entry and its icon** (both not needed)

    1.  Copy `.local/share/applications/org.gimp.GIMP.desktop` to `$HOME/.local/share/applications/org.gimp.GIMP.desktop`

            cp ~/Downloads/"PhotoGIMP by Diolinux v2020 for Flatpak"/.local/share/applications/org.gimp.GIMP.desktop  ~/.local/share/applications/org.gimp.GIMP.desktop
        
        For non-Flatpak installations: Edit `$HOME/.local/share/applications/org.gimp.GIMP.desktop` in a text editor, look for the line beginning with `Exec=` and change the path to the GIMP executable. To find out that path, open `/usr/local/share/applications/org.gimp.GIMP.desktop` 

    1.  Copy `.icons/photogimp.png` to `$HOME/.icons/photogimp.png` 

            cp ~/Downloads/"PhotoGIMP by Diolinux v2020 for Flatpak"/.icons/photogimp.png  ~/.icons/photogimp.png


💎 Credits
---------------

* This project would not be possible without the amazing GIMP team.
* The Photo in the new Splash is from [Isabella Mariana](https://www.pexels.com/pt-br/@isabella-mariana-1022505)
* A BIG thanks to all Diolinux’s supporters on [Twitch](https://twitch.tv/Diolinux) and [YouTube](https://youtube.com/Diolinux).



📔 Patch Notes
---------------

- [Veja as Notas de Lançamento em Português](https://diolinux.com.br/2020/06/photogimp-2020.html)
