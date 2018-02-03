# con-ck-patches

**The -ck patchset (now discontinued?) for linux merged into 4.15**



This is a manual merge (and some compat additions) I did in order to get the -ck patchset running on the Linux 4.15 kernel. 

These patches aimed at interactivity and used by the coolest of folks are originally by Con Kolivas. His development blog on the topic can be found at:

https://ck-hack.blogspot.com/

I am currently running with this patchset in addition to the default archlinux patches applied to 4.15 on Archlinux ( www.archlinux.org ) on a 64-bit SMP/SMT system under Virtualbox. Things are stable, the only traceback in my kernel log are various things like "Detected Tx Hang" on my network card, which likely is an arifact of running under Virtualbox and not this patchset.

All this said, I did not do extensive research nor speed a month porting this, this is simply a one-night job spent porting my favourite kernel patchset over to the latest kernel. I make no promises that you will have similar stability, but on a similar system I don't see why you wouldn't have similar results.

Enjoy!!

- Tim ( https://github.com/kata198/con-ck-patches )

