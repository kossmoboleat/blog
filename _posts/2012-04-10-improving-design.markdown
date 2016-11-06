---
layout: post
title: Improving design
date: 2012-04-10 01:05:51.000000000 +02:00
---
I haven't used CSS in a while and it's amazing what effects you can achieve with some simple stylesheets. One thing I really like are the "intelligent" CSS selectors. Instead of dealing awkwardly with classes and polluting your Django views with design decisions, you can simply include some cool CSS.

Take for example the alternating row colors. In the olden times you used to define classes for each second row and use a different background color. Now you can just write:

<pre lang="javascript">
tr:nth-child(odd)    { background-color:#EEE; }
tr:nth-child(even)   { background-color:#FFF; }
</pre>

Pretty cool, he?
In my lunch organizer web app I also used this code to create borders between the different weeks and the header:
<pre lang="javascript">
tr:nth-child(1)   th { border-bottom:2px solid #AAAAAA; }
tr:nth-child(6)   td { border-bottom:2px solid #AAAAAA; }
</pre>

It's nice how easy it is to create fance drop-shadow effects, too:
<pre lang="javascript">
table {
    border-spacing: 0;
    border-color: #AAAAAA; 
    border-collapse:separate;
    border: solid #ccc 1px;
    -moz-border-radius: 6px;
    -webkit-border-radius: 6px;
    border-radius: 6px;
    -webkit-box-shadow: 0 1px 1px #ccc; 
    -moz-box-shadow: 0 1px 1px #ccc; 
    box-shadow: 0 1px 1px #ccc;      
}

th:first-child {
    -moz-border-radius: 6px 0 0 0;
    -webkit-border-radius: 6px 0 0 0;
    border-radius: 6px 0 0 0;
}

th:last-child {
    -moz-border-radius: 0 6px 0 0;
    -webkit-border-radius: 0 6px 0 0;
    border-radius: 0 6px 0 0;
}

th:only-child{
    -moz-border-radius: 6px 6px 0 0;
    -webkit-border-radius: 6px 6px 0 0;
    border-radius: 6px 6px 0 0;
}
</pre>

All in all it looks like this now:
<a href="{{ site.github.url | prepend:site.baseurl }}/images/lunch-organizer_version3_table.png" alt="" title="lunch-organizer_version3_table" width="530" height="393" class="alignnone size-full wp-image-528" /></a>
