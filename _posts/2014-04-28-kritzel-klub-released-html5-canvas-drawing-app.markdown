---
layout: post
title: Kritzel Klub released - HTML5 canvas drawing app
date: 2014-04-28 00:18:42.000000000 +02:00
---
I've just finished the basic version of a long-time project called ["Kritzel Klub"](http://www.kritzel-klub.de) (doodle club). This was a long running project that I care a lot about. The prospective audience are kids 7-12 years old, but I tend to enjoy it a lot too to be honest. Basically many people lose the ability to enjoy drawing when they start "real" school at this age. 

![kritzel-klub.de screenshot]({{ site.github.url | prepend:site.baseurl }}/images/Kritzelklub-2014-05-04-at-12-59-27-800px.jpg)

[Christoph Geiger](http://www.christophgeiger.de), the designer behind ["Kritzel Klub"](http://www.kritzel-klub.de), tried to find ways to let people just start doodling whithout fear of being judged. [Originally he did this with an installation](http://kritzel-klub.de/event/), where he put a big wallpapering table in an art gallery and let the visitors have a got at it with crayons. Amazingly this worked very well. Many "sophisiticated" visitors were delighted with the idea and hogged the table to make doodles and and occupied the different game stations with different drawing activities.

![wallpapering table](http://www.kritzel-klub.de/static/event/images/kritzel_klub-11.jpg)

After this initial success, Christoph thought about a digital equivalent that can be published online to reach an even larger audience. This is were I came in. We've been busy building a site around his original idea for several months and it's been online for a couple of days. The end result works well and Christoph's design stands in stark contrast to the usual clean-cut design of most sites or the candy sweet comic style of many sites for children. I'm also very happy we accomplished it with HTML5 instead of Flash, which is still used for many funded projects.

![color bar zoom]({{ site.github.url | prepend:site.baseurl }}/images/color_zoom.jpg)

One of the challenges was always to create this unique hand-drawn look with a drawable dynamic background and of course the site should work in almost all resolutions. Unfortunately the most obvious solution with a percentage based width and height would not work:

``` language-css
div#color_bar {
    height: 20%;
    width: 15%;
}
```

The problem are of course different aspect ratios. If the basic design is displayed on a 16:9 display, it will look very distorted on a 4:3 screen. So one obvious brute-force solution would be to calculate **everything** on every **resize**. The slightly unintuitive solution I came up was to use <code class="language-css">padding-bottom</code>. Here's code that respects aspect ratios using this idea:

``` language-css
div#color_bar {
    position: absolute;
    bottom: 0%;
    left: 0%;

    width: 15%;

    padding-bottom: 15%;

    background: url("/pictures/background.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
}
```

The behavior is actually [well defined in the standard](http://www.w3.org/TR/CSS2/box.html#padding-properties): padding-bottom does really only depend on the width of the element and not its height:

```
'padding-top', 'padding-right', 'padding-bottom', 'padding-left'
 Percentages:  	refer to width of containing block
```

As always there's an interesting discussion on this is defined in this way over on [stackoverflow](http://stackoverflow.com/questions/11003911/why-are-margin-padding-percentages-in-css-always-calculated-against-width). Although we can't know, because the spec doesn't specify the reason, Ryan Kinal mentions the interesting hypothesis that we would have [infinite loops of height calculation](http://stackoverflow.com/a/11004839/731302) otherwise.

Whatever the reason this little rule made working with div elements with background images so much easier when trying to build a responsive layout.

Now that the project is public, I'll continue writing about the different challenges we encountered with "Kritzel Klub".


