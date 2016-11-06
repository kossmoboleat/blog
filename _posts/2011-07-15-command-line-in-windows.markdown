---
layout: post
title: command-line in Windows
date: 2011-07-15 00:55:25.000000000 +02:00
---
I personally prefer the bash even in cygwin over the dos shell many times, but it's often the only shell available and has more features on windows. 

An example would be of course <strong>system administration stuff</strong>, like starting services -- the windows equivalent of UNIX daemons:
<code>  net start/stop *service-name*
</code>or killing processes by pid:
<code>  taskkill /pid 1234
</code>by name:
<code>  taskkill /IF "abc.exe"
</code>or by window title -- thanks to windows hard coupling of GUI and OS:
<code>  taskkill /IM * /FI "WindowTitle eq *window title wo quotes*"
</code>shutting down (See this <a href="http://www.online-tech-tips.com/computer-tips/remote-shutdown-command/">blog entry</a>):
<code>  shutdown -s
</code>In conjunction with killing processes by WindowTitle it's nice to know how to set the title of the command prompt:
<code>  title *title*
</code>
Some commands are especially useful if you have to <strong>automatically setup a system</strong>.
Change the hostname:
<code>  wmic computersystem where name="%COMPUTERNAME%" call rename name="NEW"
</code>reset windows vista/7 activation grace period to 30 days (can be done up to 3 times):
<code>  slmgr.vbs /rearm
</code>enter windows 7 product key
<code>  slmgr.vbs /ipk
</code>start windows 7 online activation
<code>  slmgr.vbs /ato
</code>
<strong>Generally useful stuff in the dos shell:
</strong>chaining commands:
<code>  echo 1 && echo b</code>
