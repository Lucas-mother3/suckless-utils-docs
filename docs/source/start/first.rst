First Setup
===========

Congrats! You just installed the suite! But you must need to do these before **actually** starting them. Luckily it's just for the first time you run this.
No need for further pain after these are done.

Initializing ``pywal``
------------------
First copy all of the things in ``config`` to ``$HOME`` and rename it to ``.config``.

To all of the colorschemes to work, hard link the generated colorscheme for everything in ``$HOME/.cache/wal/`` to each of the components:

- ``cava-config`` hard link to ``$HOME/.config/cava/config``
- ``colors.scss`` hard link to ``$HOME/.config/eww/colors.scss``
- ``dunstrc`` hard link to ``$HOME/.config/dunst/dunstrc``
- ``jgmenurc`` hard link to ``$HOME/.config/jgmenu/jgmenurc``
- ``vis`` hard link to ``$HOME/.config/vis/colors/pywal``

and you're basically done, except if you use SLiM.

SLiM is a bit different than the others, necessitating ``sudo``.  To actually reload, run the ``slim-reload`` in the same folder. This would prompt ``sudo`` as you're actually modifying the theme in ``/usr`` to replace the colors aand wallpaper.

and you're finally done with ``pywal``!

Configuring some scripts
------------------------

To configure the output for the ``quoter`` script, you need to edit the ``messages.txt`` file in the home directory.

Next, you need to modify **both** ``$HOME/.config/eww/eww.yuck`` and ``$PATH/sb-forecast`` if neccessary, to change location.

Lastly, you need to modify ``$HOME/.config/eww/eww.yuck`` and ``$HOME/.config/eww/eww.scss`` to adjust width settings and variables.

And that's it! Hope you enjoy the desktop!
