---
layout: post
title: "Installing OpenELEC for Raspberry on OS X"
description: "Quick guide to installing OpenELEC for Raspberry on OS X."
category: articles
tags: [Raspberry Pi, OpenELEC, OS X, dd]
---

"The Raspberry Pi is a computer that you can use for all sort of brilliant and useful things, from learning to program, to making robots, to Tweeting when birds visit a nesting box, to taking pictures from the stratosphere." [RaspberryPi.org](http://www.raspberrypi.org/)
<br>
<br>
My Raspberry serves as a Home Theater PC (HTPC). I've tired Rasplex, Raspbmc, and Xbian. All have worked great, but I find them all lacking one way or another. Now its time to start testing OpenELEC.

## Installing OpenELEC to SD on OS X

###First, lets find our SD card.

 
<br>
```diskutil list```
<br><br>
![image](http://www.walenoh.com/images/20131216_1.png)
<br><br>

###We can see my SD card is /dev/disk1
<br>
Lets use dd to write openELEC to our SD card. I downloaded a pre-built unofficial image from [http://openelec.thestateofme.com/](http://openelec.thestateofme.com). I put my download of OpenELEC in my Downloads folder.
<br>
<br>
**CAUTION:** dd is a powerful command. If you select the wrong disk you could destroy all the data on that disk.
<br><br>
[From the hdutil man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/hdiutil.1.html)
<br><br>
Since any /dev entry can be treated as a raw disk image, it is worth noting which devices can be accessed when and how.  /dev/rdisk nodes are character-special devices, but are "raw" in the BSD sense and force block-aligned I/O.  They are closer to the physical disk than the buffer cache.  /dev/disk nodes, on the other hand, are buffered block-special devices and are used primarily by the kernel's filesystem code.
<br><br>
We will have dd write to the raw disk /dev/rdisk1, this will be much faster than writing to /dev/disk1.
<br><br>
```sudo dd bs=1m if=~/Downloads/OpenELEC-RPi.arm-3.2.4.img of=/dev/rdisk1```
<br><br>
Control + T will show a status of process.
<br>
<br>
![image](http://www.walenoh.com/images/20131216_2.png)
<br>
<br>
dd may be unable to write to the disk if the resource is busy.
<br><br>
![image](http://www.walenoh.com/images/20131216_3.png)
<br><br>
To fix this, unmount the disk with diskutil.
<br>
```diskutil unmountdisk /dev/disk1```
<br><br>
![image](http://www.walenoh.com/images/20131216_4.png)
<br>
<br>
After the disk has been unmounted successfully. Run the dd command again.<br>
```sudo dd bs=1m if=~/Downloads/OpenELEC-RPi.arm-3.2.4.img of=/dev/rdisk1```
<br><br>
![image](http://www.walenoh.com/images/20131216_2.png)

###Now we have OpenELEC on our SD card.



