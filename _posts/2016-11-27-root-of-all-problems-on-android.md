---
layout: post
title: The root of all problems (on Android)
date: 2016-11-27 11:14
---

We always hear the PC-era is over and we're now completely in the mobile age. Despite this I've found that I don't really need my smartphone much.

Having a browser, a navigation app and access to some communication apps covers 99% of my use. For many mobile devices are replacements for computers, but I can't live without a machine with a proper keyboard and direct access to all my files.

# the problem

If you talk to friends, family and colleagues there's always a head technologist in the household who decides on the technology stack. There are even whole families using Windows phones! In our little family for better of worse its Android. Having inherited my old Samsung Galaxy S2 my girlfriend was quite happy for some time until it started rebooting frequently and using a lot of battery.

Because her usage pattern is even less demanding than mine, if found it hard to argue to buy a new device. The S2 is from 2011 and still runs the basic apps quite happily. I had installed the custom ROM Cyanogenmod 11, because Samsung was really slow in updating to recent OS versions. All in all this was the list of complaints

- several reboots per day
- very bad battery life (full charged phone was empty at 2pm)
- cannot install applications anymore because there's no space anymore (even though there was hardly any data on it)

# the instability problem

I started looking at the phone at 10am yesterday and I figured that at most I would have to reinstall the stock ROM and all the problems would go away. All motivated I started looking up what was installed and how the phone worked. Turns out I had installed Cyanogenmod in version 11 (which corresponds to Android 4.4). Samsung only made a customized Android [4.1.2](http://www.sammobile.com/firmwares/database/GT-I9100/) for this phone. The 4.x versions were published quite a few month in between not like 5, 6 and 7. Cyanogenmod also suggested upgrading to version 12.1 which corresponds to Android 5.1. As a loyal believer in software updates I took that suggestion hoping everything would just work better then.

# the google apps problem

Turns out it didn't. The update worked all right and after about an hour everything was up again. When I started the play store I found out that it wasn't so. There was a problem contacting the server; error code RH-01. So I googled and googled and what happened is, that the whole google application suite has to be updated and managed apart from the OS itself. There are some legal reasons why Cyanogenmod can't do this themselves.

After figuring that out and decrypting that I needed the new version of Google play services for arm (v7 32bit) version for Android 5.1 with 240dpi which corresponds to short code [234](http://www.apkmirror.com/apk/google-inc/google-play-services/google-play-services-10-0-84-release/), I figured out that you can in fact not install this apk directly when the OS is started. I couldn't update the Google play store on its own either. I had figured then I could update the rest of Google's apps from there.

Instead you have to install the google apps from the so-called recovery. This is a very basic interface which allows you to administer the partitions and also reinstall the OS and system apps like Google play services.

Ok, at this point we decided to back up all the photos and videos on the phone before doing anything substantial to the device. After waiting for that and figuring out how to boot in recovery. Previously I had found out that there's a package with the whole google apps available [here](http://opengapps.org/). When instructing the recovery to install this zip file it starts to work and after some minutes declares a failure.

After some more frantic googling enlightenment hit me, the reason I couldn't install the google apps and the frequent complaints for missing space were one and the same. The device has 16GB of memory but this space was partitioned very stupidly, thus not leaving enough space to install applications or use a recent version of the google apps. When the device was first sold in 2011 it was deemed leaving 500MB for the system partition and 2GB for the application partition would be enough.

To remedy this I tried to no avail delete some system applications so there would be enough room left for the google apps. This worked to some extent so I could boot and open the play store but it failed to work properly nevertheless. In between I had to figure out how to run a shell using adb on the device connected via usb, remounting the system partition read-write and delete the system apps (I ended up without a keyboard app, but I had to do sth. else anyway).

After chewing on this for some time I found a helpful [answer](http://android.stackexchange.com/a/144816) on stackoverflow that suggested to repartition the memory. With 1GB for the system drive and 6GB for applications and the rest for media there would be enough space. Following the instructions I got much working quite fast. Heimdall is a useful tool to change the partitions and also to install a custom recovery like ClockworkMod.

Having done that I then installed Cyanogenmod 12.1 from scratch and the Google apps. Actually I had to do this twice and boot Cyanogenmod first before going back to recovery and installing the Google apps. Now everything was nearly working and the system seemed indeed to work faster. I also had to reformat all partitions and be careful to format the SD-card as vfat and everything else as ext4.

# the writability problem

The last wrinkle which took me only 3-4 hours was that the both the internal 16GB SD-card and the extra physical 32GB SD-card that you can add to the device, were not writable. Apps like Camera complained that "no external storage was available".

After a lot of fiddling and factory resetting everything I tried to see what the OS complained about via the shell. Using `adb shell` I could find out via `mount` and the /fstab.xxx file what device was supposed to be mounted as external SD-card and mount it myself. Then I could also edit files on the phone itself.

Someone [mentioned](http://android.stackexchange.com/questions/38745/check-and-fix-sd-card-errors-within-android-itself) that using fsck might revive the card. And that did work. After asking a lot of questions fsck managed to repair the file system. After rebooting the external card worked and was available under /storage/sdcard1.

For the internal card the path was much harder and I could also mount it without problems as root on the shell but the user couldn't write to it even then. In the end the partition hadn't been formatted to Android's liking and reformatting it was the solution. Of course this was easier said then done because you had to use an [alternative shell](http://android.stackexchange.com/a/43479) to execute the format command but at this point I didn't even get mad ;-).

# the cherry on top

After all this work I couldn't help to use the convenient root of Cyanogenmod to install an ad blocker on the phone. [Adaway](https://adaway.org/) works by modifying the hosts file and redirecting ad URLs to localhost. You can even get it with update support and everything from the FOSS Android app store [F-Droid](https://f-droid.org/).

All in all it took me 9 hours to do all this, but as with coding you often don't foresee that everything takes longer and then in between there was no good time to stop because I had actually made the phone unusable. At the prospective user was very happy in the end and relieved she wouldn't have to buy a new phone in the next days to function as a human being :-).