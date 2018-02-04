# con-ck-patches (unofficial)

**The -ck patchset (maybe now discontinued by author?) for linux merged into 4.15**

What?
=====

This is a manual merge (and some compat additions) I did in order to get the -ck patchset running on the Linux 4.15 kernel. 

These patches aimed at interactivity and used by the coolest of folks are originally by Con Kolivas. His development blog on the topic can be found at:

https://ck-hack.blogspot.com/

I am currently running with this patchset in addition to the default archlinux patches applied to 4.15 on Archlinux ( www.archlinux.org ) on a 64-bit SMP/SMT system under Virtualbox. Things are stable, the only traceback in my kernel log are various things like "Detected Tx Hang" on my network card, which likely is an arifact of running under Virtualbox and not this patchset.

All this said, I did not do extensive research nor speed a month porting this, this is simply a one-night job spent porting my favourite kernel patchset over to the latest kernel. I make no promises that you will have similar stability, but on a similar system I don't see why you wouldn't have similar results.

Enjoy!!

- Tim ( https://github.com/kata198/con-ck-patches )


I have noticed no hangs on anything, but this may indicate that there are changes between 4.14 and 4.15 which required additional code beyond what I provided and the port. I would still say it's completely safe and plan on continue running it myself, but if anyone has some free time may be worth looking into seeking out a "resolution." Again, I am also using virtualbox so this may just be some issue upon  resume from suspend, and seems benign.


Applying the Patch
==================

I've provided the PKGBUILD for 4.15-1-ck0 to replace the PKGBUILD in the arch repo, just override it if you want.

Or to manually apply changes:

The patch is provided as plaintext at a -p1 level from the root of the extracte d linux source.

With Makepkg
============

Fetch the base linux package ( maybe using archsrc-getpkg from https://github.com/kata198/pacman-utils or available in AUR https://aur.archlinux.org/packages/pacman-utils/  ??? :D \</plug\> ).

In the start directory (the one containing "PKGBUILD", edit the "prep" function and under the last "patch" line (line 68 in the 4.15-1) add:

	patch -Np1 "${startdir}/linux-4.15-ck0.patch"

I suggest also maybe adding an "exit" underneath or a "make xconfig" to then update your configuration. 

From Source
-----------

Download the source from www.kernel.org , extract the source, cd into that directory, and apply the patch with:

	cat linux-4.15-ck0.patch | patch -p1

before running configure.


License
-------

I make no additional claims over this patchset, all credit for the majority of the work goes to Con Kolivas, and you may consider my merge additions as GPLv2.

See the "COPYING" file within the linux source code for the specific text of the GPLv2.

