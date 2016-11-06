---
layout: post
title: Getting external static files to work with Django on Google App Engine
date: 2012-04-08 17:53:11.000000000 +02:00
---
It's surprisingly hard to reference simple static files such as css stylesheets or images. When you upload your project to GAE the usual simple file links stop working. Even referencing a file in the same directory doesn't work. That stumped me a bit. Why shouldn't it work? I can only imagine that there are security reasons for this. After all you don't want anybody to be able to access your actual python scripts either. So how does Google solve this? They implemented a technology on top of the web app framework that redirects access on specific paths. This is the same mechanism that's used for Django's urls.py.

Now my apps.yaml looks like this:
<pre lang="yaml">
- url: /media
  static_dir: static/media  
</pre>

Any path that starts with /media is translated to the path static/media in your project folder then. It's advised to distinguish between the actual path and the path used in your templates this way. I imagine the reason is again security, but isn't this security by obscurity and not even that much obscurity because it's rather obvious? I'll have to do some more research on this. One disadvantage of this approach is that a local django test server of course can't see the files because the app.yaml configuration is specific to GAE. I hope there's an easy fix for this and you can actually use both with the same set of files.

Now that my site uses some fancy external css file, that defines the default font, it looks like this:
<a href="{{ site.github.url | prepend:site.baseurl }}/images/lunch-organizer_version2_table.png" alt="" title="lunch-organizer_version2_table" width="640" height="422" class="alignnone size-full wp-image-508" /></a>

