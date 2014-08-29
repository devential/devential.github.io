---
layout: post
title: Creating a Mac bootable Linux USB stick with OS X
tags: linux
---  

> In the spirit of proper documentation, I’ve decided to document the entire process of installing Arch Linux in a dual boot setup with OS X on my MacBook Pro. Macs are notably finicky when installing _foreign_ operating systems such as many Linux distributions that aren’t Ubuntu, thus, keeping a proper log on what worked for me would be useful if ever I revisit this situation in the future. The install procedures I use here have been consolidated from many online sources which I’ve picked out through trial-and-error. Links to these references are noted in the appropriate parts. This also should serve as a good consolidated reference for anyone who decides to undertake a similar exercise. The installation proper was done on the 30th of August, 2014, with preparation of the installation media done days prior. The latest install image (`archlinux-2014.08.01-dual`) at this time was used; the currently available installation media will have changed at this point. 

On OS X, creating a bootable Linux USB stick should be as simple as running the `dd` command in terminal, writing your downloaded image directly to your stick. While this in itself is already bootable on most ordinary PCs, A Mac will not be able to detect the stick on bootup, and thus will be unable to boot from it (This was tested using the ordinary boot switcher method of holding down the option key. I have not personally attempted this with a custom boot loader such as _rEFInd_.) 

After a relatively short search, I stumbled upon a recent post that details the [creation of a Ubuntu Live USB bootable on Macs](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253). While this tutorial uses Ubuntu, it should very well apply for any Linux distribution, such as Arch Linux, which I used in mine. Other references I used were the [Arch Wiki](https://wiki.archlinux.org/index.php/USB_Flash_Installation_Media#In_Mac_OS_X) as well as [Cody Littlewood’s dual boot post](http://codylittlewood.com/arch-linux-on-macbook-pro-installation/). Below I detail the exact steps I took which allowed me to successfully create a bootable USB stick. This procedure was both done on and tested with my MacBook Pro 9,2, OS X version 10.9.4.

The first part was to add a GUID partition table to the USB stick. In the Partition pane of your USB stick in Disk Utility, select ‘1 Partition’ from the dropdown and select the format as ‘Mac OS Extended (Journaled)’. Before Applying, go into options and select ‘GUID Partition Table’ as the partition scheme. Apply the changes.

The next step will be to convert the disk image (which will most likely come as a `.iso` file) into a `.img` file. On Terminal,

	hdiutil convert -format UDRW -o ~/target/path.img ~/source/path.iso

where `~/target/path.img` is the path to where and what the `.img` file will be saved as, and `~/source/path.iso` is the path to your disk image. on OS X, you can simply drag and drop the disk image file onto the terminal window to input the file’s path to avoid any errors in text entry. OS X will append the `.dmg` file extension to the end of the target file; changing this file extension is not necessary.

Once this is finished, enter 

	diskutil list 

to identify your USB stick. note the device’s properties such as name and size to correctly identify it; you can remove your USB stick, run the command again and note which disk is no longer visible to make sure that you have correctly identified the drive. 

Once you’re sure of your device information, take note of the device node; it should be in the format `/dev/diskN`, where `N` is a number assigned to your USB drive. Unmount the drive with the command

	diskutil unmountDisk /dev/diskN

then run `dd` to write the disk image file (the converted `.img.dmg` file in the previous step). Double check that file paths and the destination disk are correct; drag and drop the file onto the terminal window to be sure. Writing to the wrong disk (such as your hard drive) could very easily result in file corruption and data loss.

	sudo dd if=~/target/path.img of=/dev/rdiskN bs=1m

The `if` path corresponds to the input file, in this case, your install disk image. `of` refers to the destination disk, where `N` should be the device number of your USB stick. Note that we are using `/dev/rdiskN` instead of `/dev/diskN` as we saw in `diskutil` list. The `bs` parameter refers to the block size which defaults to ___. here it’s set to `1m` (1 megabyte) so it copies quicker. You may change this or leave it out as desired.

The `dd` command should take a few minutes to run and finish; do not attempt to close your terminal window while this is still running. Once it finishes, a dialog should appear saying ‘The disk you inserted was not readable by this computer.’ click ignore to dismiss this message, and eject your USB stick with the command

	diskutil eject /dev/diskN

and physically remove the stick after. This should now be bootable on a Mac. On reboot with the USB stick reinserted, hold down the option key before the startup chime and a boot selection menu appears, select the yellow USB icon to boot from it, and proceed with your installation.
