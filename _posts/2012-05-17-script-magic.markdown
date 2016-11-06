---
layout: post
title: Script Magic
date: 2012-05-17 00:51:00.000000000 +02:00
---
When working with lots of remote machines it's sometimes necessary to reboot them. Then it's always a pain to wait for them booting up. If the machines have extra interface cards, e.g. RAID, you have to sit there for a while until the machine becomes usable. So being a geek, I made a (Windows) script:

![geeks-vs-nongeeks-repetitive-tasks](/images/geeks-vs-nongeeks-repetitive-tasks.png)

This script requires cygwin on windows and you should install it's ping implementation -- the windows version doesn't return with an error if the host in unreachable. You also have to run it as an administrator on windows, because it needs these privileges to open a socket.

{% highlight bash %}
function waithost() { 
    if [ -n "$1" ]; then
      ping localhost 1 1 > /dev/null
      if [ $? -eq 0 ]; then
          while ! ping $1 1 1 &>/dev/null; do sleep 5;echo -n .; done
          messagebox.sh "Host $1 is reachable now!"
      else
          messagebox.sh "Error: Need admin privileges!"
      fi
  else
      messagebox.sh "Error: No host parameter given!"
  fi
}
{% endhighlight %}

Here's the script to show the messagebox:
{% highlight bash %}
#!/bin/bash
/cygdrive/c/Scripts/messagebox.bat "$1"
{% endhighlight %}

The popop.bat only contains this:
{% highlight batch %}
cscript C:\Scripts\MessageBox.vbs "%~1"
{% endhighlight %}

And here's the final tidbit, a visual basic script to show a messagebox.
{% highlight vbscript %}
Set objArgs = WScript.Arguments
messageText = objArgs(0)
MsgBox messageText
{% endhighlight %}

This comes in handy in other situations, too. For instance you can schedule an alarm with Windows' task scheduling:
{% highlight batch %}
schtasks /create /tn "Lunch Notification" /tr "messagebox.bat Lunch" /ST 12:00 /SC daily
{% endhighlight %}

This script will display a messabox with the text "Lunch" every day at noon. You can choose much more refined date schedules or intervals. Here's the <a href="http://msdn.microsoft.com/en-us/library/windows/desktop/bb736357(v=vs.85).aspx">documentation</a>.
