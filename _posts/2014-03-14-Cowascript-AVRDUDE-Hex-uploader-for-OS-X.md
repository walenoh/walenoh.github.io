---
layout: post
title: "Cowascript: AVRDUDE Hex uploader for OS X"
description: "Cowascript: AVRDUDE Hex uploader for OS X"
category: articles
tags: [OS X, Arduino, AVRdude, bash]
comments: false
---
<p>
Last week, I found myself needing to flash [Grbl](http://bengler.no/grbl) to an Arduino. AVRDUDE is bundled with the Arduino IDE, but using it in Terminal yeilds some lenghtly commands. It would be easy to write a bash script to automate this process. As always, I search the Internet for a script that may meet my needs. Why reivent the wheel?
</p>
<br>
I stumbled accrossed this post on the [Arduino fourms](http://forum.arduino.cc/index.php/topic,100978.0.html).



## Running Cowascript

First thing, lets make it executable before we run. 
<br /><br>


```chmod +x Cowascript```
<br /><br>


```./Cowascript```
<br /><br>

![image](http://www.walenoh.com/images/Cowasaki-Run.png)


<br /><br>

From the Author 
<br />
""The script starts by asking the user what they want to do: program/erase/read or verify a chip or multi-write a batch of chips.

The script then reads all the serial ports on the computer, it decides which of these are relevant and if there is just one it automatically selects it, if there are more than one it gives the user the ability to select the right one and if none it aborts.

The user can also select the chip type (but by setting a labeled variable in the script this question can be automated too).

The user will also be shown all the HEX files within the "hex" folder."


#### Arduino & OS X 10.9+

Note that with Mac OSX 10.9 "Mavericks", Apple provides their own driver for FTDI chipset. Many people have trouble with Apple's driver. Steve B has a quick fix over on his [Blog](http://stevenbreuls.com/2014/03/fix-ftdi-dmx-interface-arduino-on-osx-10-9-mavericks/).



