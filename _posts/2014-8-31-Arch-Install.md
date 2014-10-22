---
layout: post
title: An Arch Linux/OS X Dual-boot Set Up
tags: linux
---  


In the spirit of proper documentation, I’ve decided to document the entire process of installing Arch Linux in a dual boot setup with OS X on my MacBook Pro. Macs are notably finicky when installing _foreign_ operating systems such as many Linux distributions that aren’t Ubuntu, thus, keeping a proper log on what worked for me would be useful if ever I revisit this situation in the future. The install procedures I use here have been consolidated from many online sources which I’ve picked out through trial-and-error. Links to these references are noted in the appropriate parts. This also should serve as a good consolidated reference for anyone who decides to undertake a similar exercise. 

The installation proper was done on the 30th of August, 2014, with preparation of the installation media done days prior. The latest install image (`archlinux-2014.08.01-dual`) at this time was used; the currently available installation media will have changed at this point.

__Update:__ After two months of holding off finishing my setup, I made a pretty grave mistake by blindly updating my OSX partition. the recent OSX Yosemite update has overwritten the grub bootloader (which allowed me to access my Arch Linux install), while the stock Mac bootloader obvioulsy refuses to boot into any foreign partition. As such, I've decided not to continue with this set-up, instead opting to find and use a spare PC for an Arch-only install in the near future. [More details are in the update post.](/2014/10/22/Arch-Install-Update)