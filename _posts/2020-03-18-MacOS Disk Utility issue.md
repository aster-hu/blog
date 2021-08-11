---
title: "MacOS Disk Troubleshoot: Couldn't Unmount Disk Issue (69888)"
tags: macos hardware
---

## The Unmount Issue

This post doesn't have anything to do with programming, per se, but I still want to share it in case anybody run into similar issue.

The issue happened when I tried to erase/repair the disk in Disk Utility during Recovery Mode. No matter what option chose, it just shew an error message

>Erase failed.
>
>Couldn't unmount disk.

## Solutions I've Tried
I realized it's likely because I was using the local recovery partition disk, so I have been searching and trying some possible solutions:

- Used an USB bootable installer for Mojave to boot, which is the same system of the current disk. Same issue.

- Went to Internet Recovery by pressing <kbd>Cmd ⌘</kbd> <kbd>Option ⌥</kbd> <kbd>R</kbd>. Still doesn't work.

- Used [command line](https://www.amsys.co.uk/disk-utility-tip-fix-couldnt-unmount-disk-errors/) to force unmount disk within above two modes.

  Open terminal in recovery mode, enter
  ```bash
  diskutil list
  ```
  It gonna show up all disks. Find the disk needs to be unmounted, get the identifier and run
  ```bash
  diskutil unmountDisk /dev/disk0
  # disk0 is my disk's identifier
  ```

  Here is where things went wrong (again). I got the error:
  > Forced unmount of disk0 failed: at least one volume could not be unmounted

- After the command line, I tried to unmount each one of the disks in the above list (there's 23 disks in total) and see if I can unmount disk0 after that. Nope. No luck.

- Tried to put another command line `mount` to help identify what disks were actually mounted. Didn't find the issue. It doesn't look like disk0 has been using, as the system is booting from external drive.

## Now What?

OK. At this point, I'm quite desperate. Then I found [this post](https://discussions.apple.com/thread/250763252?page=2) where OP mentioned their problem has been resolved by using a High Sierra USB installer. Alright, I will try as a last resort.

And then....Eureka!

It doesn't even need to use command line. I just simply went to Disk Utility and click Erase. It's that easy.

I'm still not sure why. It must be something related to Mojave itself. Anyways, I'm happy to see it resolved eventually after a whole night's effort.
