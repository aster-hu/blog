---
title: "I Found an iMac in the Garbage Room"
tags: [life]
---

## A Mac in Garbage Suite?

It sounds super weird, but I found a 27' iMac when I went to throw out garbage.
The screen looked unscratched, so I told my partner we should grab it. I am confident of my ability to fix electronics and it could be a worthy investment if succeed.

## Troubleshooting the Disk Issue

I was able to boot the iMac. This was a good start.

However the screen stopped at the Apple logo. Usually it can be repaired through Apple's default tool **Disk Utility**.

A New issue happened when I tried to erase/repair the disk in Disk Utility during Recovery Mode. No matter what option I chose, it just showed an error message:

> Erase failed.
>
> Couldn't unmount disk (69888).

I realized it's likely because I was using the local recovery partition disk. It was similar to error message that you get when trying to delete a file that is still opened.

I have been searching and trying some possible solutions but none of them gave me good result:

* I used an USB bootable installer for Mojave to boot, which is the same system of the current disk. No luck.

* I also went to Internet Recovery Mode by pressing <kbd>Cmd ⌘</kbd> <kbd>Option ⌥</kbd> <kbd>R</kbd>. Still doesn't work.

* I used [command line](https://www.amsys.co.uk/disk-utility-tip-fix-couldnt-unmount-disk-errors/) to force unmount disk within above two modes. With this method I can at least look deeper into the issue.

  Open Terminal in recovery mode, enter
  
```bash
  diskutil list
  ```

  It will show up all disks. I found the disk that needs to be unmounted, got the identifier and ran:
  
```bash
  diskutil unmountDisk /dev/disk0
  # disk0 is my disk's identifier
  ```

  Here is where things went wrong. I got the error:
  > Forced unmount of disk0 failed: at least one volume could not be unmounted

* After running the command line, I tried to unmount each one of the disks in the above list (there's 23 disks in total) and see if I could unmount disk0 after that. Nope.

* I tried to put another command line `mount` to help identify what disks were actually mounted but I couldn't find where went wrong. It doesn't look like disk0 has been using, as the system is booting from external drive.

## Solutions

OK. At this point, I'm quite desperate. Then I found [this post](https://discussions.apple.com/thread/250763252?page=2) where OP mentioned their problem has been resolved by using a High Sierra USB installer (I'm using Mojave). Alright, I decided to try it as a last resort.

And then.... Eureka!

It didn't even need to use command line. I just simply went to Disk Utility and click Erase. It's that easy.

I'm still not sure why. It must be something related to Mojave itself. Anyway, I'm happy to see my free iMac is finally working after a whole night's effort.
