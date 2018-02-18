# con-ck-patches (unofficial)

**The -ck patchset for linux merged into 4.15**

NOTE: This is an unofficial release. The "Early Bird Special." Con Kolivas has stated that he will get to doing an official release within a week or so (so mid-February).


Update Feb 18 2018
==================

Con Kolivas has releasd the "official" version of the -ck patchset, 4.15-ck1 on Feb 18 2018 around 2AM EST.

I have provided a diff from my -ck0 merge to the official -ck1 merge, available as: https://raw.githubusercontent.com/kata198/con-ck-patches/master/linux-4.15-ck0.patch

This patch is provided just for curiousity sake, and in the slim event that one needs an incremental patch instead of a full patch (like maybe for a quicker build via *makepkg*

Reading through, it looks like the only differences are:

	1. Addition of options related to runqueue-sharing (was an experimental patch not included in 4.14-ck but now is considered stable enough.

	2. A possible fix to a condition that I noted could be seen on -ck0 after restoring from suspend/sleep ( I'm running this in Virtualbox, and when the parent OS goes to sleep and then wakes up, sometimes there are panics and high-cpu usage / load henceforth on system until reboot)

	3. Some minor cleanups


Of course I would recommend usng the official release -ck1 in lieu of my merge -ck0. This patch is provided if for some reason you need to patch your -ck0 to -ck1

Enjoy!!

- Tim


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

