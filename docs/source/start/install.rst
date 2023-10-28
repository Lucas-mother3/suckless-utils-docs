Installing ``suckless-utils``
=============================

.. tip::
  All of the steps should be reproducible within any modern Linux distros with internet access, but with minor tweaking.

.. note::
  Some components might be also be available on your distro's repository (for example the Arch User Repository). 
  Refer to your distro's package management for more info.

Dependencies
------------
Before installing all components, we need the dependencies:

- ``git``
- ``xorg`` (including drivers of course)
- ``base-devel`` (or ``build-essential``/``s``)
- ``libX11`` (``-devel`` or ``-dev``)
- ``libXft`` (``-devel`` or ``-dev``)
- ``libXcb`` (``-devel`` or ``-dev``)
- ``libXrender`` (``-devel`` or ``-dev``)
- ``libXinerama`` (``-devel`` or ``-dev``) 
- ``freetype`` (``-devel`` or ``-dev``)
- ``fontconfig`` (``-devel`` or ``-dev``)
- Nerd Fonts (Hack as default, can be changed manually)
- ``imlib2`` (``-devel`` or ``-dev``)
- ``picom`` (for transparency)
- ``feh`` (optional, if one decided not to use ``pywal``)
- ``pywal`` (for colors/wallpaper)
- ``slop`` (for the ``riodraw`` patch in ``dwm``)
- ``yajl`` (for handling IPC in ``dwm`` with ``dwm-ipc`` enabled)
- ``eww`` (optional, but recommended)
- ``jgmenu`` (for handling context menus, recommended but ``xmenu`` could be used as an alternative.)
- ``libexif`` (``-devel`` or ``-dev``) (for ``nsxiv``)
- ``jq`` (for handling eww notifications, as well for the ``adelle-theme`` script.)
- ``pamixer`` (for the media related scripts.)
- ``nemo`` (for handling desktop icons, though other file managers with similar functionality could be used.)

In addition, if you use the Termux application for Android, you must **also** install these:

- ``termux-X11`` repo (via main Termux app)
- ``proot``/``chroot``
- PulseAudio (if you like audio support)
- Display client of choice:
  
  - TigerVNC  
  - VNC client
  
  or
  
  - a XSDL client
  
  or

  - Termux:X11 (both the ``apk`` and the companion ``deb`` package.)

For installing ``spmenu``:

.. tip::
  You probably don't need the Wayland libraries as well, you could build ``spmenu`` with only X11
  by running ``meson setup build -Dwayland-=false``.

- ``wayland-client`` (``-devel`` or ``-dev``, for Wayland support)
- ``wayland-scanner`` (``-devel`` or ``-dev``, for Wayland support)
- ``wayland-protocols`` (``-devel`` or ``-dev``, for Wayland support)
- ``xbcommon`` (``-devel`` or ``-dev``, for Wayland support)
- ``pango`` (``-devel`` or ``-dev``)
- ``cairo`` (``-devel`` or ``-dev``)
- ``libconfig`` (``-devel`` or ``-dev``)
- OpenSSL or ``libssl`` (``-devel`` or ``-dev``)
- ``meson``

To make the tabbed windows functionality to work:

.. note::
  This uses ``tabbed`` instead of it being integrated in ``dwm`` itself
  due to modularity reasons, as well as ease of implementation.

- ``cut``
- ``xargs``
- ``grep``
- ``pstree``
- ``sed``
- ``wmctrl``
- ``xdotool``
- ``xprop``
- ``xwininfo``

.. note::
  Refer to ``patches.def.h`` and ``config.mk`` for additional dependencies, as well as tweaks for other Unix-based operating systems such as OpenBSD.


Setting up build environment and compilation
--------------------------------------------
1. Install the dependencies defined above.
2. Clone the repository (``git clone --recurse-submodules``)
3. Change directory to the ``suckless-utils`` directory.
4. Before compilation, remove ``config.h`` and ``patches.h`` (if exists) to ensure loading of defaults.
5. Start building ``dwm`` first by using ``make clean`` then ``make`` then ``sudo make install`` (For ``nsxiv``, it's ``make install-all``.)
6. After that, build anything except ``spmenu`` and ``slim``.

.. note::
  It is important to build anything except ``spmenu`` and ``slim``
  first as it uses a different build system than most of the components.

7. Setup ``spmenu`` by running ``meson setup build``. Pass ``-Dwayland-=false`` for disabling Wayland support.
8. Run ``ninja -C build`` for building spmenu binaries.
9. Install ``spmenu`` by running ``meson install -C build``. It would prompt for root access if necessary.

.. tip::
  Installing ``slim`` is optional as well, if one already have SDDM or GDM installed.

10. Make a build folder inside the ``slim`` directory.
11. Generate the ``Makefile`` via ``cmake``. Make sure the ``PREFIX`` variable is set on the ``/usr`` directory.
12. Then run ``make`` and ``sudo make install`` as usual. 
13. Set up the systemd service as well. If not, tweaking is necessary.
14. And it's built!

Installing scripts
------------------
The suite also utilize a lot of scripts as well. For example, ``layoutmenu`` handles setting layouts easily in ``dwm``.

Installing most scripts are just as easy as copying and pasting it to ``$PATH`` and ``chmod``ing if neccessary. 

.. note::
  It is recommended to have ``$HOME/.local/bin`` in the ``$PATH`` variable to avoid conflicts.

Installing some scripts however might need some effort to install. For example, ``adelle-theme`` needs ``wget``, ``tabb`` needs the same dependencies as enabling tabbed window functionality, and the ``quoter`` script needs ``messages.txt`` to be placed on $HOME.

Some are reliant to ``jgmenu``, notably ``shutdown`` and ``layoutmenu``.

In ``spmenu`` some actually needs to be compiled manually. Here's the dependencies for some:

``clipmenu-spmenu`` dependencies:
- ``xsel`` 
- ``clipnotify``

``screenshot-spmenu`` dependencies:
- ``curl``
- ``xclip`` (X11)
- ``maim`` (X11)
- ``wayshot`` (Wayland)
- ``wl-clipboard`` (Wayland)
- ``slurp`` (Wayland)

``wallpaper-spmenu`` dependencies:
- ``xwallpaper``

Scripts are also necessary to make ``dwmblocks-async`` working, as well as the complete ``eww`` functionality. 

Congratulations! You just installed the suite! But hold your horses, we need some more set up, especially with the configuration files.
