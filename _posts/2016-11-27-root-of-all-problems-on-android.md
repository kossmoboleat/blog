---
layout: post
title: The root of all problems (on Android)
date: 2016-11-27 11:14
---

We always hear the PC-era is over and we’re now completely in the mobile age. Despite this I’ve found that I don’t need my smartphone that much.

Having a browser, a navigation app and access to some communication apps covers 99% of my use. For a majority of users mobile devices are replacements for computers. Contrary to that I can’t live without a machine with a proper keyboard and direct access to all my files.

# the problem

If you talk to friends, family and colleagues their households are usually "branded". There’s a head technologist in the household who decides on the technology stack. There are even whole families using Windows phones! In our little family for better or worse it's Android. Having passed my old Samsung Galaxy S2 on to my girlfriend, she was quite happy for 2 years. Until it started rebooting several times a day. The battery was also depleted come 2pm.

Because her usage pattern is even less demanding than mine, I've found it hard to argue to buy a new device. The S2 is from 2011 and still performs well with the basic apps. I had installed the custom ROM Cyanogenmod 11, because Samsung was took ages updating the OS. All in all this was the list of complaints:

- several reboots per day
- abysmal battery life. The completely charged phone was dead at 2pm.
- inability to install applications anymore because there’s no space anymore. Even though there was hardly any data on it.

# the instability problem


I started looking at the phone at 10am yesterday. I figured that in the worst case I would have to reinstall the stock ROM and all the problems would go away. All motivated I started looking up what was the installed OS and how the phone worked. Turns out I had installed Cyanogenmod in version 11 (which corresponds to Android 4.4). Samsung only made a customized Android [4.1.2](http://www.sammobile.com/firmwares/database/GT-I9100/) for this phone. Google published the  4.x versions in half-year intervals not like 5, 6 and 7. Cyanogenmod suggested an update to version 12.1 which corresponds to Android 5.1. As a loyal believer in software updates I took that suggestion.  Like a fool I hoped everything would work better then.

# the google apps problem

Imagine my surprise when it didn’t. The update worked all right and after about an hour everything was up again. When I started the play store I found out that it wasn’t so. There was a problem contacting the server; error code RH-01. So I googled and googled and it seems the whole google application suite has to be updated. Moreover it's also managed apart from the OS itself. There are some legal reasons why Cyanogenmod can’t do this themselves.

After figuring that out I decrypted a specific version of Google play services. The phone needed the arm (v7 32bit) version for Android 5.1 with 240dpi which corresponds to the code [234](http://www.apkmirror.com/apk/google-inc/google-play-services/google-play-services-10-0-84-release/). I figured out that you can in fact not install this apk directly in the running OS. I couldn’t update the Google play store on its own either. I had figured then I could update the rest of Google’s apps from there.

Instead you have to install the google apps from the so-called recovery. This is a basic tool to administer the partitions and also reinstall the OS and system apps.

At this point we decided to back up all the photos and videos on the phone. I waited for that and then figured out how to boot to recovery. Before I had found out that there’s a package with the whole google apps available[here](http://opengapps.org/). When instructing the recovery to install this zip file it started working on extracting it. Then after some minutes it declared a failure.

After some more frantic googling enlightenment hit me. I couldn’t install the google apps and I got the frequent no-space notifications for the same reason. The device has 16GB of memory but Samsung partitioned it without much foresight. They didn't leave enough space to install applications. Installing recent versions of google apps is not possible at all. In 2011  they deemed 500MB for the OS and 2GB for apps should be enough for everybody.

To remedy this I tried to no avail to delete some system applications. Then I would have had enough room left for the google apps. This worked to some extent so I could boot and open the play store but it failed to work completely even so. Before this I had to figure out how to run a shell using adb on the device connected via usb. And then remount the system partition read-write and delete the system apps. I ended up without a keyboard this way, but I had to do redo everything anyways.

After chewing on this for some time I found a helpful [answer](http://android.stackexchange.com/a/144816) on stackoverflow. It suggested to repartition the memory. With 1GB for the system drive and 6GB for applications and the rest for media there would be enough space. Following the instructions I got much working quite fast. Heimdall is a useful tool to partition and also to install a custom recoveries like ClockworkMod.

Having done that I then installed Cyanogenmod 12.1 from scratch and the Google apps. Actually I had to do this twice. The second time I booted Cyanogenmod first before going back to recovery and installing the Google apps. Now everything seemed to work and the system seemed indeed to work faster. I also had to reformat all partitions and be careful to format the SD-card as vfat and everything else as ext4.

# the writability problem

The last wrinkle took me *only* 3-4 hours. Both the internal 16GB SD-card and the extra physical 32GB SD-card were not writable. Apps like Camera complained that “no external storage was available”.

After an hour of fiddling and factory resetting everything I tried to see what the OS complained about via the shell. Using  `adb shell` I could find out via `mount` and the /fstab.xxx file what device was supposed to be mounted as external SD-card and mount it myself. Then I could also edit files on the phone itself.

Someone [mentioned](http://android.stackexchange.com/questions/38745/check-and-fix-sd-card-errors-within-android-itself) that using fsck might revive the card. And that did work. After asking a dozen questions fsck managed to repair the file system. After rebooting the external card worked and was available under /storage/sdcard1.

For the internal card the path was much harder and I could also mount it without problems as root on the shell but the user couldn't write to it even then. In the end the partition hadn't been formatted to Android's liking and reformatting it was the solution. Of course this was easier said then done because you had to use an [alternative shell](http://android.stackexchange.com/a/43479) to execute the format command but at this point I didn't even get mad ;-).

# the cherry on top

After all this work I couldn't help to use the convenient root of Cyanogenmod to install an ad blocker on the phone. [Adaway](https://adaway.org/) works by modifying the hosts file and redirecting ad URLs to localhost. You can even get it with update support and everything from the FOSS Android app store [F-Droid](https://f-droid.org/).

All in all it took me 9 hours to do all this. As with coding you usually don’t foresee that everything takes longer. Before the end there was no good time to stop because I had actually made the phone unusable. Finally the prospective user was happy. She was relieved she wouldn’t have to buy a new phone in the next days :-).