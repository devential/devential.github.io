---
layout: post
title: An Arch Linux/OS X Dual-boot Set Up (Update, or, Damn You OSX Yosemite)
tags: linux
---

It's been two months since I last edited the post detailing my [Arch Linux dual-boot setup](/2014/08/31/Arch-Install), promising an update on what worked in my case, and ideally showing off my system in the process. Sadly, I wasn't able to update the post (or my installation for that matter) before I updated my OSX partition to try out Yosemite, unintentionally overwriting the GRUB bootloader, cutting off any and all access to my Arch partition.

I've deemed that restoring access to the partition was too much trouble for what it's worth. Additionally, after considering the possible damage I might do to my primary work computer from my tinkering (and I've bricked entire systems before), I've decided to no longer continue with the dual-boot setup. Instead, I'll try to find a spare PC that I can play with in the near future, with just Arch.

Nonetheless, my installation was still moderately successful: A working set-up was achieved by simply following the ArchWiki article for a [Mid-2012 MacBook Pro](https://wiki.archlinux.org/index.php/MacBookPro9,2_%28Mid-2012%29#Sample_partition_layout). I had also gotten far enough to begin customizing my window manager, [bspwm](https://wiki.archlinux.org/index.php/Bspwm), and had already pinned down most basic functionality, such as controlling the [Wi-Fi card with the b43 driver](https://wiki.archlinux.org/index.php/MacBookPro9,2_%28Mid-2012%29#b43), properly mapping all the media hotkeys, and managing my laptop's power usage using [Powerdown](https://wiki.archlinux.org/index.php/Powerdown). I don't consider all my efforts to be in vain, having learned a little more about setting-up and customizing Arch. It was still a bloody long exercise, but fulfilling enough to have kept me going for a while.