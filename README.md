# compat-wireless-tvws
Highly experimental and obsolete modification of the ath5k Linux driver to implemented support for 5/10/20 MHz channels for TVWS (802.11af-like) operation. In addition, per-packet statistics and a few other modifications were added for research purposes.

This driver module was used to develop a TVWS transceiver using a frequency translator for my Ph.D. thesis. The code is not pretty nor optimized, but it does work. Before I made these hacks, 5/10 MHz channel bandwidths were not available with the ath5k driver. Today, this is both an obsolete driver and probably an obsolete hack.

Contacts
- Ryan E. Guerra (ryan@guerra.rocks)

Contributers
- Ryan E. Guerra (war@rice.edu)
- Stanislav Miskovich (smm1@rice.edu)
- George Chen (mgeorgechen@gmail.com)
- Reed Jones (a.reedjones@gmail.com)

## Requirements
The only tested and known-working version of Ubuntu for this mod:

root@mynode:~# cat /etc/debian_version; uname -a 
6.0.2
Linux mynode 2.6.32-5-686 #1 SMP i686 GNU/Linux

Note that this has some very specific compatibility requirements due to some symbol definitions being moved from the compat-wireless package to the Linux kernel headers. If you compile it with any updated version of the Linux header files, you will probably run into a number of compilation errors; most of these errors can be fixed by addressing the compilation problems one-by-one on your machine by getting the conflicting definition locations, and commenting out the duplicate located in this compat-wireless branch.

## Build Instructions

1. To install, cd to the unzipped folder and type:

  * `./scripts/driver-select ath5k`
  * `make`
  * `make install`
  * `make unload`
  * `modprobe ath5k`
  
2. To test the installed version of this driver, type “modinfo ath5k” at the prompt. You should see one line that contains “RNG – v12.7″ and some description info.

## Support
Unfortunately, I can NOT offer support for this code.

## Revision Notes

2018-09-30 Initial import into GitHub, cleaned READMEs and documentation for public release. REG

2011-10-28 12.7 Fixed new compile-time errors that are due to updated Linux headers. REG

2011-07-06 12.2 The whitespace debugfs now prints out the MAC address of the attached card in order that we know which card is assigned which PHYX number. REG

2011-07-01 12.1 Fixed compile errors and warnings involving a redefinition of NETDEV. Reed
