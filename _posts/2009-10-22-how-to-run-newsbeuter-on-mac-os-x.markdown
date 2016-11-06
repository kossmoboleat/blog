---
layout: post
title: How to run newsbeuter on Mac OS X
date: 2009-10-22 23:00:57.000000000 +02:00
---
This is howto shows how you can install <a title="newsbeuter homepage" href="http://www.newsbeuter.org">newsbeuter</a> 2.1 on Mac OS X. First you have install some required libraries using <a title="MacPorts Project" href="http://www.macports.org/">MacPorts</a>, a packet-manager on the Mac. MacPorts is very similar to FreeBSD's ports system.
<ol>
	<li>The curses-based widget set<strong> </strong><a title="STFL Project" href="http://www.clifford.at/stfl/">Structured Terminal Forms Language/Library (STFL)</a> delivers the graphical frontend for newsbeuter.
<pre><strong>sudo port install stfl</strong></pre>
</li>
	<li>The <a href="http://tiswww.case.edu/php/chet/readline/rltop.html">GNU readline</a> library gives users basic line-editing features as known from simple editors like emacs or vi.
<pre><strong>sudo port install readline</strong></pre>
</li>
	<li>Other dependencies are the embedded database <a href="http://www.sqlite.org/">SQLite</a> for storing the blog entries, <a href="http://curl.haxx.se/">libcurl</a> for transferring files from the Web and <a href="http://pkg-config.freedesktop.org/">pkg-config</a> for managing installed libraries and compile options.
<pre><strong>sudo port install sqlite3 libcurl pkgconfig</strong></pre>
</li>
	<li>The latest available mac-compatible newsbeuter version can be found <a href="http://github.com/jperras/newsbeuter/tree/os-x-compatible">here</a> (click on download). It's dated July 22nd. This <a href="http://groups.google.com/group/newsbeuter/browse_thread/thread/4d6a7d1aa449433b">thread</a> explains that jperras had to do some minimal modifications to newsbeuter itself to make it compile on osx. If you prefer, you can make the same change to the 2.0 release or current HEAD to get a compiling version for Mac. The necessary change is to the file: src/utils.cpp:</li>
</ol>
<pre style="font-size: 12px; overflow-x: hidden; overflow-y: hidden; padding-left: 0.7em;">- in line 264:

//#ifndef __linux
//	const char * inbufp;
//#else
	char * inbufp;
// #endif
Fixed the problem.</pre>
<pre style="font-size: 12px; overflow-x: hidden; overflow-y: hidden; padding-left: 0.7em;">5. <span style="font-family: Georgia, 'Times New Roman', 'Bitstream Charter', Times, serif; line-height: 19px; white-space: normal; font-size: 13px;">Have fun!</span></pre>
