Welcome to the ``suckless-utils`` docs!
===================================

``suckless-utils`` is a collection of applications that aims to form a desktop environment that is modular, flexible and lightweight (for the RAM and storage).

- **Modular** - it aims for various functionality that can be turned off or on in the source code level, which could make for various personal versions of each component.
- **Flexible** - it aims to be flexible, with the ability to have various functionality, window management layouts and down-to-source code customization aiding for that, as well as the ease of hacking due to the ``-flexipatch`` forks by bakkeby implemented preprocessor directives.
- **Lightweight** - compared to other desktop environments, the suite clocks in at 700+ MB in RAM usage when idle (but actual mileage may vary), and it's small source code size (only clocking in at 18.2MB not including ``.git``) makes it the lightest desktop environment that you could compile yourself.

It features things such as EWMH support, IPC and ``fsignal``, ``pywal`` color scheming, **dynamic** window management (tiled, floating, tabbed and stacked window types), desktop icons (``nemo-desktop``), notfications (``dunst``), and more!

Check out the :doc:`usage` section for further information, including
how to :ref:`installation` the project.

.. note::

   This project is under heavy development.

Contents
--------

.. toctree::
   :maxdepth: 1
   :caption: Getting started
   start/install
   start/first
   start/components
   start/patches
   start/oobe
