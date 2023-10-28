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

.. note::
  You probably don't need the Wayland libraries as well, you could build ``spmenu`` with only X11
  by running ``meson setup build -Dwayland=false``.

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

