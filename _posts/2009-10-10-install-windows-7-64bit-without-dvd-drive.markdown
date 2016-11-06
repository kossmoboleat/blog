---
layout: post
title: Install Windows 7 64bit without DVD drive
date: 2009-10-10 23:03:03.000000000 +02:00
---
In this how-to I describe how I installed Windows 7 64bit without a DVD drive on my mac. My SuperDrive stopped working nearly a year ago and I haven't really missed it that much to pay Apple's huge repair costs or order a replacement drive and install it myself. Anyways; installing without a DVD drive is possible.

There are a couple of <a href="http://insidethebrackets.blogspot.com/2009/04/install-windows-on-macbook-air-with-no.html">How-t</a>o floating around that use Windows on a USB stick as an installation medium, but I found a how-to that only uses a USB stick to be able to change the startup disk's MBR. In short you'll need these things:
<ol>
	<li>An ISO image of Windows 7</li>
	<li>A clone of your Mac partition or a bootable version of the Mac OS X installer on a USB drive</li>
	<li>A computer running Windows with a working DVD drive to get Boot camp drivers</li>
</ol>
Most of the details are specified in the excellent <a href="http://insidethebrackets.blogspot.com/2009/04/install-windows-on-macbook-air-with-no.html">how-to</a>, but you can just boot from the clone or the installer on the USB drive. To get a clone of your startup disk just use tools like <a href="http://www.bombich.com/">CCC</a> or <a href="http://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html">SuperDuper!</a> to backup to an external hard disk.

Just a caveat: Make sure your Boot camp partition is big enough. It is extremely hard to increase the size of the Bootcamp partition. It normally involves deleting the partition and using the Boot camp assistant again.

To get power management and your apple keyboard to work you will have to install the Boot camp drivers after installing Windows. The Snow Leopard DVD is a dual DVD for PC/mac. When opened on any Windows PC, the DVD contains a setup utility and any drivers for your mac's hardware. Some of the hardware are actually standard components like the graphics or sound card, but the mac-specific keyboard and power management can only beg used with these drivers.

To get the drivers on your mac, just copy the DVD's contents on another DVD drive and open it in your newly installed Windows 7. The setup.exe unfortunately fails on 64bit Windows versions, but you can simply execute:
<pre>msiexec /i BootCamp64.msi</pre>
in the directory "Boot CampDriversApple" and the installer will start without any complains. After that you can enjoy your new OS :-)!
