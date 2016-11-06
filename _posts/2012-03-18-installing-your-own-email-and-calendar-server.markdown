---
layout: post
title: Installing your own email and calendar server
date: 2012-03-18 23:05:41.000000000 +01:00
---
Instead of giving all your data to other companies like Google or Apple, you can keep it to yourself and create your own email, address and calendar server from which you can control all your data and export it whichever way you want.

If you want an integrated solution for emails, addresses and calendar, you have two choices give up all your data to some big mega corp or setup a home server with Windows and install Exchange on it. Fortunately there are some less well-known open source alternatives to that. You can install them on an old computer that runs Linux and have a much cheaper solution than with Windows. In fact there are even solutions that work on a measly file server or NAS (Network Attached Storage). Such a device has very limited processing power and ram, but it may be enough for an open source group ware solution (that's what email+addresses+calendar actually is).

[wikipedia](http://en.wikipedia.org/wiki/Zarafa_(software))

Since a few days Zarafa is available for Synology NAS boxes with more than 256 MB RAM. Setting the machine up is relatively easy. There's a <a href="http://www.zarafa.com/wiki/index.php/Zarafa_Installation_Instructions_for_Synology_NAS#What_is_Zarafa.3F">guide on their community site</a>.

I just had a few problems that held me up along the way:

<ul>
<li>
If you try to execute postfix reload and it does not work. Check /var/log/messages. If you get this message:
Mar 18 00:02:24 postfix/postfix-script[11456]: starting the Postfix mail system
Mar 18 00:02:26 postfix/master[11466]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied

check the permissions of each directory level up to the file and make sure it's at least 755.
</li>
	<li>Here are <a href="http://www.synology-wiki.de/index.php/Fehlersuche_in_der_Mailstation">some things</a> (link in German) you can check if something goes wrong.</li>

	<li><a href="http://www.synology-wiki.de/index.php/Mail-Relay_mit_Postfix">Here's a guide</a> in German on how to setup different SMTP servers for different sender addresses</li>
 
	<li>If you wan to change the default behavior that deletes fetched mail from the server, check <a href="http://webcache.googleusercontent.com/search?q=cache:aas3Y_99BrAJ:forum.qnapclub.de/viewtopic.php%3Ff%3D364%26t%3D19806+zarafa+fetchmail+leave+mail+on+server&cd=1&hl=en&ct=clnk">this</a> (in German) out. It's a thread in a QNAP forum that describes how to change fetchmail's default behavior such that it only copies mail from a mailbox and does not delete it. You have to modify the tip a bit to match Synology's paths. Use /var/lib/postfix/atc/fetchmailrc and /usr/local/zarafa/bin/fetchmail instead of the QNAP paths mentioned in the thread.
</li>
</ul>

Unfortunately I realized that my machine is a bit too light for this workload. It does not have 256 MB of ram and Zarafa is not very usable, because it's much too slow.


<a href="http://community.zarafa.com/">Zarafa community website</a>
