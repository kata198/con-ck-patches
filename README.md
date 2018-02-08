# con-ck-patches (unofficial)

**The -ck patchset for linux merged into 4.15**

NOTE: This is an unofficial release. The "Early Bird Special." Con Kolivas has stated that he will get to doing an official release within a week or so (so mid-February).

What?
=====

This is a manual merge (and some compat additions) I did in order to get the -ck patchset running on the Linux 4.15 kernel. 

These patches aimed at interactivity and used by the coolest of folks are originally by Con Kolivas. His development blog on the topic can be found at:

https://ck-hack.blogspot.com/

I am currently running with this patchset in addition to the default archlinux patches applied to 4.15 on Archlinux ( www.archlinux.org ) on a 64-bit SMP/SMT system under Virtualbox. Things have been running stable for several days, no hangs, hickups, or anything of the sort.

All this said, I have only tested this on a single machine with a single configuration. I do not anticipate that any alternate configurations, hardware or otherwise, will be anything less than 100% stable, but I also don't make a promise that it will be. You will just have to download and build to try it out for yourself :)

Enjoy!!

- Tim ( https://github.com/kata198/con-ck-patches )



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

