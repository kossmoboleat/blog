---
layout: post
title: How to backup your IMAP mail account
date: 2009-11-01 22:03:56.000000000 +01:00
---
Since about a year IMAP has become widely available with free email providers. See <a href="http://mail-eu.gmx.com">GMX</a> and <a href="http://www.gmail.com">gmail</a>. That's why I decided to abandon my old payed email account at <a href="http://www.fusemail.com">fusemail</a>. Now to backup your emails there a couple of open-source projects that store your emails (archivemail, imapbackup.py and offlineIMAP). I finally settled for offlineIMAP because it has the most interface options and supports incremental backups. Incremental backups were very important to me because the other programs seemed to hang from time to time and had to restart the whole backup process all over again.

<em>This might be due to my flaky Wifi connection; YMMV.</em>

Offlineimap only backups in Maildir format. Unfortunately most GUI email clients like Mail.app or Thunderbird by default only support mbox format for importing mails. I found a small script that converts mails from Maildir to mbox format using the command formail from the projekt <a href="http://www.procmail.org/">procmail</a>.

Using this command the conversion is extremely easy. I've written a small script that should be executed from the parent directory of the backed up Maildir folder with maildir2mbox.sh &lt;foldername&gt;:
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 152px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">for i in $1/cur/*;</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 152px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;"><span style="white-space: pre;"> </span>do formail -I "Status: RO" &lt;"$i" &gt;&gt;$1-mbox;</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 152px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">done</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 152px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">for i in $1/new/*;</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 152px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;"><span style="white-space: pre;"> </span>do formail -I Status: &lt;"$i" &gt;&gt;$1-mbox;</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 152px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">done</div>
for i in $1/cur/*;
do formail -I "Status: RO" &lt;"$i" &gt;&gt;$1-mbox;
done
for i in $1/new/*;
do formail -I Status: &lt;"$i" &gt;&gt;$1-mbox;
done

The resulting &lt;folder-name&gt;.mbox files can be easily imported into either Thunderbird or Mail.app. Another possiblity for import to Thunderbird.app is the Add-on <a href="http://nic-nac-project.de/~kaosmos/mboximport-en.html">ImportExportTools</a>. Which recognizes the mails from Offlineimap if you add an .eml extension to their filenames.

There remains the problem that mails for special folders like drafts or templates are imported like normail emails in e.g. Mail.app. A simple solution to this problem is to drag them to the drafts folder in a local POP3 mailbox or on another remote IMAP mailbox.
