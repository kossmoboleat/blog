---
layout: post
title: Sony PRS-T1 Rooting
date: 2012-01-02 18:04:49.000000000 +01:00
---
I couldn't resist from unlocking, aka rooting, my ebook reader. Rooting means that you have full access to your device and you can install any software you want. Whereas iPhones have "jailbreak" you have "rooting" for Android devices, because it is actually running a flavor of Linux and the administrator user on a Linux box is called the root user.

For the Sony ebook reader the advantages are that you can install any application that is also available for Android smartphones and tablets. Some examples are:
<ul>
	<li>Reading apps for different ebook vendors: e.g. Kindle, Kobo, B&N</li>
	<li>Games: anything w/o much animation will work: e.g chess, go, sudoku, cross word puzzles and so on</li>
	<li>Synchronization and transfer apps for ebooks: e.g. Dropbox</li>
</ul>

Rooting the Sony is a very simple process that seems to require a Windows machine - sorry, mac-people. There's a different more manual way described <a href="http://www.mobileread.com/forums/showpost.php?p=1899369&postcount=242">here</a>. You download a .zip-file, extract it and run the included batch script that performs the rooting on your connected sony reader. You can get the .zip-file from <a href="http://projects.mobileread.com/reader/users/porkupan/PRST1/flash_packages/minimal-root.zip">here</a> (linked from the excellent <a href="http://wiki.mobileread.com/wiki/PRST1_Rooting_and_Tweaks">mobileread wiki page</a>). Chalid from cme.at has written up a nice <a href="http://cme.at/reviews-tests-previews/howto/anleitung-sony-prs-t1-reader-wifi-root/">step-by-step guide</a> in German on how to perform this.

After you've done that installing other apps is a matter of copying them to the device and starting it's "Root Explorer" or the included Dropbox to open them. One very important step is to install "Link2SD" which allows you to install a lot more apps. The sony reader only has a couple of tens of MBs of free space for apps and "Link2SD" allows you to install apps on an MicroSD card, which means that you can install all the apps you want. There's <a href="http://cme.at/reviews-tests-previews/howto/anleitung-internen-speicher-des-sony-prs-t1-fur-app-installationen-erweitern/">another blog post</a> over at cme.at that describes the procedure very nicely. The main steps are creating two partitions on the MicroSD card: a 500 MB Fat partition and another primary ext3/4 partition for content on the card. Then you can just install the Link2SD.apk (See the blog article for the download) by copying it to the device or Dropbox. The first time you open Root Explorer, it might not show anything. When that happens check the notifications in the upper left corner, because it will try to obtain root privileges, but fail to display the appropriate dialog.

Now that you have the device rooted and enough space for all the apps you want, you're ready to install anything you want. Another useful step is to install the Google App Framework and then the Android Market, which gives you access to all Google apps and Google's application repository respectively. Again there's an <a href="http://cme.at/reviews-tests-previews/howto/anleitung-android-market-am-sony-prs-t1/">article</a> on cme.at for that, that describes the procedure and a link to a .zip-file that contains the framework and the market which have to be installed in exactly that order. When installed the market allows you to install apps directly on the reader without messing with Dropbox or the "Root-Explorer". 

Happy Hacking!
